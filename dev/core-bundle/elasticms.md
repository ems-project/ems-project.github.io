# Elasticms documentation

## Content Management

### Versioning

Documents share a version **uuid** and have a **from** and **to** date.
The document without to date is the current version. All revisions have a **version_tag** defined.

If a content type has at least one version tag, revisions versioning will be enabled.
You also can defined the date from and to fields.

Finalization is now called "publish in preview" (preview = contentType default environment).
A modal will popup on publication of a revision. The author needs to select a version_tag or silent.

If the author selects a version_tag:
- the current document will be updated and the from will be set to now()
- a new revision (snapshot) will be created from the previous revision with version end date set to now().

Revision bookmarks will not change, and tasks are allways on the latest version.

When the user selects 'silent', the revision will just be finalized. 
Silent publication is not available for new document, because each revision needs a version_tag.

The from and to dateField are managed by ems and can not be updated by the user.

#### Migration

If you want to enable versioning for an existing content type with documents.
The from date will be the creation date and the first version tag will be used as version tag. 

```bash
php bin/console ems:environment:updatemetafield preview
php bin/console ems:env:rebuild preview
```





 