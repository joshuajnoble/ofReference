

##  ofBaseDraws ##
public:
### virtual  ~ofBaseDraws() ###
### virtual  void draw(float x,float y) ###
### virtual  void draw(float x,float y,float w, float h) ###

### virtual  void draw(const ofPoint & point)
	draw( point.x, point.y)

### virtual  void draw(const ofRectangle & rect)
	draw(rect.x, rect.y, rect.width, rect.height) ### 

### virtual  float getHeight() ###
### virtual  float getWidth() ###

### virtual  void setAnchorPercent(float xPct, float yPct) ###
### virtual  void setAnchorPoint(float x, float y) ###
### virtual  void resetAnchor() ###

##  ofBaseUpdates ##

### ### virtual  ~ofBaseUpdates() ### 
### ### virtual  void update() ### 

##  ofBaseHasTexture ##

### virtual  ~ofBaseHasTexture() ###
### virtual  ofTexture & getTextureReference() ###
### virtual  void setUseTexture(bool bUseTex) ###


##  ofAbstractHasPixels ##
### virtual  ~ofAbstractHasPixels() ###

##  ofBaseHasPixels_

Extends ofAbstractHasPixels
template<typename T>

### virtual  ~ofBaseHasPixels_<T>() ###
### virtual  T * getPixels() ###
### virtual  ofPixels_<T> & getPixelsRef() ###

typedef ofBaseHasPixels_<unsigned char> ofBaseHasPixels ###
typedef ofBaseHasPixels_<float> ofBaseHasFloatPixels ###

##  ofAbstractImage ##

public ofBaseDraws, public ofBaseHasTexture

### virtual  ~ofAbstractImage() ###


##  ofBaseImage_ ## 

Extends public ofAbstractImage, public ofBaseHasPixels_<T>.

template<typename T>

### virtual  ~ofBaseImage_<T>() ###

## typedef ofBaseImage_<unsigned char> ofBaseImage ##

## typedef ofBaseImage_<float> ofBaseFloatImage ##

##  ofBaseSoundInput ##

    ### virtual  ~ofBaseSoundInput()  ###

	### virtual  void audioIn( float * input, int bufferSize, int nChannels, int deviceID, long unsigned long tickCount ) ###
		audioIn(input, bufferSize, nChannels) ###

	### virtual  void audioIn( float * input, int bufferSize, int nChannels ) ###
		audioReceived(input, bufferSize, nChannels) ###

	### virtual  void audioReceived( float * input, int bufferSize, int nChannels ) ###

##  ofBaseSoundOutput ##

    ### virtual  ~ofBaseSoundOutput()  ###

	### virtual  void audioOut( float * output, int bufferSize, int nChannels, int deviceID, long unsigned long tickCount  )
		audioOut(output, bufferSize, nChannels) ###

	### virtual  void audioOut( float * output, int bufferSize, int nChannels )
		audioRequested(output, bufferSize, nChannels) ###

	### virtual  void audioRequested( float * output, int bufferSize, int nChannels ) ###
	//legacy

##  ofBaseVideo ##
public ofBaseHasPixels, public ofBaseUpdates

### virtual  ~ofBaseVideo() ###
### virtual  bool isFrameNew()  ###
### virtual  void close() ###


##  ofBaseVideoDraws ##

public ofBaseVideo, public ofBaseDraws, public ofBaseHasTexture

### virtual  ~ofBaseVideoDraws() ###


##  ofBaseVideoGrabber ## 

virtual public ofBaseVideo

### virtual  ~ofBaseVideoGrabber() ###

### virtual  void	listDevices() ###
needs implementing

### virtual  bool	initGrabber(int w, int h) ###
### virtual  void	update() ###
### virtual  bool	isFrameNew() ###

### virtual  unsigned char * getPixels() ###

### virtual  void	close() ###	

### virtual  float	getHeight() ###
### virtual  float	getWidth() ###

//should implement!
### virtual  void setVerbose(bool bTalkToMe) ###
### virtual  void setDeviceID(int _deviceID) ###
### virtual  void setDesiredFrameRate(int framerate) ###
### virtual  void videoSettings() ###
### virtual  void setPixelFormat(ofPixelFormat pixelFormat) ###
### virtual  ofPixelFormat getPixelFormat() ###

} ###


//----------------------------------------------------------
// ofBaseVideoPlayer
//----------------------------------------------------------
##  ofBaseVideoPlayer: ### virtual  public ofBaseVideo{

public:
### virtual  ~ofBaseVideoPlayer() ###

//needs implementing
### virtual  boolloadMovie(string name) ###
### virtual  voidclose() ###
### virtual  voidupdate() ###

### virtual  voidplay() ###
### virtual  voidstop() ###		

### virtual  bool isFrameNew() ###
### virtual  unsigned char * 	getPixels() ###
### virtual  ofTexture *			getTexture(){return NULL ###} ### 
If your videoplayer needs to implement seperate texture and pixel returns for performance, implement this function to return a texture instead of a pixel array. see iPhoneVideoGrabber for reference

### virtual  float getWidth() ###
### virtual  float getHeight() ###

### virtual  bool isPaused() ###
### virtual  bool isLoaded() ###
### virtual  bool isPlaying() ###

### virtual  float getPosition() ###
### virtual  float getSpeed() ###
### virtual  float getDuration() ###
### virtual  bool getIsMovieDone() ###

### virtual  void setPaused(bool bPause) ###
### virtual  void setPosition(float pct) ###
### virtual  void setVolume(int volume) ###
### virtual  void setLoopState(ofLoopType state) ###
### virtual  void setSpeed(float speed) ###
### virtual  void setFrame(int frame) ###  // frame 0 = first frame...

