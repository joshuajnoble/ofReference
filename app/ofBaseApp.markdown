
###  setup() ## {#setup}
This function gets called once, at the start of the app. It's where you allocate variables, initialize camera communication, load data, begin communication with a local or remoate service, and generally prepare your application.

### void update() ###  {#update}
This function gets called repeatedly, each frame. It gets just before draw, so it is an ideal place to do any updating of variables, checking files or peripherals, or any other preparation for drawing.

### void draw() ### 	{#draw}
This function gets called regularly just after update. It's where you draw things.

### void exit() ###  {#exit}
Add this function to your testApp to have it called at the moment before the app is terminated. This is useful for doing cleanup stuff or making sure files are saved before the app terminates. This happens before the destructor of the app instance is called.

### void windowResized(int w, int h) ###  {#windowResized}
This function gets called when ever we resize the application window. You receive the new width (w) and the new height (h) of the window.

### void keyPressed( int key ) ###  {#keyPressed}
This function gets called when a key is pressed. The value key can be tested against.

There are more complicated character codes, for keys such as F1-F12, Down, Enter: OF_KEY_BACKSPACE, OF_KEY_RETURN, OF_KEY_PRINTSCR, OF_KEY_F1 - OF_KEY_F12, OF_KEY_LEFT, OF_KEY_UP, OF_KEY_RIGHT, OF_KEY_DOWN, OF_KEY_PAGE_UP, OF_KEY_PAGE_DOWN, OF_KEY_HOME, OF_KEY_END, OF_KEY_INSERT 


### void keyReleased( int key ) ###  {#keyReleased}
This function gets called when a key is released. The value key can be tested against.

There are more complicated character codes, for keys such as F1-F12, Down, Enter: OF_KEY_BACKSPACE, OF_KEY_RETURN, OF_KEY_PRINTSCR, OF_KEY_F1 - OF_KEY_F12, OF_KEY_LEFT, OF_KEY_UP, OF_KEY_RIGHT, OF_KEY_DOWN, OF_KEY_PAGE_UP, OF_KEY_PAGE_DOWN, OF_KEY_HOME, OF_KEY_END, OF_KEY_INSERT

### void mouseMoved( int x, int y ) ###  {#mouseMoved}
This function gets when ever the mouse moves. You receive the x and y corrdinates of the mouse.

### void mouseDragged( int x, int y, int button ) ###  {#mouseDragged}
This function gets when ever the mouse is dragged. You receive the x and y corrdinates of the mouse.

### void mousePressed( int x, int y, int button ) ###  {#mousePressed}
This function gets when ever the mouse pressed. You receive the x and y corrdinates of the mouse and the button that is pressed

### void mouseReleased() ###  {#mouseReleased}
This function gets when ever the mouse moves.

### void mouseReleased(int x, int y, int button ) ###  {#mouseReleased}
This function gets when ever the mouse moves. You receive the x and y corrdinates of the mouse and the button that was released.
	
### void dragEvent(ofDragInfo dragInfo) ###  {#dragEvent}
Sends an [ofDragInfo](../events/ofEvents.htm#ofDragInfo) event.

### void gotMessage(ofMessage msg) ###  {#gotMessage}
