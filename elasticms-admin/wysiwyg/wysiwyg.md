# WYSIWYG

In elasticms you can configure WYSIWYG [profiles](#profiles) and [style sets](#style-sets).
These are used for configurating and styling the [CKEditors](https://ckeditor.com/).

<!-- TOC -->
* [WYSIWYG](#wysiwyg)
    * [Profiles](#profiles)
        * [EMS settings](#ems-settings)
    * [Style sets](#style-sets)
        * [Styles set preview](#styles-set-preview)
<!-- TOC -->

## Profiles

Profiles are attached to an elasticms [user](../user/user.md). The configuration is applied on all WYSIWYG fields.

A profile has a required `name` and `config` json field.

For building the json, the ckeditor [Toolbar Configurator](https://ckeditor.com/latest/samples/toolbarconfigurator/index.html#basic) can be helpful.

[Example full profile config json](../wysiwyg/example_profile.md).

### EMS settings

EMS settings are used over customizing the CKEditor experience.

| Property           | Description                                           |
|--------------------|-------------------------------------------------------|
| urlTypes           | Limit the url types when creating a url               |
| urlAllContentTypes | Disable the option `All ContentTypes` on internal url |

```json
{
  "ems": {
    "urlTypes": ["url", "anchor", "localPage", "fileLink", "email"],
    "urlAllContentTypes": true
  }
}
```

## Style sets

Style sets are attached to a WYSIWYG field.
Can be used to overwrite CKEditor settings and user profiles.

| Property                      | Info                                    |
|-------------------------------|-----------------------------------------|
| Name                          | required style set name                 |
| Format tags                   | overwrite CKEditor format tags          |
| Default table class attribute | overwrite default class in table dialog |
| Assets                        | Zip asset file                          |
| Content CSS                   | CSS path inside asset zip               |
| Content JS                    | JS path inside asset zip                |
| Save dir                      | Public path for symlink unzipped asset  |

### Styles set preview

Using the style on a **WysiwygFieldType** you can enable `Styles set preview`. 

It will load the CSS and JS files when using the WYSIWYG field. 

In revision detail the text content will be rendered inside an iframe including the CSS and JS files.

> **TIP** 
> 
> The unzipping of the assets zip will be triggered when loading the CKEditor for the first time.
> 
> Updating the asset zip requires loading the WysiwygFieldType (make a new draft and discard).
