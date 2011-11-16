

## ofVideoPlayer

The ofVideoPlayer class loads in a movie file via quicktime in windows and mac
or gstreamer in linux, and offers various controls to play the movie, control
the properties of the movie, and to access the pixels of a given frame.

  
Example:
```cpp

    
    ofVideoPlayer myPlayer;

### ofVideoPlayer Functions

bool loadMovie(...)

Returns true if the video is loaded successfully and false if not
Load a movie file (fileName) into that object. It will look for the movie file
inside of the data/ folder. The movie does not automatically play once loaded.

  
Example:
```cpp
    ofVideoPlayer myPlayer;  
    
    myPlayer.loadMovie('myMovie.mov');
```

void closeMovie()

Closes the movie file and de-allocates resources.

  
  
Example:
```cpp

    
    ofVideoPlayer myPlayer;  
    
    myPlayer.loadMovie("myMovie.mov"); //Loads video resources  
    
    myPlayer.closeMovie(); //Unloads video resources
```


### void close()

Calls the closeMovie() function, which closes the movie file and de-allocates
resources.



### void update()

Calls the idleMovie() function. This function idles the movie player, so that
the movie can play. If you don't call it, when the movie is playing then you
may encounter problems, especially on windows machines.
This function idles the movie player, so that the movie can play. If you don't
call it, when the movie is playing then you may encouter problems, especially
on winodws machines.


### void play()

Plays the movie. If the movie has been stopped or paused it will the continue
playback at the point it was stopped.

### void stop()

Stops the movie.

### bool isFrameNew()

Returns true if the frame of pixels is "new".
For example, if the pixels are new, you could then process them.
      
```cpp    
    if (myMovie.isFrameNew()){  
    
    	;	// do something  
    
    }  
```
    
### unsigned char* getPixels()

Returns a pointer to the array of pixels that are RGB (width*height*3).
For example, to get the red green and blue of the pixel (100,20):

```cpp  
unsigned char * pixels = myMovie.getPixels();

int widthOfLine = myMovie.width * w; // how long is a line of pixels

int red = pixels[(20 * widthOfLine) + 100 * 3 ];

int green = pixels[(20 * widthOfLine) + 100 * 3 + 1];

int blue = pixels[(20 * widthOfLine) + 100 * 3 + 2];
```

### float getPosition()

Returns the current playhead position, between 0 (start of movie) and 1 (end
of movie).

### float getSpeed()

Returns the current speed of the movie.
note: 1 = normal speed, 0 = paused, -1 = backwards.

### float getDuration()

Returns the duration, in seconds, of the movie.

### bool getIsMovieDone()

Returns a boolean with the current status of the movie (returns true if
finished, or false if still playing).

### void setPosition(float pct)

Sets the position of the playhead to a given percentage through the movie. Can
be used to scrub through a movie.

### void setVolume(int volume)

Sets the volume of a movie - default = 0, silent

### void setLoopState(int state)

Sets the looping state of the movie. Deafult behavior is to loop. There are
three options:      
    
    OF_LOOP_NONE - don't loop, the movie will stop when it gets to the last frame (or first frame, if playing backwards)  
    
    OF_LOOP_NORMAL - loop normally (the last frame loops to the first frame)  
    
    OF_LOOP_PALINDROME - loop back and forth  


### void setSpeed(float speed)

Sets the speed of the movie that is playing. 1 = normal, 2 = 2x as fast, 0 =
stopped, -1 = backwards, etc;


### void setFrame(int frame)

Sets the current frame of the video. Should be used only if you know the
bounds of the movie ( using totalNumberFrames() ) or store a location using
getCurrentFrame();


### void setUseTexture(bool bUse)

Set the usage of texture inside this object. Typically, you will want to draw
the movie on screen, and so it will be necessary to use a texture, but there
may be cases where it helps to not use a texture in order to save memory or
for better performance. To disable the internal use of the texture, you can
load the movie like this:

```cpp
    myMovie.setUseTexture(false);  
    
    myMovie.loadMovie("blah.mov");  
```
    

### ofTexture& getTextureReference()

Returns a reference to the videoPlayer's texture.

### void draw(float x, float y, float w, float h)

Draws the texture of the movie player class at the position (x,y) with the
given width (w) and height (h).


### void draw(float x, float y)

Draws the texture of the movie player class as the position (x,y) with the
internal width and height of the loaded movie.



### void setAnchorPercent(float xPct, float yPct)

Set the anchor point that the texture will be drawn when it is drawn in percentages, 0 - 100

### void setAnchorPoint(int x, int y)

Set the anchor point that the texture will be drawn when it is drawn in pixels

### void resetAnchor()

### void setPaused(bool bPause)

Pause or unpause the video

### int getCurrentFrame()

Returns the current frame of the video.

### int getTotalNumFrames()

Returns the total number of frames for the loaded movie.


### void firstFrame()

Moves the playhead to the first frame of the movie. This can also be
accomplished using setCurrentFrame(0).


### void nextFrame()

Advances the playhead by one frame.


### void previousFrame()

Reverses the playhead by one frame.

### float getHeight()

Returns the height of the loaded movie.

### float getWidth()

Returns the width of the loaded movie.

### int width

Variable containing the width of the video.

### int height

Variable containing the height of the video.


### float speed

Contains the playback speed of the video. 1.0 is the normal speed. 2.0 is
double the normal speed, -1 is backwards etc.

### bool bLoaded

A boolean that describes if the movie loaded properly.

### int nFrames

Variable containing the number of frames of the video.


### unsigned char * pixels

Array of pixels that represents the current frame of live video. The data is
stored as RGB in an array which is the size: width*height*3.

### bool bHavePixelsChanged

A boolean controlling if pixels have change.



### ofTexture& tex

ofTexture used by the video player class.


### bool bUseTexture

bUseTexture enables and disables the use of ofTexture in our video player.



### bool allocated

Boolean varible containing true if the texture has been already allocated
inside our video player.



