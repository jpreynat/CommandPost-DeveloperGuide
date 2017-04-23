# [docs](index.md) » cp.apple.finalcutpro
---

Represents the Final Cut Pro application, providing functions that allow different tasks to be accomplished.

This module provides an API to work with the FCPX application. There are a couple of types of files:

* `init.lua` - the main module that gets imported.
* `axutils.lua` - some utility functions for working with `axuielement` objects.
* `test.lua` - some support functions for testing. TODO: Make this better.

Generally, you will `require` the `cp.finalcutpro` module to import it, like so:

```lua
local fcp = require("cp.apple.finalcutpro")
```

Then, there are the `UpperCase` files, which represent the application itself:

* `MenuBar` 	- The main menu bar.
* `prefs/PreferencesWindow` - The preferences window.
* etc...

The `fcp` variable is the root application. It has functions which allow you to perform tasks or access parts of the UI. For example, to open the `Preferences` window, you can do this:

```lua
fcp:preferencesWindow():show()
```

In general, as long as FCPX is running, actions can be performed directly, and the API will perform the required operations to achieve it. For example, to toggle the 'Create Optimized Media' checkbox in the 'Import' section of the 'Preferences' window, you can simply do this:

```lua
fcp:preferencesWindow():importPanel():toggleCreateOptimizedMedia()
```

The API will automatically open the `Preferences` window, navigate to the 'Import' panel and toggle the checkbox.

The `UpperCase` classes also have a variety of `UI` methods. These will return the `axuielement` for the relevant GUI element, if it is accessible. If not, it will return `nil`. These allow direct interaction with the GUI if necessary. It's most useful when adding new functions to `UpperCase` files for a particular element.

This can also be used to 'wait' for an element to be visible before performing a task. For example, if you need to wait for the `Preferences` window to finish loading before doing something else, you can do this with the `cp.just` library:

```lua
local just = require("cp.just")

local prefsWindow = fcp:preferencesWindow()

local prefsUI = just.doUntil(function() return prefsWindow:UI() end)

if prefsUI then
	-- it's open!
else
	-- it's closed!
end
```

By using the `just` library, we can do a loop waiting until the function returns a result that will give up after a certain time period (10 seconds by default).

Of course, we have a specific support function for that already, so you could do this instead:

```lua
if fcp:preferencesWindow():isShowing() then
	-- it's open!
else
	-- it's closed!
end
```

## Submodules
 * [cp.apple.finalcutpro.MenuBar](cp.apple.finalcutpro.MenuBar.md)
 * [cp.apple.finalcutpro.axutils](cp.apple.finalcutpro.axutils.md)
 * [cp.apple.finalcutpro.cmd](cp.apple.finalcutpro.cmd.md)
 * [cp.apple.finalcutpro.destinations](cp.apple.finalcutpro.destinations.md)
 * [cp.apple.finalcutpro.export](cp.apple.finalcutpro.export.md)
 * [cp.apple.finalcutpro.ids](cp.apple.finalcutpro.ids.md)
 * [cp.apple.finalcutpro.import](cp.apple.finalcutpro.import.md)
 * [cp.apple.finalcutpro.keycodes](cp.apple.finalcutpro.keycodes.md)
 * [cp.apple.finalcutpro.main](cp.apple.finalcutpro.main.md)
 * [cp.apple.finalcutpro.prefs](cp.apple.finalcutpro.prefs.md)
 * [cp.apple.finalcutpro.ui](cp.apple.finalcutpro.ui.md)

