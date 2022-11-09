# Environment

An environment is used by a [ContentType](./elasticms/contentType/contentType.md), all revisions will be indexed into the alias.
The environment attach to a contentType is the `default` environment for this contentType.

From the default environment we can publish/unpublish to other environments.
Often an elasticms has 2 environments `preview` and `live`. 

<!-- TOC -->
* [Environment](#environment)
  * [Properties](#properties)
  * [Template publication](#template-publication)
<!-- TOC -->

## Properties 

| Property            | Description                                                      |
|---------------------|------------------------------------------------------------------|
| name                | Internal name                                                    |
| label               | Display label                                                    |
| color               | Display color                                                    |
| alias               | Elasticsearch alias (EMSCO_INSTANCE_ID + name)                   |
| circles             |                                                                  |
| inDefaultSearch     |                                                                  |
| managed             |                                                                  |
| snapshot            |                                                                  |
| updateReferrers     |                                                                  |
| templatePublication | Twig template, see [Template publication](#template-publication) |
| baseUrl             | Text field for defining an baseUrl                               |

## Template publication

You can block publication to an environment by defining a publication template.
- If the template adds a warning or error, the publication is block. 
- If the template add an info message, the publication is not block.

```twig
{% set markdownMessage %}
**Validation failed**
* Document {{ revision.label }} is not validated (checkbox)
{% endset %}

{% if revision.contentType == 'page' and false == document.source.validated|default(false) %} 
    {% do publication.addWarning(markdownMessage) %}
{% endif %}
```

> **Template context**
>
> * `publication` : publication object (methods addWarning, addError, addInfo)
> * `environment` : current environment
> * `revision` : revision to be published
> * `document` : elasticsearch document of the revision (default environment) 