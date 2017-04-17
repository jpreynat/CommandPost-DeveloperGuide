# [docs](index.md) » cp.commands.shortcut.builder
---

Shortcut Commands Builder Module.

## API Overview
* Methods - API calls which can only be made on an object returned by a constructor
 * [add](#add)
 * [new](#new)

## API Documentation

### Methods

| [add](#add)         |                                                                                     |
| --------------------------------------------|-------------------------------------------------------------------------------------|
| **Signature**                               | `cp.commands.shortcut.builder:add(modifier, [keyCode]) -> shortcut/command`                                                                    |
| **Type**                                    | Method                                                                     |
| **Description**                             | Adds the specified modifier to the set. If a `keyCode` is provided,                                                                     |
| **Parameters**                              | <ul><li>modifier - (optional) The modifier that was added.</li><li>keyCode	- (optional) The key code being modified.</li></ul> |
| **Returns**                                 | <ul><li>`self` if no `keyCode` is provided, or the original `command`.</li></ul>          |

| [new](#new)         |                                                                                     |
| --------------------------------------------|-------------------------------------------------------------------------------------|
| **Signature**                               | `cp.commands.shortcut.builder:new(receiverFn)`                                                                    |
| **Type**                                    | Method                                                                     |
| **Description**                             | Creates a new shortcut builder. If provided, the receiver function                                                                     |
| **Parameters**                              | <ul><li>None</li></ul> |
| **Returns**                                 | <ul><li>None</li></ul>          |