## API Overview
* Constants - Useful values which cannot be changed
 * [BUNDLE_ID](#bundle_id)
 * [EARLIEST_SUPPORTED_VERSION](#earliest_supported_version)
 * [FLEXO_LANGUAGES](#flexo_languages)
 * [PASTEBOARD_UTI](#pasteboard_uti)
 * [PREFS_PLIST_PATH](#prefs_plist_path)
 * [SUPPORTED_LANGUAGES](#supported_languages)
* Functions - API calls offered directly by the extension
 * [application](#application)
 * [browser](#browser)
 * [colorBoard](#colorboard)
 * [commandEditor](#commandeditor)
 * [effects](#effects)
 * [eventViewer](#eventviewer)
 * [exportDialog](#exportdialog)
 * [fullScreenWindow](#fullscreenwindow)
 * [generators](#generators)
 * [getActiveCommandSet](#getactivecommandset)
 * [getActiveCommandSetPath](#getactivecommandsetpath)
 * [getBundleID](#getbundleid)
 * [getCommandSet](#getcommandset)
 * [getCommandShortcuts](#getcommandshortcuts)
 * [getCurrentLanguage](#getcurrentlanguage)
 * [getDefaultCommandSetPath](#getdefaultcommandsetpath)
 * [getFlexoLanguages](#getflexolanguages)
 * [getPasteboardUTI](#getpasteboarduti)
 * [getPreference](#getpreference)
 * [getPreferences](#getpreferences)
 * [getSupportedLanguages](#getsupportedlanguages)
 * [getVersion](#getversion)
 * [hide](#hide)
 * [importXML](#importxml)
 * [inspector](#inspector)
 * [isFrontmost](#isfrontmost)
 * [isInstalled](#isinstalled)
 * [isRunning](#isrunning)
 * [launch](#launch)
 * [libraries](#libraries)
 * [media](#media)
 * [mediaImport](#mediaimport)
 * [menuBar](#menubar)
 * [new](#new)
 * [path](#path)
 * [performShortcut](#performshortcut)
 * [preferencesWindow](#preferenceswindow)
 * [primaryWindow](#primarywindow)
 * [quit](#quit)
 * [restart](#restart)
 * [secondaryWindow](#secondarywindow)
 * [selectMenu](#selectmenu)
 * [setPreference](#setpreference)
 * [show](#show)
 * [timeline](#timeline)
 * [transitions](#transitions)
 * [viewer](#viewer)
 * [windowsUI](#windowsui)
* Methods - API calls which can only be made on an object returned by a constructor
 * [unwatch](#unwatch)
 * [watch](#watch)

## API Documentation

### Constants

#### [BUNDLE_ID](#bundle_id)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.BUNDLE_ID` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Constant                                                                                         |
| **Description**                                      | Final Cut Pro's Bundle ID                                                                                         |

#### [EARLIEST_SUPPORTED_VERSION](#earliest_supported_version)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.EARLIEST_SUPPORTED_VERSION` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Constant                                                                                         |
| **Description**                                      | The earliest version of Final Cut Pro supported by this module.                                                                                         |

#### [FLEXO_LANGUAGES](#flexo_languages)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.FLEXO_LANGUAGES` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Constant                                                                                         |
| **Description**                                      | Table of Final Cut Pro's supported Languages for the Flexo Framework                                                                                         |

#### [PASTEBOARD_UTI](#pasteboard_uti)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.PASTEBOARD_UTI` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Constant                                                                                         |
| **Description**                                      | Final Cut Pro's Pasteboard UTI                                                                                         |

#### [PREFS_PLIST_PATH](#prefs_plist_path)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.PREFS_PLIST_PATH` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Constant                                                                                         |
| **Description**                                      | Final Cut Pro's Preferences Path                                                                                         |

#### [SUPPORTED_LANGUAGES](#supported_languages)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.SUPPORTED_LANGUAGES` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Constant                                                                                         |
| **Description**                                      | Table of Final Cut Pro's supported Languages                                                                                         |

### Functions

#### [application](#application)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:application() -> hs.application` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the hs.application for Final Cut Pro.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The hs.application, or nil if the application is not installed.</li></ul>          |

#### [browser](#browser)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:browser() -> Browser` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Browser instance, whether it is in the primary or secondary window.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the Browser</li></ul>          |

#### [colorBoard](#colorboard)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:colorBoard() -> ColorBoard` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the ColorBoard instance from the primary window                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the ColorBoard</li></ul>          |

#### [commandEditor](#commandeditor)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:commandEditor() -> commandEditor object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Final Cut Pro Command Editor                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The Final Cut Pro Command Editor</li></ul>          |

#### [effects](#effects)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:effects() -> EffectsBrowser` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the EffectsBrowser instance, whether it is in the primary or secondary window.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the EffectsBrowser</li></ul>          |

#### [eventViewer](#eventviewer)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:eventViewer() -> Event Viewer` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Event Viewer instance, whether it is in the primary or secondary window.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the Event Viewer</li></ul>          |

#### [exportDialog](#exportdialog)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:exportDialog() -> exportDialog object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Final Cut Pro Export Dialog Box                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The Final Cut Pro Export Dialog Box</li></ul>          |

#### [fullScreenWindow](#fullscreenwindow)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:fullScreenWindow() -> fullScreenWindow object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Final Cut Pro Full Screen Window                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The Full Screen Playback Window</li></ul>          |

#### [generators](#generators)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:generators() -> GeneratorsBrowser` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the GeneratorsBrowser instance, whether it is in the primary or secondary window.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the GeneratorsBrowser</li></ul>          |

#### [getActiveCommandSet](#getactivecommandset)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:getActiveCommandSet([forceReload]) -> table or nil` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the 'Active Command Set' as a Table. The result is cached, so pass in                                                                                         |
| **Parameters**                                       | <ul><li>forceReload	- (optional) If `true`, require the Command Set to be reloaded.</li></ul> |
| **Returns**                                          | <ul><li>A table of the Active Command Set's contents, or `nil` if an error occurred</li></ul>          |

#### [getActiveCommandSetPath](#getactivecommandsetpath)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:getActiveCommandSetPath() -> string or nil` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Gets the 'Active Command Set' value from the Final Cut Pro preferences                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The 'Active Command Set' value, or the 'Default' command set if none is set.</li></ul>          |

#### [getBundleID](#getbundleid)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:getBundleID() -> string` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Final Cut Pro Bundle ID                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>A string of the Final Cut Pro Bundle ID</li></ul>          |

#### [getCommandSet](#getcommandset)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:getCommandSet(path) -> string` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Loads the Command Set at the specified path into a table.                                                                                         |
| **Parameters**                                       | <ul><li>`path`	- The path to the command set.</li></ul> |
| **Returns**                                          | <ul><li>The Command Set as a table, or `nil` if there was a problem.</li></ul>          |

#### [getCommandShortcuts](#getcommandshortcuts)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.getCommandShortcuts(id) -> table of hs.commands.shortcut` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Finds a shortcut from the Active Command Set with the specified ID and returns a table                                                                                         |
| **Parameters**                                       | <ul><li>id - The unique ID for the command.</li></ul> |
| **Returns**                                          | <ul><li>The array of shortcuts, or `nil` if no command exists with the specified `id`.</li></ul>          |

#### [getCurrentLanguage](#getcurrentlanguage)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:getCurrentLanguage() -> string` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the language Final Cut Pro is currently using.                                                                                         |
| **Parameters**                                       | <ul><li>none</li></ul> |
| **Returns**                                          | <ul><li>Returns the current language as string (or 'en' if unknown).</li></ul>          |

#### [getDefaultCommandSetPath](#getdefaultcommandsetpath)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:getDefaultCommandSetPath([langauge]) -> string` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Gets the path to the 'Default' Command Set.                                                                                         |
| **Parameters**                                       | <ul><li>`language`	- (optional) The language code to use. Defaults to the current FCPX language.</li></ul> |
| **Returns**                                          | <ul><li>The 'Default' Command Set path, or `nil` if an error occurred</li></ul>          |

#### [getFlexoLanguages](#getflexolanguages)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:getFlexoLanguages() -> table` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns a table of languages Final Cut Pro's Flexo Framework supports                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>A table of languages Final Cut Pro supports</li></ul>          |

#### [getPasteboardUTI](#getpasteboarduti)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:getPasteboardUTI() -> axuielementObject` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Final Cut Pro axuielementObject                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>A axuielementObject of Final Cut Pro</li></ul>          |

#### [getPreference](#getpreference)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.getPreference(value, default, forceReload) -> string or nil` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Get an individual Final Cut Pro preference                                                                                         |
| **Parameters**                                       | <ul><li>value 			- The preference you want to return</li><li>default			- (optional) The default value to return if the preference is not set.</li><li>forceReload		= (optional) If true, forces a reload of the app's preferences.</li></ul> |
| **Returns**                                          | <ul><li>A string with the preference value, or nil if an error occurred</li></ul>          |

#### [getPreferences](#getpreferences)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:getPreferences() -> table or nil` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Gets Final Cut Pro's Preferences as a table. It checks if the preferences                                                                                         |
| **Parameters**                                       | <ul><li>forceReload	- (optional) if true, a reload will be forced even if the file hasn't been modified.</li><li>preventMultipleReloads - (optional) if true, adds a 0.01 delay before reloading preferences (for use with the watcher)</li></ul> |
| **Returns**                                          | <ul><li>A table with all of Final Cut Pro's preferences, or nil if an error occurred</li></ul>          |

#### [getSupportedLanguages](#getsupportedlanguages)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:getSupportedLanguages() -> table` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns a table of languages Final Cut Pro supports                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>A table of languages Final Cut Pro supports</li></ul>          |

#### [getVersion](#getversion)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:getVersion() -> string or nil` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Version of Final Cut Pro                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>Version as string or nil if an error occurred</li></ul>          |
| **Notes**                                            | <ul><li>If Final Cut Pro is running it will get the version of the active Final Cut Pro application, otherwise, it will use hs.application.infoForBundleID() to find the version.</li></ul>                |

#### [hide](#hide)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:hide() -> cp.finalcutpro object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Hides Final Cut Pro                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>An cp.finalcutpro object otherwise nil</li></ul>          |

#### [importXML](#importxml)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:importXML() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Imports an XML file into Final Cut Pro                                                                                         |
| **Parameters**                                       | <ul><li>path = Path to XML File</li></ul> |
| **Returns**                                          | <ul><li>A boolean value indicating whether the AppleScript succeeded or not</li></ul>          |

#### [inspector](#inspector)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:inspector() -> Inspector` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Inspector instance from the primary window                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the Inspector</li></ul>          |

#### [isFrontmost](#isfrontmost)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:isFrontmost() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Is Final Cut Pro Frontmost?                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>`true` if Final Cut Pro is Frontmost.</li></ul>          |

#### [isInstalled](#isinstalled)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:isInstalled() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Is a supported version of Final Cut Pro Installed?                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>`true` if a supported version of Final Cut Pro is installed otherwise `false`</li></ul>          |

#### [isRunning](#isrunning)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:isRunning() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Is Final Cut Pro Running?                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>True if Final Cut Pro is running otherwise False</li></ul>          |

#### [launch](#launch)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:launch() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Launches Final Cut Pro, or brings it to the front if it was already running.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>`true` if Final Cut Pro was either launched or focused, otherwise false (e.g. if Final Cut Pro doesn't exist)</li></ul>          |

#### [libraries](#libraries)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:libraries() -> LibrariesBrowser` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the LibrariesBrowser instance, whether it is in the primary or secondary window.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the LibrariesBrowser</li></ul>          |

#### [media](#media)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:media() -> MediaBrowser` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the MediaBrowser instance, whether it is in the primary or secondary window.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the MediaBrowser</li></ul>          |

#### [mediaImport](#mediaimport)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:mediaImport() -> mediaImport object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Final Cut Pro Media Import Window                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The Final Cut Pro Media Import Window</li></ul>          |

#### [menuBar](#menubar)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:menuBar() -> menuBar object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Final Cut Pro Menu Bar                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>A menuBar object</li></ul>          |

#### [new](#new)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:new() -> App` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Creates a new App instance representing Final Cut Pro                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>True is successful otherwise Nil</li></ul>          |

#### [path](#path)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:path() -> string or nil` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Path to Final Cut Pro Application                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>A string containing Final Cut Pro's filesystem path, or nil if the bundle identifier could not be located</li></ul>          |

#### [performShortcut](#performshortcut)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro.performShortcut() -> Boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Performs a Final Cut Pro Shortcut                                                                                         |
| **Parameters**                                       | <ul><li>whichShortcut - As per the Command Set name</li></ul> |
| **Returns**                                          | <ul><li>true if successful otherwise false</li></ul>          |

#### [preferencesWindow](#preferenceswindow)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:preferencesWindow() -> preferenceWindow object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Final Cut Pro Preferences Window                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The Preferences Window</li></ul>          |

#### [primaryWindow](#primarywindow)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:primaryWindow() -> primaryWindow object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Final Cut Pro Preferences Window                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The Primary Window</li></ul>          |

#### [quit](#quit)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:quit() -> cp.finalcutpro object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Quits Final Cut Pro                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>An cp.finalcutpro object otherwise nil</li></ul>          |

#### [restart](#restart)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:restart() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Restart Final Cut Pro                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>`true` if Final Cut Pro was running and restarted successfully.</li></ul>          |

#### [secondaryWindow](#secondarywindow)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:secondaryWindow() -> secondaryWindow object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Final Cut Pro Preferences Window                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The Secondary Window</li></ul>          |

#### [selectMenu](#selectmenu)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:selectMenu(...) -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Selects a Final Cut Pro Menu Item based on the list of menu titles in English.                                                                                         |
| **Parameters**                                       | <ul><li>... - The list of menu items you'd like to activate, for example:</li><li>           select("View", "Browser", "as List")</li></ul> |
| **Returns**                                          | <ul><li>`true` if the press was successful.</li></ul>          |

#### [setPreference](#setpreference)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:setPreference(key, value) -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Sets an individual Final Cut Pro preference                                                                                         |
| **Parameters**                                       | <ul><li>key - The preference you want to change</li><li>value - The value you want to set for that preference</li></ul> |
| **Returns**                                          | <ul><li>True if executed successfully otherwise False</li></ul>          |

#### [show](#show)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:show() -> cp.finalcutpro object` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Activate Final Cut Pro                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>An cp.finalcutpro object otherwise nil</li></ul>          |

#### [timeline](#timeline)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:timeline() -> Timeline` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Timeline instance, whether it is in the primary or secondary window.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the Timeline</li></ul>          |

#### [transitions](#transitions)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:transitions() -> TransitionsBrowser` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the TransitionsBrowser instance, whether it is in the primary or secondary window.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the TransitionsBrowser</li></ul>          |

#### [viewer](#viewer)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:viewer() -> Viewer` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the Viewer instance, whether it is in the primary or secondary window.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the Viewer</li></ul>          |

#### [windowsUI](#windowsui)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:windowsUI() -> axuielement` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Returns the UI containing the list of windows in the app.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>The axuielement, or nil if the application is not running.</li></ul>          |

### Methods

#### [unwatch](#unwatch)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:unwatch() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Stop watching for events that happen in the application for the specified ID.                                                                                         |
| **Parameters**                                       | <ul><li>* `id` 	- The ID object which was returned from the `watch(...)` function.</li></ul> |
| **Returns**                                          | <ul><li>* `true` if the ID was watching and has been removed.</li></ul>          |

#### [watch](#watch)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`cp.apple.finalcutpro:watch() -> string` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Watch for events that happen in the application.                                                                                         |
| **Parameters**                                       | <ul><li>* `events` - A table of functions with to watch. These may be:</li><li>	* `active()`		- Triggered when the application is the active application.</li><li>	* `inactive()`		- Triggered when the application is no longer the active application.</li><li>   `move()` 	 		- Triggered when the application window is moved.</li><li>	* `preferences()`	- Triggered when the application preferences are updated.</li></ul> |
| **Returns**                                          | <ul><li>* An ID which can be passed to `unwatch` to stop watching.</li></ul>          |
