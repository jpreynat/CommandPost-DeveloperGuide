# [docs](index.md) » hs.inspect
---

Produce human-readable representations of Lua variables (particularly tables)

This extension is based on inspect.lua by Enrique García Cota
https://github.com/kikito/inspect.lua

## API Overview
* Functions - API calls offered directly by the extension
 * [inspect](#inspect)

## API Documentation

### Functions

#### [inspect](#inspect)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.inspect.inspect(variable[, options]) -> string` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Gets a human readable version of the supplied Lua variable                                                                                         |
| **Parameters**                                       | <ul><li>variable - A lua variable of some kind</li><li>options - An optional table which can be used to influence the inspector. Valid keys are as follows:</li><li> depth - A number representing the maximum depth to recurse into `variable`. Below that depth, data will be displayed as `{...}`</li><li> newline - A string to use for line breaks. Defaults to `\n`</li><li> indent - A string to use for indentation. Defaults to `  ` (two spaces)</li><li> process - A function that will be called for each item. It should accept two arguments, `item` (the current item being processed) and `path` (the item's position in the variable being inspected. The function should either return a processed form of the variable, the original variable itself if it requires no processing, or `nil` to remove the item from the inspected output.</li><li> metatables - If `true`, include (and traverse) metatables</li></ul> |
| **Returns**                                          | <ul><li>A string containing the human readable version of `variable`</li></ul>          |
| **Notes**                                            | <ul><li>For convenience, you can call this function as `hs.inspect(variable)`</li><li>For more information on the options, and some examples, see [the upstream docs](https://github.com/kikito/inspect.lua)</li></ul>                |

