# [docs](index.md) » hs.tabs
---

Place the windows of an application into tabs drawn on its titlebar

## API Overview
* Functions - API calls offered directly by the extension
 * [enableForApp](#enableforapp)
 * [focusTab](#focustab)
 * [tabWindows](#tabwindows)

## API Documentation

### Functions

#### [enableForApp](#enableforapp)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.tabs.enableForApp(app)` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Places all the windows of an app into one place and tab them                                                                                         |
| **Parameters**                                       | <ul><li>app - An `hs.application` object or the app title</li></ul> |
| **Returns**                                          | <ul><li>None</li></ul>          |

#### [focusTab](#focustab)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.tabs.focusTab(app, num)` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Focuses a specific tab of an app                                                                                         |
| **Parameters**                                       | <ul><li>app - An `hs.application` object previously enabled for tabbing</li><li>num - A tab number to switch to</li></ul> |
| **Returns**                                          | <ul><li>None</li></ul>          |
| **Notes**                                            | <ul><li>If num is higher than the number of tabs, the last tab will be focussed</li></ul>                |

#### [tabWindows](#tabwindows)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.tabs.tabWindows(app)` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Gets a list of the tabs of a window                                                                                         |
| **Parameters**                                       | <ul><li>app - An `hs.application` object</li></ul> |
| **Returns**                                          | <ul><li>An array of the tabbed windows of an app in the same order as they would be tabbed</li></ul>          |
| **Notes**                                            | <ul><li>This function can be used when writing tab switchers</li></ul>                |

