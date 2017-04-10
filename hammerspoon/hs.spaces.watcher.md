# Hammerspoon docs: hs.spaces.watcher

Watches for the current Space being changed
NOTE: This extension determines the number of a Space, using OS X APIs that have been deprecated since 10.8 and will likely be removed in a future release. You should not depend on Space numbers being around forever!

## API Overview
* Constructors - API calls which return an object, typically one that offers API methods</li>
  * new
* Methods - API calls which can only be made on an object returned by a constructor</li>
  * start
  * stop

## API Documentation

### Constructors

#### new
  * Signature: hs.spaces.watcher.new(handler) -> watcher
  * Type: Constructor
  * Description: Creates a new watcher for Space change events
  * Parameters:
     * handler - A function to be called when the active Space changes. It should accept one argument, which will be the number of the new Space (or -1 if the number cannot be determined)
  * Returns:
     * An `hs.spaces.watcher` object

### Methods

#### start
  * Signature: hs.spaces.watcher:start()
  * Type: Method
  * Description: Starts the Spaces watcher
  * Parameters:
     * None
  * Returns:
     * The watcher object

#### stop
  * Signature: hs.spaces.watcher:stop()
  * Type: Method
  * Description: Stops the Spaces watcher
  * Parameters:
     * None
  * Returns:
     * The watcher object