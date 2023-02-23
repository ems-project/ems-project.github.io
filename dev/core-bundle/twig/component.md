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

Example `media_file` content type: [contenttype_media_library.json](/files/contenttype_media_library.json ':ignore')

```twig
{{ component('media_library', {
    'id': 'examaple-media-lib',
    'contentTypeName': 'media_file',
    'fieldPath': 'media_path',
    'fieldPathOrder': 'media_path.alpha_order',
    'fieldLocation': 'media_folder',
    'fieldFile': 'media_file'
}) }}
```

| Property          | Default                | Description                                                |
|-------------------|------------------------|------------------------------------------------------------|
| `id`              |                        | **required** html id attribute                             |
| `contentTypeName` |                        | **required** contentType name                              |
| `fieldPath`       | media_path             | **required** Field name for path value                     |
| `fieldPathOrder`  | media_path.alpha_order | **required** Field name for ordering paths                 |
| `fieldLocation`   | media_location         | **required** Field name for location                       |
| `fieldFile`       | media_file             | **required** Field name for asset                          |
| `defaultValue`    |                        | Key/value array for defining default, example organization |
| `searchQuery`     |                        | Example only load media files for an organization          |


