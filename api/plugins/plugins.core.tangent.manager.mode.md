# [docs](index.md) » plugins.core.tangent.manager.mode
---

Represents a Tangent Mode

## API Overview
* Functions - API calls offered directly by the extension
 * [is](#is)
* Constructors - API calls which return an object, typically one that offers API methods
 * [new](#new)
* Methods - API calls which can only be made on an object returned by a constructor
 * [activate](#activate)
 * [onActivate](#onactivate)
 * [onDeactivate](#ondeactivate)
 * [xml](#xml)

## API Documentation

### Functions

#### [is](#is)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.mode.is(other) -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Checks to see if other is a mode or not.                                                                                         |
| **Parameters**                                       | <ul><li>other - The item to check</li></ul> |
| **Returns**                                          | <ul><li>`true` if is a mode otherwise `false`</li></ul>          |

### Constructors

#### [new](#new)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.mode.new(id, name)` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Constructor                                                                                         |
| **Description**                                      | Creates a new `Mode` instance.                                                                                         |
| **Parameters**                                       | <ul><li>id        - The ID number of the mode.</li><li>name      - The name of the mode.</li></ul> |
| **Returns**                                          | <ul><li> *</li></ul>          |

### Methods

#### [activate](#activate)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.mode:activate() -> nil` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Executes the `activate` function, if present.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>`nil`</li></ul>          |

#### [onActivate](#onactivate)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.mode:onActivate(activateFn) -> self` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Sets the function that will be called when the Tangent sends a 'mode change' request.                                                                                         |
| **Parameters**                                       | <ul><li>activateFn     - The function to call when the Tangent requests the mode change.</li></ul> |
| **Returns**                                          | <ul><li>The `parameter` instance.</li></ul>          |

#### [onDeactivate](#ondeactivate)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.mode:onDeactivate(deactivateFn) -> self` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Sets the function that will be called when the Tangent sends a 'mode change' request and switche to a different mode.                                                                                         |
| **Parameters**                                       | <ul><li>deactivateFn     - The function to call when the Tangent requests the mode change.</li></ul> |
| **Returns**                                          | <ul><li>The `parameter` instance.</li></ul>          |

#### [xml](#xml)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`plugins.core.tangent.manager.mode:xml() -> cp.web.xml` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Returns the `xml` configuration for the Mode.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The `xml` for the Mode.</li></ul>          |

