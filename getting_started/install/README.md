# Installation and Setup

## Building CommandPost

CommandPost is made up of two seperate components:

* [CommandPost-App](https://github.com/CommandPost/CommandPost-App) contains the [Hammerspoon](http://www.hammerspoon.org) fork which makes up the main application.
* [CommandPost](https://github.com/CommandPost/CommandPost) contains all the [Lua](https://www.lua.org/about.html) scripts that drive the interface and feature set.

To build your own version of CommandPost, you need to download both these repositories from here:

* [CommandPost](https://github.com/CommandPost/CommandPost)
* [CommandPost-App](https://github.com/CommandPost/CommandPost-App)

Once downloaded, these two repositories should be contained in the same folder, because when you build CommandPost-App, it will copy the Lua Scripts from the CommandPost folder.

To build CommandPost-App:

* Create a self-signed Code Signing certificate named **Internal Code Signing** as explained [here](http://bd808.com/blog/2013/10/21/creating-a-self-signed-code-certificate-for-xcode/) - however, please make sure you label the certificate "Internal Code Signing" and not "Self-signed Applications".
* Open a Terminal window.
* Navigate to the CommandPost-App project root directory.
* Install `pip` by following [these instructions](https://packaging.python.org/installing/#install-pip-setuptools-and-wheel).
* Execute `pip install -r requirements.txt`
* Navigate to the CommandPost project root directory.
* Execute `./scripts/build_commandpost_testing.sh`
* Once complete, navigate to the CommandPost-App project root directory, and the application should be contained within the `build` folder.

---

## Developing CommandPost

By default CommandPost-App will look for the CommandPost Lua scripts inside it's application bundle (i.e. `CommandPost.app/Contents/Resources/extensions/`), however, if something with the same name exists in `~/Library/Application Support/CommandPost/Extensions/` it will use those files instead.

To speed up development, you can tell CommandPost-App to look for the CommandPost Lua scripts in another location, such as your CommandPost folder (as downloaded from GitHub). This means that you can modify the Lua files within the CommandPost folder whilst CommandPost-App is running, and each time you "save" a file, CommandPost will reload, so that you can test things out instantly.

To tell CommandPost-App to use your development folder:

* Navigate to the CommandPost project root directory.
* Execute `./scripts/load_lua_scripts_from_developer_source.sh`

If you want to undo this process, you can:

* Navigate to the CommandPost project root directory.
* Execute `./scripts/load_lua_scripts_from_app_bundle.sh`

---

## Building Documentation

To build the documentation you see in this Developers Guide:

* Navigate to the CommandPost project root directory.
* Execute `./scripts/build_commandpost_docs.sh`

---

## Trashing CommandPost Preferences

The CommandPost preferences are located at: `~/Library/Preferences/org.latenitefilms.CommandPost.plist`

To trash this file:

* Navigate to the CommandPost project root directory.
* Execute `./scripts/trash_commandpost_preferences.sh`