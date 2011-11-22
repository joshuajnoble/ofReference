## ofFbo ##

ofFbo is an easy way to work with Frame Buffer Objects or fobs, which allow you to easily do off-screen rendering, very convenient for doing image filters or post-processing effects. 

As an example, with an fbo you can do some drawing to the fbo (instead of to the screen or a texture) and then do some blurring, maybe invert the colors, combine multiple images, all without needing to draw it to the screen until you're ready.

fbos are also used to create views of other scenes, like a TV in a house. A scene can be rendered through an FBO to a texture, then that texture can be applied to the surface of another object.

You can also create a depth buffer within your fbo to figure out which objects should go in front of which other objects.

As an example of an advanced usage:

Create an ofFbo.
Attach the color buffer of the ofFbo to a texture.
Attach the depth buffer of the ofFbo to a texture.
Render the texture to screen with a pixel shader using ofShader.

Rad!

### ofFbo() ###
Default constructor

### ofFbo(const ofFbo & mom) ###
Copies all data from the mom fbo

### ofFbo & operator=(const ofFbo & fbo) ###
This overloaded operator allows you to set one fbo from another using the = operator. Very convenient.


### void allocate(int width, int height, int internalformat = GL_RGBA, int numSamples = 0) ###
Before you use the fbo you need to allocate it. This sets the width, height, and GL type of the fbo (i.e. whether it has alpha data or not) and the number of samples for MSAA. MSAA is sort of a big topic.

MSAA is what you typically have in hardware on a modern graphics card. The graphics card renders to a surface that is larger than the final image, but in shading each "cluster" of samples (that will end up in a single pixel on the final screen) the pixel shader is run only once. We save a ton of fill rate, but we still burn memory bandwidth.

This technique does not anti-alias any effects coming out of the shader, because the shader runs at 1x, so alpha cutouts are jagged. This is the most common way to run a forward-rendering game. MSAA does not work for a deferred renderer because lighting decisions are made after the MSAA is "resolved" (down-sized) to its final image size.

### void allocate(Settings settings = Settings()) ###
You can also allocate the ofFbo using a Settings object
	
### void draw(float x, float y) ###
This allows you draw everything that's in your fbo to the screen using it's default height and width

### void draw(float x, float y, float width, float height) ###
This allows you draw everything that's in your fbo to the screen using any height and width
	
### void setAnchorPercent(float xPct, float yPct) ###
You can set the anchor that the texture will be drawn at.

### void setAnchorPoint(float x, float y) ###
This allows you set the anchor position of the texture in the fbo when you draw it.

### void resetAnchor() ###
This allows you reset the anchor position.

### void setDefaultTextureIndex(int defaultTexture) ###
This allows you set the default texture.

### int getDefaultTextureIndex() ###
If you've set the default texture reference, you can get access to it here.
	
### ofTexture & getTextureReference() ###
This gives you access to the ofTexture contained w/in the fbo.

### ofTexture & getTextureReference(int attachmentPoint) ###
This gives you access to a particular ofTexture if there are more than 1 contained w/in the fbo.
	
### void begin() ###
Any drawing that you do after begin() is drawn into the fbo rather than the screen. This is how you draw things into your ofFbo instance.

### void end() ###
Any drawing that you do after end() is drawn into the fbo rather than the screen. This is how you stop drawing things into your ofFbo instance.
	
### void readToPixels(ofPixels & pixels, int attachmentPoint = 0) ###
This allows you to get the pixels from an ofFbo and store it in an ofPixels instance. The attachmentPoint parameter allows you indicate which of the textures attached to the fbo you want to grab

### void readToPixels(ofShortPixels & pixels, int attachmentPoint = 0) ###
This allows you to get the pixels from an ofFbo and store it in an ofShortPixels instance. The attachmentPoint parameter allows you indicate which of the textures attached to the fbo you want to grab. The ofShortPixels instance is useful when you want your image at short ints, or non-floating point values.

### void readToPixels(ofFloatPixels & pixels, int attachmentPoint = 0) ###
This allows you to get the pixels from an ofFbo and store it in an ofShortPixels instance. The attachmentPoint parameter allows you indicate which of the textures attached to the fbo you want to grab. The ofShortPixels instance is useful when you want your image as floating point values.

### float getWidth() ###
This returns the width of the fbo.

### float getHeight() ###
This returns the height of the fbo.
		
### void bind() ###
This lets you draw the fbo using vertices to define the area that the fbo will be drawn into. This can be an ofRectangle, ofMesh, or other vertex based drawing technique.

### void unbind() ###
After you bind the fbo and draw with it, call fbo to stop the fbo from being attached to vertices that are created.

### int getNumTextures() ###
This returns the number of textures that the fbo contains.

### GLuint getFbo() ###
This returnes the GLuint of Fbo for advanced actions.
		
### static bool	checkGLSupport() ###
This ensures that your computer and graphics card support FBOs.

### static int maxColorAttachments() ###
This returnes the max number of simultaneous max color attachments.

### static int maxDrawBuffers() ###
This returnes the max number of simultaneous draw buffers.

### static int maxSamples() ###
This gives you the maximum number of MSAA samples.

### GLuint getDepthBuffer() ###
This gives you the OpenGL id of the depthBuffer that the fbo contains. The depth buffer contains the z-ordering information for each pixel, i.e. what object should be appearing at each pixel according to the depth relative to the view.

### GLuint getStencilBuffer() ###
This gives you the OpenGL id of the stencilBuffer that the fbo contains. A stencil buffer is typically used to add shadows to 3D applications or to do some kinds of reflections. It basically creates a per-pixel mask that can be used to determine which pixels to discard because of a shadow or a reflection.

## Settings ##

The settings object is an easier way to set up the fbo when you allocate the fbo.

### int width ###
width of images attached to fbo

### int	height ###
height of images attached to fbo

### int	numColorbuffers ###
Sets how how many color buffers to create in the fbo.

### bool useDepth ###
This sets whether the fbo will use a depth buffer or not.

### bool useStencil ###
This sets whether the fbo will use a stencil buffer or not.

### GLenum textureTarget ###
This defines how the texture of the fbo GL_TEXTURE_2D or GL_TEXTURE_RECTANGLE_ARB. By default this is GL_TEXTURE_RECTANGLE_ARB.

### GLint internalformat ###
Represents the color mode of the fbo. Possible options are GL_RGBA, GL_RGBA16F_ARB, GL_RGBA32F_ARB, GL_LUMINANCE32F_ARB.

### int	wrapModeHorizontal ###
This sets how the fbo will wrap around vertical edges of an object that's too large for the fbo along the horizontal. Possible options are GL_NEAREST, GL_LINEAR etc.

### int	wrapModeVertical ###
This sets how the fbo will wrap around vertical edges of an object that's too large for the fbo along the vertical. Possible options are GL_NEAREST, GL_LINEAR etc.

### int	minFilter ###
When you get further or closer to the fbo you need to scale the image. This allows you to set the filter determining how the texture will handle when it scales GL_NEAREST, GL_LINEAR.

### int	maxFilter ###
When you get further or closer to the fbo you need to scale the image. This allows you to set the filter determining how the texture will handle when it scales GL_NEAREST, GL_LINEAR.

### int	numSamples ###
number of samples for multisampling (set 0 to disable)
