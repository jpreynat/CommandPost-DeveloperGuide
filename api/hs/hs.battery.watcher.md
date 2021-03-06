# [docs](index.md) » hs.battery.watcher
---

Watch for battery/power state changes

This module is based primarily on code from the previous incarnation of Mjolnir by [Steven Degutis](https://github.com/sdegutis/).

## API Overview
* Constructors - API calls which return an object, typically one that offers API methods
 * [new](#new)
* Methods - API calls which can only be made on an object returned by a constructor
 * [start](#start)
 * [stop](#stop)

## API Documentation

### Constructors

#### [new](#new)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.battery.watcher.new(fn) -> watcher` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Constructor                                                                                         |
| **Description**                                      | Creates a battery watcher                                                                                         |
| **Parameters**                                       | <ul><li>A function that will be called when the battery state changes. The function should accept no arguments.</li></ul> |
| **Returns**                                          | <ul><li>An `hs.battery.watcher` object</li></ul>          |
| **Notes**                                            | <ul><li>Because the callback function accepts no arguments, tracking of state of changing battery attributes is the responsibility of the user (see https://github.com/Hammerspoon/hammerspoon/issues/166 for discussion)</li></ul>                |

### Methods

#### [start](#start)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.battery.watcher:start() -> self` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Starts the battery watcher                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The `hs.battery.watcher` object</li></ul>          |

#### [stop](#stop)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.battery.watcher:stop() -> self` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Stops the battery watcher                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The `hs.battery.watcher` object</li></ul>          |

