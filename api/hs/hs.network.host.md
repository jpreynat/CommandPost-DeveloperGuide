# [docs](index.md) » hs.network.host
---

This sub-module provides functions for acquiring host information, such as hostnames, addresses, and reachability.

## API Overview
* Functions - API calls offered directly by the extension
 * [addressesForHostname](#addressesforhostname)
 * [hostnamesForAddress](#hostnamesforaddress)
 * [reachabilityForAddress](#reachabilityforaddress)
 * [reachabilityForHostname](#reachabilityforhostname)
* Methods - API calls which can only be made on an object returned by a constructor
 * [cancel](#cancel)
 * [isRunning](#isrunning)

## API Documentation

### Functions

#### [addressesForHostname](#addressesforhostname)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.network.host.addressesForHostname(name[, fn]) -> table | hostObject` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Get IP addresses for the hostname specified.                                                                                         |
| **Parameters**                                       | <ul><li>name - the hostname to lookup IP addresses for</li><li>fn   - an optional callback function which, when provided, will perform the address resolution in an asynchronous, non-blocking manner.</li></ul> |
| **Returns**                                          | <ul><li>If this function is called without a callback function, returns a table containing the IP addresses for the specified name.  If a callback function is specified, then a host object is returned.</li></ul>          |
| **Notes**                                            | <ul><li>If no callback function is provided, the resolution occurs in a blocking manner which may be noticeable when network access is slow or erratic.</li><li>If a callback function is provided, this function acts as a constructor, returning a host object and the callback function will be invoked when resolution is complete.  The callback function should take two parameters: the string "addresses", indicating that an address resolution occurred, and a table containing the IP addresses identified.</li><li>Generates an error if network access is currently disabled or the hostname is invalid.</li></ul>                |

#### [hostnamesForAddress](#hostnamesforaddress)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.network.host.hostnamesForAddress(address[, fn]) -> table | hostObject` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Get hostnames for the IP address specified.                                                                                         |
| **Parameters**                                       | <ul><li>address - a string or number representing an IPv4 or IPv6 network address to lookup hostnames for.  If the argument is a number, it is treated as the 32 bit numerical representation of an IPv4 address.</li><li>fn      - an optional callback function which, when provided, will perform the hostname resolution in an asynchronous, non-blocking manner.</li></ul> |
| **Returns**                                          | <ul><li>If this function is called without a callback function, returns a table containing the hostnames for the specified address.  If a callback function is specified, then a host object is returned.</li></ul>          |
| **Notes**                                            | <ul><li>If no callback function is provided, the resolution occurs in a blocking manner which may be noticeable when network access is slow or erratic.</li><li>If a callback function is provided, this function acts as a constructor, returning a host object and the callback function will be invoked when resolution is complete.  The callback function should take two parameters: the string "names", indicating that hostname resolution occurred, and a table containing the hostnames identified.</li><li>Generates an error if network access is currently disabled or the IP address is invalid.</li></ul>                |

#### [reachabilityForAddress](#reachabilityforaddress)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.network.host.reachabilityForAddress(address[, fn]) -> integer | hostObject` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Get the reachability status for the IP address specified.                                                                                         |
| **Parameters**                                       | <ul><li>address - a string or number representing an IPv4 or IPv6 network address to check the reachability for.  If the argument is a number, it is treated as the 32 bit numerical representation of an IPv4 address.</li><li>fn      - an optional callback function which, when provided, will determine the address reachability in an asynchronous, non-blocking manner.</li></ul> |
| **Returns**                                          | <ul><li>If this function is called without a callback function, returns the numeric representation of the address reachability status.  If a callback function is specified, then a host object is returned.</li></ul>          |
| **Notes**                                            | <ul><li>If no callback function is provided, the resolution occurs in a blocking manner which may be noticeable when network access is slow or erratic.</li><li>If a callback function is provided, this function acts as a constructor, returning a host object and the callback function will be invoked when resolution is complete.  The callback function should take two parameters: the string "reachability", indicating that reachability was determined, and the numeric representation of the address reachability status.</li><li>Generates an error if network access is currently disabled or the IP address is invalid.</li><li>The numeric representation is made up from a combination of the flags defined in `hs.network.reachability.flags`.</li><li>Performs the same reachability test as `hs.network.reachability.forAddress`.</li></ul>                |

#### [reachabilityForHostname](#reachabilityforhostname)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.network.host.reachabilityForHostname(name[, fn]) -> integer | hostObject` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Function                                                                                         |
| **Description**                                      | Get the reachability status for the IP address specified.                                                                                         |
| **Parameters**                                       | <ul><li>name - the hostname to check the reachability for.  If the argument is a number, it is treated as the 32 bit numerical representation of an IPv4 address.</li><li>fn   - an optional callback function which, when provided, will determine the address reachability in an asynchronous, non-blocking manner.</li></ul> |
| **Returns**                                          | <ul><li>If this function is called without a callback function, returns the numeric representation of the hostname reachability status.  If a callback function is specified, then a host object is returned.</li></ul>          |
| **Notes**                                            | <ul><li>If no callback function is provided, the resolution occurs in a blocking manner which may be noticeable when network access is slow or erratic.</li><li>If a callback function is provided, this function acts as a constructor, returning a host object and the callback function will be invoked when resolution is complete.  The callback function should take two parameters: the string "reachability", indicating that reachability was determined, and the numeric representation of the hostname reachability status.</li><li>Generates an error if network access is currently disabled or the IP address is invalid.</li><li>The numeric representation is made up from a combination of the flags defined in `hs.network.reachability.flags`.</li><li>Performs the same reachability test as `hs.network.reachability.forHostName`.</li></ul>                |

### Methods

#### [cancel](#cancel)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.network.host:cancel() -> hostObject` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Cancels an in-progress asynchronous host resolution.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>the hostObject</li></ul>          |
| **Notes**                                            | <ul><li>This method has no effect if the resolution has already completed.</li></ul>                |

#### [isRunning](#isrunning)
| <span style="float: left;">**Signature**</span> | <span style="float: left;">`hs.network.host:isRunning() -> boolean` </span>                                                          |
| -----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Type**                                             | Method                                                                                         |
| **Description**                                      | Returns whether or not resolution is still in progress for an asynchronous query.                                                                                         |
| **Parameters**                                       | <ul><li>None</li></ul> |
| **Returns**                                          | <ul><li>true, if resolution is still in progress, or false if resolution has already completed.</li></ul>          |

