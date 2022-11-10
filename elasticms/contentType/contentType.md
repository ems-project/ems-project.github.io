# ContentType

ContentType contain the structure, default environment and information for all related revisions.

<!-- TOC -->
* [ContentType](#contenttype)
  * [Properties](#properties)
  * [Default value](#default-value)
  * [Fields](#fields)
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
| askForOuuid          |                                              |
| refererFieldName     |                                              |
| sortOrder            |                                              |
| rootContentType      |                                              |
| editTwigWithWysiwyg  |                                              |
| webContent           |                                              |
| autoPublish          |                                              |
| active               |                                              |
| environment          |                                              |
| defaultValue         | See [Default value](#default-value)          |
| versionTags          |                                              |
| versionOptions       |                                              |
| versionDateFromField |                                              |
| versionDateToField   |                                              |
| roles                | Json field see [roles](#Roles)               |
| fields               | Json field see [fields](#Fields)             |

## Default value

On a content type you can define a default value for the revisions.
The result should be a valid JSON rendered by Twig template.

> **Template context**
> 
> * `environment` : the default environment of the content type
> * `contentType` : the content type entity
> * `currentUser` : the authenticated user

## Fields

On a content type we can define fields from the elasticsearch mapping.
These are used for displaying revision information.

| Field       | Description                                              |
|-------------|----------------------------------------------------------|
| label       | Display label for the revision                           |
| color       | Display color for the revision                           |
| sort        | Default sorting in choice lists (better use querySearch) |
| tooltip     | Add tooltip on dataLinks                                 |
| circles     | Field containing the revision circles                    |
| business_id | Used in export/import documents                          |
| category    | Used in criteria view                                    |
| asset       | Used in asset link from WYSIWYG                          |

## Roles

On a content type you can define a [user role](./elasticms/user/user.md#Roles) for permissions.

| Permission       | Description                                                                                                                                  |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| view             | Display contentType in menu, enable dataLinks                                                                                                |
| create           | Grant creation of new revisions                                                                                                              |
| edit             | Grant update revision                                                                                                                        |
| publish          | Grant publication to other environments, can be overruled by [environment publish role](./elasticms/environment/environment.md#publish-role) |
| delete           | Grant delete revision                                                                                                                        |
| trash            | Trash functional enabled (put back deleted revisions)                                                                                        |
| archive          | Grant archive revision (unpublish default environment)                                                                                       |
| owner            | Can be revision owners                                                                                                                       |
| show_link_create | Display creation link in navigation                                                                                                          |
| show_link_search | Display search link in navigation                                                                                                            |

