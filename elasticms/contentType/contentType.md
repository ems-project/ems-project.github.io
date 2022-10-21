# ContentType

ContentType contain the structure, default environment and information for all related revisions.

<!-- TOC -->
* [ContentType](#contenttype)
  * [Properties](#properties)
  * [Roles](#roles)
<!-- TOC -->

## Properties

| Property             | Description                                  |
|----------------------|----------------------------------------------|
| name                 | Internal name                                |
| pluralName           | Display plural name                          |
| singularName         | Display single name                          |
| icon                 | Display icon in menu, dropdown, revision     |
| color                | Display color                                |
| description          | Internal description (not visible for users) |
| indexTwig            | **Deprecated**                               |
| extra                |                                              |
| circlesField         |                                              |
| businessIdField      |                                              |
| askForOuuid          |                                              |
| labelField           |                                              |
| colorField           |                                              |
| userField            |                                              |
| dateField            |                                              |
| startDateField       |                                              |
| endDateField         |                                              |
| locationField        |                                              |
| refererFieldName     |                                              |
| categoryField        |                                              |
| ouuidField           |                                              |
| imageField           |                                              |
| videoField           |                                              |
| emailField           |                                              |
| assetField           |                                              |
| orderField           |                                              |
| sortBy               |                                              |
| sortOrder            |                                              |
| orderKey             |                                              |
| rootContentType      |                                              |
| editTwigWithWysiwyg  |                                              |
| webContent           |                                              |
| autoPublish          |                                              |
| active               |                                              |
| environment          |                                              |
| defaultValue         |                                              |
| translationField     |                                              |
| localeField          |                                              |
| versionTags          |                                              |
| versionOptions       |                                              |
| versionDateFromField |                                              |
| versionDateToField   |                                              |
| roles                | Json field see [roles](#Roles)               |

## Roles

On a content type you can define a [user role](./elasticms/user/user.md#Roles) for permissions.

| Permission       | Description                                            |
|------------------|--------------------------------------------------------|
| view             | Display contentType in menu, enable dataLinks          |
| create           | Grant creation of new revisions                        |
| edit             | Grant update revision                                  |
| publish          | Grant publication to other environments                |
| delete           | Grant delete revision                                  |
| trash            | Trash functional enabled (put back deleted revisions)  |
| archive          | Grant archive revision (unpublish default environment) |
| owner            | Can be revision owners                                 |
| show_link_create | Display creation link in navigation                    |
| show_link_search | Display search link in navigation                      |
