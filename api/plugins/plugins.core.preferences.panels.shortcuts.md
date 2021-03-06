# [docs](index.md) » plugins.core.preferences.panels.shortcuts
---

Shortcuts Preferences Panel

## API Overview
* Constants - Useful values which cannot be changed
 * [DEFAULT_SHORTCUTS](#default_shortcuts)
* Functions - API calls offered directly by the extension
 * [getGroupEditor](#getgroupeditor)
 * [init](#init)
 * [setGroupEditor](#setgroupeditor)
* Fields - Variables which can only be accessed from an object returned by a constructor
 * [lastGroup](#lastgroup)

## API Documentation

### Constants

#### [DEFAULT_SHORTCUTS](#default_shortcuts)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.preferences.panels.shortcuts.DEFAULT_SHORTCUTS -> string` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Constant                                                                                         |
| **Description**                                      | Default Shortcuts File Name                                                                                         |

### Functions

#### [getGroupEditor](#getgroupeditor)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.preferences.panels.shortcuts.getGroupEditor(groupId) -> none` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Gets the Group Editor                                                                                         |
| **Parameters**                                       | <ul><li>groupId - Group ID</li></ul> |
| **Returns**                                          | <ul><li>Group Editor</li></ul>          |

#### [init](#init)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.preferences.panels.shortcuts.init(deps, env) -> module` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Initialise the Module.                                                                                         |
| **Parameters**                                       | <ul><li>deps - Dependancies Table</li><li>env - Environment Table</li></ul> |
| **Returns**                                          | <ul><li>The Module</li></ul>          |

#### [setGroupEditor](#setgroupeditor)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.preferences.panels.shortcuts.setGroupEditor(groupId, editorFn) -> none` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Sets the Group Editor                                                                                         |
| **Parameters**                                       | <ul><li>groupId - Group ID</li><li>editorFn - Editor Function</li></ul> |
| **Returns**                                          | <ul><li>None</li></ul>          |

### Fields

#### [lastGroup](#lastgroup)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.preferences.panels.shortcuts.lastGroup <cp.prop: string>` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Field                                                                                         |
| **Description**                                      | Last group used in the Preferences Drop Down.                                                                                         |

