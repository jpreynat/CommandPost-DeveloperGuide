# Hammerspoon docs: hs.network.configuration

This sub-module provides access to the current location set configuration settings in the system's dynamic store.

## API Overview
* Constructors - API calls which return an object, typically one that offers API methods</li>
  * open
* Methods - API calls which can only be made on an object returned by a constructor</li>
  * computerName
  * consoleUser
  * contents
  * dhcpInfo
  * hostname
  * keys
  * location
  * locations
  * monitorKeys
  * proxies
  * setCallback
  * setLocation
  * start
  * stop

## API Documentation

### Constructors

#### open
  * Signature: hs.network.configuration.open() -> storeObject
  * Type: Constructor
  * Description: Opens a session to the dynamic store maintained by the System Configuration server.
  * Parameters:
     * None
  * Returns:
     * the storeObject

### Methods

#### computerName
  * Signature: hs.network.configuration:computerName() -> name, encoding
  * Type: Method
  * Description: Returns the name of the computeras specified in the Sharing Preferences, and its string encoding
  * Parameters:
     * None
  * Returns:
     * name     - the computer name
     * encoding - the encoding type
  * Notes:
     * You can also retrieve this information as key-value pairs with `hs.network.configuration:contents("Setup:/System")`

#### consoleUser
  * Signature: hs.network.configuration:consoleUser() -> name, uid, gid
  * Type: Method
  * Description: Returns the name of the user currently logged into the system, including the users id and primary group id
  * Parameters:
     * None
  * Returns:
     * name - the user name
     * uid  - the user ID for the user
     * gid  - the user's primary group ID
  * Notes:
     * You can also retrieve this information as key-value pairs with `hs.network.configuration:contents("State:/Users/ConsoleUser")`

#### contents
  * Signature: hs.network.configuration:contents([keys], [pattern]) -> table
  * Type: Method
  * Description: Return the contents of the store for the specified keys or keys matching the specified pattern(s)
  * Parameters:
     * keys    - a string or table of strings containing the keys or patterns of keys, if `pattern` is true.  Defaults to all keys.
     * pattern - a boolean indicating wether or not the string(s) provided are to be considered regular expression patterns (true) or literal strings to match (false).  Defaults to false.
  * Returns:
     * a table of key-value pairs from the dynamic store which match the specified keys or key patterns.
  * Notes:
     * if no parameters are provided, then all key-value pairs in the dynamic store are returned.

#### dhcpInfo
  * Signature: hs.network.configuration:dhcpInfo([serviceID]) -> table
  * Type: Method
  * Description: Return the DHCP information for the specified service or the primary service if no parameter is specified.
  * Parameters:
     * serviceID - an optional string contining the service ID of the interface for which to return DHCP info.  If this parameter is not provided, then the default (primary) service is queried.
  * Returns:
     * a table containing DHCP information including lease time and DHCP options
  * Notes:
     * a list of possible Service ID's can be retrieved with `hs.network.configuration:contents("Setup:/Network/Global/IPv4")`
     * generates an error if the service ID is invalid or was not assigned an IP address via DHCP.

#### hostname
  * Signature: hs.network.configuration:hostname() -> name
  * Type: Method
  * Description: Returns the current local host name for the computer
  * Parameters:
     * None
  * Returns:
     * name - the local host name
  * Notes:
     * You can also retrieve this information as key-value pairs with `hs.network.configuration:contents("Setup:/System")`

#### keys
  * Signature: hs.network.configuration:keys([keypattern]) -> table
  * Type: Method
  * Description: Return the keys in the dynamic store which match the specified pattern
  * Parameters:
     * keypattern - a regular expression specifying which keys to return (defaults to ".*", or all keys)
  * Returns:
     * a table of keys from the dynamic store.

#### location
  * Signature: hs.network.configuration:location() -> location
  * Type: Method
  * Description: Returns the current location identifier
  * Parameters:
     * None
  * Returns:
     * location - the UUID for the currently active network location
  * Notes:
     * You can also retrieve this information as key-value pairs with `hs.network.configuration:contents("Setup:")`
     * If you have different locations defined in the Network preferences panel, this can be used to determine the currently active location.

#### locations
  * Signature: hs.network.configuration:locations() -> table
  * Type: Method
  * Description: Returns all configured locations
  * Parameters:
     * None
  * Returns:
     * a table of key-value pairs mapping location UUIDs to their names

#### monitorKeys
  * Signature: hs.network.configuration:monitorKeys([keys], [pattern]) -> storeObject
  * Type: Method
  * Description: Specify the key(s) or key pattern(s) to monitor for changes.
  * Parameters:
     * keys    - a string or table of strings containing the keys or patterns of keys, if `pattern` is true.  Defaults to all keys.
     * pattern - a boolean indicating wether or not the string(s) provided are to be considered regular expression patterns (true) or literal strings to match (false).  Defaults to false.
  * Returns:
     * the store Object
  * Notes:
     * if no parameters are provided, then all key-value pairs in the dynamic store are monitored for changes.

#### proxies
  * Signature: hs.network.configuration:proxies() -> table
  * Type: Method
  * Description: Returns information about the currently active proxies, if any
  * Parameters:
     * None
  * Returns:
     * a table of key-value pairs describing the current proxies in effect, both globally, and scoped to specific interfaces.
  * Notes:
     * You can also retrieve this information as key-value pairs with `hs.network.configuration:contents("State:/Network/Global/Proxies")`

#### setCallback
  * Signature: hs.network.configuration:setCallback(function | nil) -> storeObject
  * Type: Method
  * Description: Set or remove the callback function for a store object
  * Parameters:
     * a function or nil to set or remove the store object callback function
  * Returns:
     * the store object
  * Notes:
     * The callback function will be invoked each time a monitored key changes value and the callback function should accept two parameters: the storeObject itself, and an array of the keys which contain values that have changed.
     * This method just sets the callback function.  You specify which keys to watch with [hs.network.configuration:monitorKeys](#monitorKeys) and start or stop the watcher with [hs.network.configuration:start](#start) or [hs.network.configuartion:stop](#stop)

#### setLocation
  * Signature: hs.network.configuration:setLocation(location) -> boolean
  * Type: Method
  * Description: Switches to a new location
  * Parameters:
     * location - string containing UUID or name of new location
  * Returns:
     * bool

#### start
  * Signature: hs.network.configuration:start() -> storeObject
  * Type: Method
  * Description: Starts watching the store object for changes to the monitored keys and invokes the callback function (if any) when a change occurs.
  * Parameters:
     * None
  * Returns:
     * the store object
  * Notes:
     * The callback function should be specified with [hs.network.configuration:setCallback](#setCallback) and the keys to monitor should be specified with [hs.network.configuration:monitorKeys](#monitorKeys).

#### stop
  * Signature: hs.network.configuration:stop() -> storeObject
  * Type: Method
  * Description: Stops watching the store object for changes.
  * Parameters:
     * None
  * Returns:
     * the store object