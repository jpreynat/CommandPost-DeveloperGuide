# [docs](index.md) » plugins.finalcutpro.commands.actions
---

An `action` which will execute a command with matching group/id values.
Registers itself with the `core.action.manager`.

## API Overview
* Functions - API calls offered directly by the extension
 * [execute](#execute)
 * [getId](#getid)
 * [init](#init)
 * [onChoices](#onchoices)
 * [reset](#reset)

## API Documentation

### Functions

#### [execute](#execute)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.finalcutpro.commands.actions.execute(action) -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Executes the action with the provided parameters.                                                                                         |
| **Parameters**                                       | <ul><li>* `action`  - A table representing the action, matching the following:</li><li>   `id`      - The specific Command ID within the group.</li></ul> |

#### [getId](#getid)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.finalcutpro.commands.actionss.getId(action) -> string` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Gets the ID from an action.                                                                                         |
| **Parameters**                                       | <ul><li>* action - The action table.</li></ul> |
| **Returns**                                          | <ul><li>* The ID as a string.</li></ul>          |

#### [init](#init)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.finalcutpro.commands.actions.init(actionmanager, cmds) -> none` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Initialises the module.                                                                                         |
| **Parameters**                                       | <ul><li>actionmanager - The action manager object</li><li>cmds - Final Cut Pro commands manager</li></ul> |
| **Returns**                                          | <ul><li>None</li></ul>          |

#### [onChoices](#onchoices)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.finalcutpro.commands.actionss.onChoices(choices) -> none` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Adds available choices to the  selection.                                                                                         |
| **Parameters**                                       | <ul><li>* `choices` - The `cp.choices` to add choices to.</li></ul> |
| **Returns**                                          | <ul><li>* None</li></ul>          |

#### [reset](#reset)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.finalcutpro.commands.actions.reset() -> nothing` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Resets the set of choices.                                                                                         |
| **Parameters**                                       | <ul><li>* None</li></ul> |
| **Returns**                                          | <ul><li>* Nothing</li></ul>          |

