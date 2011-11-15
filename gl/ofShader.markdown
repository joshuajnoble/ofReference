
## ofShader ##

Graphics Language Shading Language (GLSL) can be used in oF by using the ofShader object. Shading happens in two distinct steps: the vertex shader creates values for each vertex in the model, and the fragment shader creates values for each pixel in the rendered object. To define a shader, create a .frag file for the fragment shader and a .vert file for the vertex shader.
A vertex shader has attributes about a location in space or vertex, which means not only the actual coordinates of that location but also its color, how any textures should be mapped onto it, and how the vertices are modified in the operation. A vertex shader can change the positions of each vertex, the number of lighting computations per vertex, and the color that will be applied to each vertex.
A geometry shader can generate new graphics primitives like points, lines, and triangles, from those primitives that were sent to the graphics card from the CPU. This means that you could get a point and turn it into a triangle or even a bunch of triangles, or get a line and turn it into a rectangle, or do real-time extrusion. They are very powerful and can be quite tricky to get right, but they’re becoming more popular.
The fragment shader is somewhat misleadingly named because what it really allows you to do is to change values assigned to each pixel. The vertex shader operates on the vertices, and the fragment shader operates on the pixels. By the time the fragment shader gets information passed into it by the graphics card, the color of a particular pixel has already been computed and in the fragment shader can be combined with an element like a lighting effecting, a fog effect, or a blur among many other options. The usual end result of this stage per fragment is a color value and a depth for the fragment.

### ofShader() ###
### ~ofShader() ###

### bool load(string shaderName) ###
This assumes that your vertex and fragment shaders have the same name and loads them.

### bool load(string vertName, string fragName, string geomName="") ###
Here you can load shaders with whatever names you choose. The geometry shader is optional, but the vertex and fragment shaders aren't.

### void setGeometryInputType(GLenum type) ###
You have to call this before linking the program with geometry shaders.
Possible types are GL_POINTS, GL_LINES, GL_LINES_ADJACENCY_EXT, GL_TRIANGLES, GL_TRIANGLES_ADJACENCY_EXT

### void setGeometryOutputType(GLenum type) ###
You have to call this before linking the program with geometry shaders.
type: GL_POINTS, GL_LINE_STRIP or GL_TRIANGLE_STRIP

### void setGeometryOutputCount(int count) ###
You have to call this before linking the program with geometry shaders to set number of output vertices

### int getGeometryMaxOutputCount() ###	### 
returns maximum number of supported vertices for your graphics card


### void unload() ###
This unload the shader, which means that it will not be active on the graphics card any longer.

### void begin() ###

After you call begin() everything that you draw, vertexes and textures, in your of application have the effects of the shader applied to them.

### void end() ###

After you call end() any drawing, vertexes and textures, do not have the effect of the shader applied to them.

### void setUniformTexture(const char* name, ofBaseHasTexture& img, int textureLocation) ###
set a texture reference

On your shader it should look like this:

```cpp
uniform sampler2DRect texture;
```

### void setUniformTexture(const char* name, ofTexture& img, int textureLocation) ###

For multi-texturing.

```cpp
uniform sampler2DRect texture;
```

### void setUniform1i(const char* name, int v1) ###

set a single uniform value. On your shader this should look like:

```cpp
uniform int texture;
```

### void setUniform2i(const char* name, int v1, int v2) ###

```cpp
uniform ivec2 texture;
```

### void setUniform3i(const char* name, int v1, int v2, int v3) ###

```cpp
uniform ivec3 texture;
```

### void setUniform4i(const char* name, int v1, int v2, int v3, int v4) ###

```cpp
uniform ivec4 texture;
```

### void setUniform1f(const char* name, float v1) ###
set a float uniform on the shader

### void setUniform2f(const char* name, float v1, float v2) ###
set a vec2 uniform on the shader

### void setUniform3f(const char* name, float v1, float v2, float v3) ###
set a vec3 uniform on the shader


### void setUniform4f(const char* name, float v1, float v2, float v3, float v4) ###
set a vec4 uniform on the shader

```cpp
vec4 fv;
```

