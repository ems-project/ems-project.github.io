# Check list and tips and tricks in order to upgrade to version 4

## Checklist > 4.0

#### Deprecated twig functions
* replace `{% spaceless %}` by `{% apply spaceless %}`
* replace `{% endspaceless %}` by `{% endapply %}`
* replace `{% for key, item in array if test %}` by  `{% for key, item in array|filter(key, item => test) %}`
* replace `transchoice` by `trans`
  * I.e. replace `{{ 'search.results'|transchoice(results.hits.total.value|default(response.total))|raw -}}`
  * by `{{ 'search.results'|trans({'%count%': results.hits.total.value|default(response.total)}) -}}`

#### Asset custom twig functions
* replace `{{ emsch_assets(assets) }}` or `{%- do emsch_assets(assets) -%}` by `{%- set assetPath = emsch_assets_version(assets) -%}`
* replace `{{ assets('resource') }}?{{ assets_hash }}` by `{{ assets('resource', 'emsch') }}`

#### Email custom twig functions
```twig
{%- set email = emsco_generate_email(subjectMail) -%}
{%- set email = email.setTo(toMail) -%}
{%- set email = email.setBody(bodyMail, 'text/html') -%}
{%- set email = email.setFrom(fromMail) -%}
{{- emsco_send_email(email) -}}
```
→
```twig
{%- set email = emsco_generate_email(subjectMail) -%}
{%- set email = email.to(toMail) -%}
{%- set email = email.html(bodyMail) -%}
{%- set email = email.from(fromMail) -%}
{{- emsco_send_email(email) -}}
```

#### Misc
* replace `/\.hits\.total/` by `{% var.hits.total.value|default(var.hits.total) %}`
  * replace `/\[\'hits\'\][\'total\']/` by `var['hits']['total']['value']|default(var['hits']['total'])`
* remove the template environment
  * align template and preview for route, template and label
  * switch default environment `emsco:content:swith template preview`
* Do a force push to override the document
  * Keep in mind that all ouuids have changed, check in your content types for datalink to template documents
  * Rollback, in the routes.yaml, static templates have been replaced by their OUUID

## Checklist > 4.2

#### Content type roles in twig
Replace `is_granted(contentType.createRole)` → `is_granted(contentType.roles.create)`
* createRole → roles.create
* editRole → roles.edit

## Tips and tricks

### Backward compatibility route to old school assets path

New route to redirect to the new asset's url. Route:

```yaml
redirect_asset:
    config:
        path: 'bundles/emsch_assets/{slug}'
        requirements: { slug: '^.+$' }
        controller: 'emsch.controller.router::redirect'
    template_static: template/redirects/asset.json.twig
```

Template (template/redirects/asset.json.twig):

```twig
{% extends '@EMSCH/template/variables.twig' %}

{% block request -%}
{% apply spaceless %}
    {{ {
        url: asset(app.request.get('slug'), 'emsch'),
    }|json_encode|raw }}
{% endapply %}
{% endblock -%}
```