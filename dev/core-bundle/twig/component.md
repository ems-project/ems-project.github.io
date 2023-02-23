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


