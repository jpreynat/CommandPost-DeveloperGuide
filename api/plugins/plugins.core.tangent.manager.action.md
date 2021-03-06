# [docs](index.md) » plugins.core.tangent.manager.action
---

Represents a Tangent Action

## API Overview
* Constructors - API calls which return an object, typically one that offers API methods
 * [new](#new)
* Methods - API calls which can only be made on an object returned by a constructor
 * [controls](#controls)
 * [onPress](#onpress)
 * [onRelease](#onrelease)
 * [parent](#parent)
 * [xml](#xml)

## API Documentation

### Constructors

#### [new](#new)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.action.new(id[, name]) -> action` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Constructor                                                                                         |
| **Description**                                      | Creates a new `Action` instance.                                                                                         |
| **Parameters**                                       | <ul><li>* id        - The ID number of the action.</li><li>* name      - The name of the action.</li></ul> |
| **Returns**                                          | <ul><li>* the new `action`.</li></ul>          |

### Methods

#### [controls](#controls)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.action:controls()` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Returns the `controls` the action belongs to.                                                                                         |
| **Parameters**                                       | <ul><li>* None</li></ul> |
| **Returns**                                          | <ul><li>* The `controls`, or `nil` if not specified.</li></ul>          |

#### [onPress](#onpress)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.action:onPress(pressFn) -> self` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Sets the function that will be called when the Tangent sends a 'action on' request.                                                                                         |
| **Parameters**                                       | <ul><li>* pressFn     - The function to call when the Tangent requests the action on.</li></ul> |
| **Returns**                                          | <ul><li>* The `parameter` instance.</li></ul>          |

#### [onRelease](#onrelease)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.action:onRelease(releaseFn) -> self` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Sets the function that will be called when the Tangent sends a 'action off' request.                                                                                         |
| **Parameters**                                       | <ul><li>* releaseFn     - The function to call when the Tangent requests the action off.</li></ul> |
| **Returns**                                          | <ul><li>* The `parameter` instance.</li></ul>          |

#### [parent](#parent)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.action:parent() -> group | controls` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Returns the `group` or `controls` that contains this action.                                                                                         |
| **Parameters**                                       | <ul><li>* None</li></ul> |
| **Returns**                                          | <ul><li>* The action's parent.</li></ul>          |

#### [xml](#xml)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.action:xml() -> cp.web.xml` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Returns the `xml` configuration for the Action.                                                                                         |
| **Parameters**                                       | <ul><li>* None</li></ul> |
| **Returns**                                          | <ul><li>* The `xml` for the Action.</li></ul>          |

