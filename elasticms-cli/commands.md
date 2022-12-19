# EMS (CommonBundle) Commands

<!-- TOC -->
* [EMS Commands](#ems-commonbundle-commands)
  * [Admin](#admin)
    * [Backup](#backup)
<!-- TOC -->

### Admin

#### Backup

The command downloads the configuration (JSON files for content types, environments, ...) and documents (JSON files) for all managed content types.

Be cautious that the document are downloaded from the elasticsearch's default indexes. So ensure that your elasticsearch's indexes are well synchronized. Only the last finalized revision will be archived.

```bash
Usage:
  ems:admin:backup [options]

Options:
      --export                               Backup elasticMS's configs in JSON files (dry run by default)
      --export-folder[=EXPORT-FOLDER]        Global export folder (can be overwritten per type of exports)
      --configs-folder[=CONFIGS-FOLDER]      Export configs folder
      --documents-folder[=DOCUMENTS-FOLDER]  Export documents folder
```

