
## ofVideoGrabber ##


The ofVideoGrabber class wraps quicktime's sequence grabbing component to provide low level access to live cameras. On windows it now uses the directshow based videoInput library which offers mainy performance advantages over quicktime and does not require quicktime or WinVDig to be installed. A #define in ofConstants.h allows you to choose whether to use quicktime or directshow (default) for windows.

In linux it uses by default unicap, although you can change to v4l through a #define in [ofConstants](../utils/ofConstants.htm) in case some v4l device doesn't work properly with unicap.

### listDevices() ###

Prints to the console a list of available capture devices with the device ID of each device. The device ID can then be used with setDeviceID() to specify a specific device to capture from.	

### isFrameNew() ### 

Returns true, if the current pixels have changed since the last time isFrameNew() was called. 	

### grabFrame() ### 

This function should be called regularly (for example, once per update) if you'd like to get new data from the sequence grabber. It will idle the video grabbing component so that you get new data.	

### close() ### 

Closes the sequence grabber and de-allocates any allocated resources. 	
	

### initGrabber(int w, int h, bool bTexture) ### 

Initializes either the default capture device or the capture device specified by setDeviceID. Attempts to setup capture at the width and height specified. If the capture dimensions are not available it will setup capture for the next closest dimensions available. It is good to check what the actual size is before you start processing the pixels.

```
myGrabber.setVerbose(true);
myGrabber.setDeviceID(1);
myGrabber.initGrabber(320,240,false);
int grabW = myGrabber.width;
int grabH = myGrabber.height;
cout << "asked for 320 by 240 - actual size is " << grabW << " " << grabH << endl;
```

bTexture variable tells ofVideoGrabber that it should setup a texture so you can display the video on the screen.		
	
### videoSettings() ### 

Loads the video settings on screen. If your opengl application is full screen, this window might appear underneath the main window the first time you call this.	


### getPixels()	### 

Returns the pointer to the array of pixels that represents the current frame of live video. the data is stored as RGB, and in an array which is the size: width*height*3.	


### getTextureReference() ### 
	
Returns the [ofTexture](../gl/ofTexture.htm) object that our videoGrabber class is using.	
	
	
### setDeviceID(int _deviceID) ### 
	
Choose to capture from a specific capture device specified by _deviceID. Use listDevices() to see a list of available capture devices and their device IDs.		

### setUseTexture(bool bUse) ### 

Set the usage of texture inside this object. Typically, you will want to draw the movie grabber on screen, and so it will be necessary to use a texture, but there may be cases where it helps to not use a texture in order to save memory or for better performance. To disable the internal use of the texture, you can initialize the sequence grabber like this:

```
myGrabber.setUseTexture(false);
myGrabber.initGrabber(320,240);
```
	
### draw(float x, float y, float w, float h) ### 

Draws the internal texture of the movie grabber class at the position (x,y) with the given width (w) and height (h). 	
	
### draw(float x, float y)	### 
	
Draws the internal texture of the movie grabber class at the position (x,y) with the internal width and height of the movie grabber.	

### update() ###

Calls grabframe function.	
	

### getHeight() ### 

Returns the height of the video grabber.	

### getWidth() ### 

Returns the width of the video grabber.	
	
### height ### 

Variable containing the height of the video grabber.	
	
### width ### 

Variable containing the width of the video grabber.	
