# Hammerspoon docs: hs.uielement.watcher

Watch for events on certain UI elements (including windows and applications)

You can watch the following events:
### Application-level events
See hs.application.watcher for more events you can watch.
* hs.uielement.watcher.applicationActivated: The current application switched to this one.
* hs.uielement.watcher.applicationDeactivated: The current application is no longer this one.
* hs.uielement.watcher.applicationHidden: The application was hidden.
* hs.uielement.watcher.applicationShown: The application was shown.

#### Focus change events
These events are watched on the application level, but send the relevant child element to the handler.
* hs.uielement.watcher.mainWindowChanged: The main window of the application was changed.
* hs.uielement.watcher.focusedWindowChanged: The focused window of the application was changed. Note that the application may not be activated itself.
* hs.uielement.watcher.focusedElementChanged: The focused UI element of the application was changed.

### Window-level events
* hs.uielement.watcher.windowCreated: A window was created. You should watch for this event on the application, or the parent window.
* hs.uielement.watcher.windowMoved: The window was moved.
* hs.uielement.watcher.windowResized: The window was resized.
* hs.uielement.watcher.windowMinimized: The window was minimized.
* hs.uielement.watcher.windowUnminimized: The window was unminimized.

### Element-level events
These work on all UI elements, including windows.
* hs.uielement.watcher.elementDestroyed: The element was destroyed.
* hs.uielement.watcher.titleChanged: The element's title was changed.

## API Overview
* Methods - API calls which can only be made on an object returned by a constructor</li>
  * element
  * start
  * stop

## API Documentation

### Methods

#### element
  * Signature: hs.uielement.watcher:element() -> object
  * Type: Method
  * Description: Returns the element the watcher is watching.
  * Parameters:
     * None
  * Returns:
     * The element the watcher is watching.

#### start
  * Signature: hs.uielement.watcher:start(events) -> hs.uielement.watcher
  * Type: Method
  * Description: Tells the watcher to start watching for the given list of events.
  * Parameters:
     * An array of events to be watched for.
  * Returns:
     * hs.uielement.watcher
  * Notes:
     * See hs.uielement.watcher for a list of events. You may also specify arbitrary event names as strings.
     * Does nothing if the watcher has already been started. To start with different events, stop it first.

#### stop
  * Signature: hs.uielement.watcher:stop() -> hs.uielement.watcher
  * Type: Method
  * Description: Tells the watcher to stop listening for events.
  * Parameters:
     * None
  * Returns:
     * hs.uielement.watcher
  * Notes:
     * This is automatically called if the element is destroyed.