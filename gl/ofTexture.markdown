
## ofTextureData ##

### unsigned int textureID ###
### int textureTarget ###
### int glTypeInternal ### // internalFormat, e.g., GL_RGB8. should be named glInternalFormat
### int glType ### // format, e.g., GL_RGB. should be named glFormat
### int pixelType ###  // type, e.g., GL_UNSIGNED_BYTE. should be named glType

### float tex_t ###
### float tex_u ###
### float tex_w ###
### float tex_h ###
### float width, height ###

### bool bFlipTexture ###
### ofTexCompression compressionType ###
### bool bAllocated ###

## ofTexture ##

oftexture is a wrapper for opengl's texture support. Specifically, it allows to use non power of 2 textures in opengl, and to upload and draw graphical data.

### ofTexture() ###

### ofTexture(const ofTexture & mom) ###
Copy constructor

### ofTexture& operator=(const ofTexture & mom) ###
Let's you do 

```cpp
tex2 = tex1;
```

### virtual ~ofTexture() ###

### void  allocate(const ofTextureData & textureData) ###
You need to allocate the texture before drawing it or loading data into it.

### void  allocate(int w, int h, int glInternalFormat) ###
You need to allocate the texture before drawing it or loading data into it.
uses the currently set OF texture type - default ARB texture

### void  allocate(int w, int h, int glInternalFormat, bool bUseARBExtention) ###
You need to allocate the texture before drawing it or loading data into it, lets you overide the default OF texture type

### void  clear() ###
Clears all the data from the texture

### void  loadData(float* data, int w, int h, int glFormat) ###
Loads raw data from an array. Make sure to se the pixel type in the glFormat correctly.

### void  loadData(unsigned char* data, int w, int h, int glFormat) ###
Loads raw data from an array. Make sure to se the pixel type  in the glFormat correctly.

### void  loadData(unsigned short* data, int w, int h, int glFormat) ###
Loads raw data from an array. Make sure to se the pixel type  in the glFormat correctly.

### void  loadData([ofPixels](../graphics/ofPixels.htm) & pix) ###
Loads raw data from an ofPixels object.

### void  loadData(ofShortPixels & pix) ###
Loads raw data from an ofPixels object.

### void  loadData(ofFloatPixels & pix) ###
Loads raw data from an ofPixels object.

### void  loadScreenData(int x, int y, int w, int h) ###
Load data from the current screen into this texture.

### void  setAnchorPercent(float xPct, float yPct) ###

The anchor is the point the image is drawn around. This can be useful if you want to rotate an image around a particular point, allowing you to set the anchor as a percentage of the image width/height ( 0.0-1.0 range )

### void  setAnchorPoint(float x, float y) ###
set the anchor point in pixels

### void  resetAnchor() ### //resets the anchor to (0, 0)

### void  draw(const [ofRectangle](../types/ofRectangle.htm) & r) ###
Draws the texture into a rectangle.

### void  draw(const ofPoint & p, float w, float h) ###
Draws the texture at the point rpresent by ofPoint

### void  draw(float x, float y, float w, float h) ###
Draws the texture at the x, y and w, h.

### void  draw(float x, float y, float z, float w, float h) ###
Draws the texture at the x, y, z in 3D space with the width and height at w,h.

### void  draw(const ofPoint & p) ###
Draws the texture at the point passed in.

### void  draw(float x, float y) ###
Draws the texture at the point passed in.

### void  draw(float x, float y, float z) ###
Draws the texture at the point passed in in 3D space.

### void  draw(ofPoint p1, ofPoint p2, ofPoint p3, ofPoint p4) ###
Draws the texture at 4 poitns passed in as if you created 4 glVertices.

### void  readToPixels([ofPixels](../graphics/ofPixels.htm) & pixels) ###
Reads the data from the texture to an ofPixels object.

### void  readToPixels(ofShortPixels & pixels) ###
Reads the data from the texture to an ofShortPixels object.

### void  readToPixels(ofFloatPixels & pixels) ###
Reads the data from the texture to an ofFloatPixels object.

### void  bind() ###
This is for the advanced user who wants to draw textures in their own way. Each set of vertices that you draw after calling bind() will be textured using this texture.

### void  unbind() ###
This for the advanced user who wants to draw textures in their own way. This stops vertices from being textured using this texture.

### ofPoint getCoordFromPoint(float xPos, float yPos) ###	
these are helpers to allow you to get points for the texture ala "glTexCoordf" but are texture type independent. use them for immediate or non immediate mode

### ofPoint getCoordFromPercent(float xPts, float yPts) ###		

### void  setTextureWrap(GLint wrapModeHorizontal, GLint wrapModeVertical) ###
Sets how the texture wraps around the edges of the vertices that the texture is being drawn to.

### void  setTextureMinMagFilter(GLint minFilter, GLint maxFilter) ###
Set how the texture is scaled up and down, when it's being drawn larger or smaller than it's actual size.

### void  setCompression(ofTexCompression compression) ###

### bool bAllocated() ###
Get whether the texture has been allocated.

### bool isAllocated() ###
Get whether the texture has been allocated.

ofTextureData getTextureData() ###

// reference to the actual textureData inside the smart pointer
// for backwards compatibility
ofTextureData texData ###

float getHeight() ###
float getWidth() ###