# Twig Components

Overview core twig components. 
Now we are using Symfony ux [twig components](https://symfony.com/bundles/ux-twig-component/current/index.html), 
in the feature we may use [live components](https://symfony.com/bundles/ux-live-component/current/index.html).  

The following components can be used in views/actions and dashboards.

<!-- TOC -->
* [Twig Components](#twig-components)
  * [Media library](#media-library)
<!-- TOC -->

## Media library

If you use this [media_library.json](/files/contenttype_media_library.json ':ignore') contentType, the only required attribute is `id`.

```twig
{{ component('media_library', {
    'id': 'examaple-media-lib'
}) }}
```

| Property          | Default                | Description                                                |
|-------------------|------------------------|------------------------------------------------------------|
| `id`              |                        | **required** html id attribute                             |
| `contentTypeName` | media_file             | **required** contentType name                              |
| `fieldPath`       | media_path             | **required** Field name for path value                     |
| `fieldPathOrder`  | media_path.alpha_order | Used for sorting folders and files.                        |
| `fieldFolder`     | media_folder           | **required** Field name for folder value                   |
| `fieldFile`       | media_file             | **required** Field name for asset                          |
| `defaultValue`    |                        | Key/value array for defining default, example organization |
| `searchQuery`     |                        | Example only load media files for an organization          |
| `template`        |                        | see [templating](#templating)                              |
| `context`         |                        | see [templating](#templating)                              |

### Templating

!> For overwriting the blocks, the emsch templates must be loaded with `EMSCH_ENVS`.
Using `emsch_add_environment` twig function, will not work. see [Upgrade 5.3.x](/upgrade.md#version-53x)

Be using an emsch template, you can overwrite the blocks for custom rendering.
Using the twig `self` variable, the blocks can be defined in the same template.

Available in blocks:
* [Config](https://github.com/ems-project/elasticms/blob/HEAD/EMS/core-bundle/src/Core/Component/MediaLibrary/MediaLibraryConfig.php)
* [MediaFile](https://github.com/ems-project/elasticms/blob/HEAD/EMS/core-bundle/src/Core/Component/MediaLibrary/MediaLibraryFile.php) only in `mediaLibraryFileRow`
* The context if defined in config

The following example contains all possible blocks, with their default rendering.

```twig
{{ block("body", "@EMSCH/template/dashboard/media_library.twig") }}
```

```twig
{% block body %}
    {{ component('media_library', { 
        'id': 'examaple-media-lib', 
        'template': _self,
        'context': {
            'example': 'example'
        } 
    }) }}
{% endblock body %}

{%- block mediaLibraryHeaderLeft -%}
    {% apply spaceless %}
        <div class="media-lib-container">
            {{ buttonHome|raw }}
        </div>
    {% endapply %}
{%- endblock mediaLibraryHeaderLeft -%}

{%- block mediaLibraryHeader -%}
    {% apply spaceless %}
        <div class="media-lib-container">
            {{ buttonAddFolder|raw }}
            {{ buttonUpload|raw }}
            {{ breadcrumb|raw }}
        </div>
    {% endapply %}
{%- endblock mediaLibraryHeader -%}

{%- block mediaLibraryFileRowHeader -%}
    {% apply spaceless %}
        <li>
            <div>Name</div>
            <div>Type</div>
            <div class="text-right">Size</div>
        </li>
    {% endapply %}
{%- endblock mediaLibraryFileRowHeader -%}

{%- block mediaLibraryFileRow -%}
    {% apply spaceless %}
        <li>
            <div><a href="{{ url }}" download="{{ media.file.filename }}">{{ media.file.filename }}</a></div>
            <div>{{ media.file.mimetype|trans({}, 'emsco-mimetypes') }}</div>
            <div class="text-right">{{ media.file.filesize|format_bytes }}</div>
        </li>
    {% endapply %}
{%- endblock mediaLibraryFileRow -%}

{%- block mediaLibraryFooter -%}
    <div class="media-lib-container"></div>
{%- endblock mediaLibraryFooter -%}
```

