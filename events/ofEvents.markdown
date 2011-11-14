
## ofDragInfo ##
Passed to the [ofBaseApp](../app/ofBaseApp.htm) in the [dragEvent](../app/ofBaseApp.htm#dragEvent) method.

### vector <string> files ### {#files}
All the files included in the drag events

### ofPoint position ### {#position}
The location in the app where the drag event terminated, i.e. where you dropped the file/s.

## ofKeyEventArgs ## {#ofKeyEventArgs}
Sent during [keyPressed](../app/ofBaseApp.htm#keyPressed) and [keyReleased](../app/ofBaseApp.htm#keyReleased) events.

## ofMouseEventArgs ## {#ofMouseEventArgs}
Sent to [ofBaseApp}(../app/ofBaseApp.htm) during [mousePressed](../app/ofBaseApp.htm#mousePressed) [mouseReleased](../app/ofBaseApp.htm#mouseReleased) and [mouseDrag](../app/ofBaseApp.htm#mouseDrag) notifications.

## ofTouchEventArgs ## {#ofTouchEventArgs}
These are sent to any any registered listeners when the device detects touches. Most commonly this is the ofBaseApp in the [touchDown](../app/ofBaseApp.htm#touchDown), [touchUp](../app/ofBaseApp.htm#touchUp), [touchUp](../app/ofBaseApp.htm#touchUp), [touchDoubleTap](../app/ofBaseApp.htm#touchDoubleTap), [touchCancelled](../app/ofBaseApp.htm#touchCancelled) method.

### int id ### {#id}
The id of the touch.

### int time ### {#time}
For taps or presses this is the time in seconds. Not currently used.

### float x ### {#x}
Application coordinate location of the event

### float y ### {#y}
Application coordinate location of the event

### int numTouches ### {#numTouches}
How many touch points the event involves. Not currently used.

### float width ### {#width}
The width of the touch area. Not currently used.

### float height ### {#height}
The height of the touch area.  Not currently used.

### float angle ### {#angle}
If there are two touches this is the angle between them.  Not currently used.

### float minoraxis ### {#minoraxis}
The shorter axis of a touch area.  Not currently used.

### float majoraxis ### {#majoraxis}
The longer axis of a touch area.  Not currently used.

### float pressure ### {#pressure}
If your device is recording pressure, this represents the pressure of the touch.  Not currently used.

### float xspeed ### {#xspeed}
For touch drag events, this is the approximation of the speed of the movement along the x-axis.  Not currently used.

### float yspeed ### {#yspeed}
For touch drag events, this is the approximation of the speed of the movement along the y-axis.  Not currently used.

### float xaccel ### {#xaccel}
For touch drag events, this is the approximation of the acceleration of the movement along the x-axis.  Not currently used.

### float yaccel ### {#yaccel}
For touch drag events, this is the approximation of the acceleration of the movement along the y-axis.  Not currently used.

## ofAudioEventArgs ## {#ofAudioEventArgs}

### float* buffer ### {#buffer}

### int bufferSize ### {#bufferSize}

### int nChannels ### {#nChannels}

## ofResizeEventArgs ## {#ofResizeEventArgs}

 ### int width  ### {#width}

 ### int height ### {#height}

## ofEvents ## {#ofEvents}
Below are the public methods of ofEvents

### void ofRegisterMouseEvents(ListenerClass * listener) ### {#ofRegisterMouseEvents}
Register the mouse events to the listener. This assumes that the listener has mousePressed, mouseReleased, mouseMoved, and mouseDragged methods to handle the events being dispatched to it.

### void ofRegisterKeyEvents(ListenerClass * listener) ### {#ofRegisterKeyEvents}
Register the mouse events to the listener. This assumes that the listener has keyPressed, keyReleased methods to handle the events being dispatched to it.

### void ofRegisterTouchEvents(ListenerClass * listener) ### {#ofRegisterTouchEvents}
Register the mouse events to the listener. This assumes that the listener has touchDown, touchMoved, touchUp, touchDoubleTap, touchCancelled methods to handle the events being dispatched to it.

### void ofRegisterGetMessages(ListenerClass * listener) ### {#ofRegisterGetMessages}
Register the mouse events to the listener. This assumes that the listener has a gotMessage method to handle the events being dispatched to it.

### void ofRegisterDragEvents(ListenerClass * listener) ### {#ofRegisterDragEvents}
Register the drag events to the listener. This assumes that the listener has the dragEvent method to handle the events being dispatched to it.

### void ofUnregisterMouseEvents(ListenerClass * listener) ### {#ofUnregisterMouseEvents}
Stop the listener from listening to mouse events.

### void ofUnregisterKeyEvents(ListenerClass * listener) ### {#ofUnregisterKeyEvents}
Stop the listener from listening to key events.

### void ofUnregisterTouchEvents(ListenerClass * listener) ### {#ofUnregisterTouchEvents}
Stop the listener from listening to touch events.

### void ofUnregisterGetMessages(ListenerClass * listener) ### {#ofUnregisterGetMessages}
Stop the listener from listening to message events.

### void ofUnregisterDragEvents(ListenerClass * listener) ### {#ofUnregisterDragEvents}
Stop the listener from listening to drag events.
