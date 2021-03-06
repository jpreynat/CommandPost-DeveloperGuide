# [docs](index.md) » cp.apple.finalcutpro.main.KeywordEditor.KeyboardShortcuts
---

Keyboard Shortcuts

## API Overview
* Methods - API calls which can only be made on an object returned by a constructor
 * [apply](#apply)
 * [hide](#hide)
 * [isShowing](#isshowing)
 * [keyword](#keyword)
 * [new](#new)
 * [parent](#parent)
 * [removeAllKeywords](#removeallkeywords)
 * [show](#show)

## API Documentation

### Methods

#### [apply](#apply)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.main.KeywordEditor.KeyboardShortcuts:apply(item) -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Applies a Keyword Shortcut.                                                                                         |
| **Parameters**                                       | <ul><li>item - The textbox you want to update. This can be a number between 1 and 9.</li></ul> |
| **Returns**                                          | <ul><li>`true` if successful otherwise `false`</li></ul>          |

#### [hide](#hide)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.main.KeywordEditor.KeyboardShortcuts:hide() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Hides the Keyword Editor's Keyboard Shortcuts section.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>`true` if successful otherwise `false`</li></ul>          |

#### [isShowing](#isshowing)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.main.KeywordEditor.KeyboardShortcuts:isShowing() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Gets whether or not the Keyword Editor's Keyboard Shortcuts section is currently showing.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>`true` if showing otherwise `false`</li></ul>          |

#### [keyword](#keyword)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.main.KeywordEditor.KeyboardShortcuts:keyword(item, value) -> string | table | nil` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Sets or gets a specific Keyboard Shortcut Keyword Textbox value.                                                                                         |
| **Parameters**                                       | <ul><li>item - The textbox you want to update. This can be a number between 1 and 9.</li><li>value - The value you want to set the keyword textbox to. This can either be a string, with the tags separated by a comma, or a table of tags.</li></ul> |
| **Returns**                                          | <ul><li>`value` if successful otherwise `false`</li></ul>          |

#### [new](#new)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.main.KeywordEditor.KeyboardShortcuts:new(parent) -> KeyboardShortcuts object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Creates a new KeyboardShortcuts object                                                                                         |
| **Parameters**                                       | <ul><li>`parent` - The parent</li></ul> |
| **Returns**                                          | <ul><li>A KeyboardShortcuts object</li></ul>          |

#### [parent](#parent)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.main.KeywordEditor.KeyboardShortcuts:parent() -> table` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Returns the KeywordShortcuts's parent table                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The parent object as a table</li></ul>          |

#### [removeAllKeywords](#removeallkeywords)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.main.KeywordEditor.KeyboardShortcuts:removeAllKeywords() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Triggers the "Remove all Keywords" button.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>`true` if successful otherwise `false`</li></ul>          |

#### [show](#show)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.main.KeywordEditor.KeyboardShortcuts:show() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Shows the Keyword Editor's Keyboard Shortcuts section.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>`true` if successful otherwise `false`</li></ul>          |

