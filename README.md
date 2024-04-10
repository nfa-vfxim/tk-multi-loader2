[![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/nfa-vfxim/tk-multi-loader2?include_prereleases)](https://github.com/nfa-vfxim/tk-multi-loader2) 
[![GitHub issues](https://img.shields.io/github/issues/nfa-vfxim/tk-multi-loader2)](https://github.com/nfa-vfxim/tk-multi-loader2/issues) 


# Loader <img src="icon_256.png" alt="Icon" height="24"/>

Locate published files and reference them into your scene.

## Requirements

| ShotGrid version | Core version | Engine version |
|------------------|--------------|----------------|
| -                | v0.19.1      | -              |

**Frameworks:**

| Name                      | Version | Minimum version |
|---------------------------|---------|-----------------|
| tk-framework-shotgunutils | v5.x.x  | v5.2.1          |
| tk-framework-qtwidgets    | v2.x.x  |                 |



## Configuration

### Strings

| Name         | Description                                   | Default value |
|--------------|-----------------------------------------------|---------------|
| `menu_name`  | Name to appear on the ShotGrid menu.          | Load          |
| `title_name` | Name to appear on the title of the UI Dialog. | Loader        |


### Hooks

| Name                    | Description                                                                                                           | Default value                   |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------------------|
| `actions_hook`          | Hook which contains all methods for action management.                                                                | {self}/{engine_name}_actions.py |
| `filter_publishes_hook` | Specify a hook that, if needed, can filter the raw list of publishes returned from ShotGrid for the current location. | {self}/filter_publishes.py      |


### Booleans

| Name                  | Description                                                                                                                                                                                                                                                                                   | Default value |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `download_thumbnails` | Controls whether thumbnails should be downloaded from ShotGrid or not. We strongly recommend that thumbnails are downloaded since this greatly enhances the user experience of the loader, however in some situations this may be difficult due to bandwidth or infrastructural restrictions. | True          |


### Dictionaries

| Name              | Description                                                                                        | Default value |
|-------------------|----------------------------------------------------------------------------------------------------|---------------|
| `action_mappings` | Associates published file types with actions. The actions are all defined inside the actions hook. | {}            |
| `entity_mappings` | Associates entity types with actions. The actions are all defined inside the actions hook.         | {}            |


### Lists

| Name              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Default value                                                                                                                                                                                                                                                                                                                  |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `entities`        | This setting defines the different tabs that will show up on the left hand side. Each tab represents a ShotGrid query, grouped by some ShotGrid fields to form a tree. This setting is a list of dictionaries. Each dictionary in the list defines one tab. Dictionaries with their *type* key set to 'Hierarchy' should have they following keys: *caption* specifies the name of the tab, *root* specifies the path to the root of the project hierarchy to display. Dictionaries with their *type* key set to 'Query' should have they following keys: *caption* specifies the name of the tab, *entity_type* specifies the ShotGrid entity type to display. *filters* is a list of standard API ShotGrid filters. *hierarchy* is a list of ShotGrid fields, defining the grouping of the tree. Optionally, you can specify a *publish_filters* key, containing ShotGrid API filters to apply to the publishes listing as it is being loaded in the main view. | [{'caption': 'Project', 'type': 'Hierarchy', 'root': '{context.project}', 'publish_filters': []}, {'caption': 'My Tasks', 'type': 'Query', 'entity_type': 'Task', 'publish_filters': [], 'filters': [['task_assignees', 'is', '{context.user}'], ['project', 'is', '{context.project}']], 'hierarchy': ['entity', 'content']}] |
| `publish_filters` | List of additional ShotGrid filters to apply to the publish listings.  These will be applied before any other filtering takes place and would allow you to for example hide things with a certain status.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | []                                                                                                                                                                                                                                                                                                                             |