### virtual  int getCurrentFrame() ###
### virtual  int getTotalNumFrames() ###
### virtual  int getLoopState() ###

### virtual  void firstFrame() ###
### virtual  void nextFrame() ###
### virtual  void previousFrame() ###
### virtual  void setPixelFormat(ofPixelFormat pixelFormat) ###

##  ofBaseRenderer{

### virtual  ~ofBaseRenderer() ###

### virtual  string getType() ###

### virtual  void update() ###

### virtual  void draw(ofPolyline & poly) ###
### virtual  void draw(ofPath & shape) ###
### virtual  void draw(ofMesh & vertexData) ###
### virtual  void draw(ofMesh & vertexData, ofPolyRenderMode renderType) ###
### virtual  void draw(vector<ofPoint> & vertexData, ofPrimitiveMode drawMode) ###
### virtual  void draw(ofImage & image, float x, float y, float z, float w, float h) ###
### virtual  void draw(ofFloatImage & image, float x, float y, float z, float w, float h) ###
### virtual  void draw(ofShortImage & image, float x, float y, float z, float w, float h) ###

//--------------------------------------------
// transformations
### virtual  void pushView() ###
### virtual  void popView() ###

// setup matrices and viewport (upto you to push and pop view before and after)
// if width or height are 0, assume windows dimensions (ofGetWidth(), ofGetHeight())
// if nearDist or farDist are 0 assume defaults (calculated based on width / height)
### virtual  void viewport(ofRectangle viewport) ###
### virtual  void viewport(float x = 0, float y = 0, float width = 0, float height = 0, bool invertY = true) ###
### virtual  void setupScreenPerspective(float width = 0, float height = 0, ofOrientation orientation=OF_ORIENTATION_UNKNOWN, bool vFlip = true, float fov = 60, float nearDist = 0, float farDist = 0) ###
### virtual  void setupScreenOrtho(float width = 0, float height = 0, ofOrientation orientation=OF_ORIENTATION_UNKNOWN, bool vFlip = true, float nearDist = -1, float farDist = 1) ###
### virtual  ofRectangle getCurrentViewport(){return ofRectangle() ###} ###
### virtual  int getViewportWidth(){return 0 ###} ###
### virtual  int getViewportHeight(){return 0 ###} ###

### virtual  void setCoordHandedness(ofHandednessType handedness) ###
### virtual  ofHandednessType getCoordHandedness(){return OF_LEFT_HANDED ###} ###

//our openGL wrappers
### virtual  void pushMatrix() ###
### virtual  void popMatrix() ###
### virtual  void translate(float x, float y, float z = 0) ###
### virtual  void translate(const ofPoint & p) ###
### virtual  void scale(float xAmnt, float yAmnt, float zAmnt = 1) ###
### virtual  void rotate(float degrees, float vecX, float vecY, float vecZ) ###
### virtual  void rotateX(float degrees) ###
### virtual  void rotateY(float degrees) ###
### virtual  void rotateZ(float degrees) ###
### virtual  void rotate(float degrees) ###

// screen coordinate things / default gl values
### virtual  void setupGraphicDefaults() ###
### virtual  void setupScreen() ###

// drawing modes
### virtual  void setRectMode(ofRectMode mode) ###
### virtual  ofRectMode getRectMode() ###
### virtual  void setFillMode(ofFillFlag fill) ###
### virtual  ofFillFlag getFillMode() ###
### virtual  void setLineWidth(float lineWidth) ###
### virtual  void setBlendMode(ofBlendMode blendMode) ###
### virtual  void setLineSmoothing(bool smooth) ###
### virtual  void setCircleResolution(int res) ###
### virtual  void enablePointSprites() ###
### virtual  void disablePointSprites() ###

// color options
### virtual  void setColor(int r, int g, int b) ### // 0-255
### virtual  void setColor(int r, int g, int b, int a) ### // 0-255
### virtual  void setColor(const ofColor & color) ###
### virtual  void setColor(const ofColor & color, int _a) ###
### virtual  void setColor(int gray) ### // new set a color as grayscale with one argument
### virtual  void setHexColor( int hexColor ) ### // hex, like web 0xFF0033 ###

// bg color
### virtual  ofFloatColor & getBgColor() ###
### virtual  bool bClearBg(){return true ###} ###
### virtual  void background(const ofColor & c) ###
### virtual  void background(float brightness) ###
### virtual  void background(int hexColor, float _a=255.0f) ###
### virtual  void background(int r, int g, int b, int a=255) ###

### virtual  void setBackgroundAuto(bool bManual) ###		// default is true

### virtual  void clear(float r, float g, float b, float a=0) ###
### virtual  void clear(float brightness, float a=0) ###
### virtual  void clearAlpha() ###

// drawing
### virtual  void drawLine(float x1, float y1, float z1, float x2, float y2, float z2) ###
### virtual  void drawRectangle(float x, float y, float z, float w, float h) ###
### virtual  void drawTriangle(float x1, float y1, float z1, float x2, float y2, float z2, float x3, float y3, float z3) ###
### virtual  void drawCircle(float x, float y, float z, float radius) ###
### virtual  void drawEllipse(float x, float y, float z, float width, float height) ###
### virtual  void drawString(string text, float x, float y, float z, ofDrawBitmapMode mode) ###


// returns true if the renderer can render curves without decomposing them
### virtual  bool rendersPathPrimitives() ###