### void setUniform1iv(const char* name, int* v, int count = 1) ###

set an array of uniform values on the shader, this uses single values, i.e. 

```cpp
int ids[4] = {1, 2, 3, 4};
```
On the shader side, this is:

```cpp
ivec iv[2];
```

### void setUniform2iv(const char* name, int* v, int count = 1) ###
set an array of uniform values on the shader using int[2] value. On the shader this looks like:

```cpp
ivec2 iv[2];
```

### void setUniform3iv(const char* name, int* v, int count = 1) ###
set an array of uniform values on the shader using int[2] value. On the shader this looks like:

```cpp
ivec3 iv[2];
```

### void setUniform4iv(const char* name, int* v, int count = 1) ###
set an array of uniform values on the shader using int[2] value. On the shader this looks like:

```cpp
ivec4 iv[2];
```

### void setUniform1fv(const char* name, float* v, int count = 1) ###

set an array of uniform values on the shader using int[2] value. On the shader this looks like:

This allows you to set multiple float uniforms.

```cpp
float v[2];
```

### void setUniform2fv(const char* name, float* v, int count = 1) ###

This allows you to set multiple vec2 uniforms.

```cpp
vec2 v[2];
```

### void setUniform3fv(const char* name, float* v, int count = 1) ###

This allows you to set multiple vec3 uniforms.

```cpp
vec3 v[2];
```

### void setUniform4fv(const char* name, float* v, int count = 1) ###

This allows you to set multiple vec4 uniforms.

```cpp
vec4 v[2];
```

### GLint getAttributeLocation(const char* name) ###
// set attributes that vary per vertex (look up the location before glBegin)

### void setAttribute1s(GLint location, short v1) ###
Set a short attribute, a short int, on the shader.

### void setAttribute2s(GLint location, short v1, short v2) ###
Set two short attributes, a short int, on the shader.

### void setAttribute3s(GLint location, short v1, short v2, short v3) ###
Set three short attributes, a short int, on the shader.

### void setAttribute4s(GLint location, short v1, short v2, short v3, short v4) ###
Set four short attributes, a short int, on the shader.

### void setAttribute1f(GLint location, float v1) ###
Set one float attributes on the shader.

### void setAttribute2f(GLint location, float v1, float v2) ###
Set two float attributes on the shader.

### void setAttribute3f(GLint location, float v1, float v2, float v3) ###
Set three float attributes on the shader.

### void setAttribute4f(GLint location, float v1, float v2, float v3, float v4) ###
Set four float attributes on the shader.

### void setAttribute1d(GLint location, double v1) ###
Set one double attribute on the shader.

### void setAttribute2d(GLint location, double v1, double v2) ###
Set two double attribute on the shader.

### void setAttribute3d(GLint location, double v1, double v2, double v3) ###
Set three double attribute on the shader.

### void setAttribute4d(GLint location, double v1, double v2, double v3, double v4) ###
Set four double attribute on the shader.

### void printActiveUniforms() ###
This prints out all the active uniforms to the console.

### void printActiveAttributes() ###
This prints out all the active attributes to the console.

### bool setupShaderFromSource(GLenum type, string source) ###
these methods create and compile a shader from a string, type: GL_VERTEX_SHADER, GL_FRAGMENT_SHADER, GL_GEOMETRY_SHADER_EXT etc.

### bool setupShaderFromFile(GLenum type, string filename) ###
This are more of advanced use function and doesn't need.

### bool linkProgram() ###
Links program with all compiled shaders. This is more of an advanced use method, as this is done automatically for you.

### GLuint& getProgram() ###
This returns the GLuint for the actual shader object that is active on the graphics card. This is more of an advanced usage method, but can be helpful if you need to do something that the ofShader doesn't support currently. This is all the shaders: vertex, geom, and frag.

### GLuint& getShader(GLenum type) ###
This returns the GLuint for the actual shader object that is active on the graphics card. This is more of an advanced usage method, but can be helpful if you need to do something that the ofShader doesn't support currently. This returns only one of the shaders. You can pass GL_VERTEX_SHADER, GL_GEOMETRY_SHADER_EXT, GL_FRAGMENT_SHADER

