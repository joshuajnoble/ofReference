
## ofVbo ##

First things first: a Vertex Buffer Object (VBO) provides methods a way for you to create vertices, normals, colors, and texture coordinates on the graphics card for non-immediate mode rendering. This means that you can store it all on the graphics card and then access, update, or draw it, whenever you need. This is pretty convenient when you have something that you want to draw multiple times wihtout changing it much, because it means that instead of needing to upload new data each time, you can simply draw it instead of needing to recreate all your vertices and colors, a philosophy which is probably familiar to you from working with the ofFbo or ofTexture.

There are a few things that are important to understand about VBOs:

Each property of the VBO, vertices, texCoords, normals, colors, can be either dynamic or static. You set it to static when you know that you won't be updating it later on. You set it to dynamic when you know you will be updating it later on.

Just like with ofMesh, you need to keep track of the vertices and their indices in order to make shapes and you can draw a VBO in any one of the OpenGL drawing modes, GL_LINE_STRIP, GL_POINTS, GL_QUADS, GL_TRIANGLES and GL_TRIANGLE_STRIP.

Vertices are passed to your graphics card and your graphics card fill in the spaces in between them in a processing usually called “the rendering pipeline”. The rendering pipeline goes more or less like this:
1. Say how you’re going to connect all the points.
2. Make some points.
3. Say that you’re done making points.

You may be thinking: “I’ll just make eight vertices and voila: a cube.” Not so quick. There’s a hitch and that hitch is that the OpenGL renderer has different ways of connecting the vertices that you pass to it and none are as efficient as to only need eight vertices to create a cube. You’ve probably seen a version of the following image somewhere before.

![gl vertices](gl_vertices_options.jpg)

Generally you have to create your points to fit the drawing mode that you’ve selected because of what’s called “winding”. A vertex gets connected to another vertex in the order that the mode does it’s winding and this means that you might need multiple vertices in a given location to create the shape you want. The cube, for example, requires eighteen vertices, not the eight that you would expect. If you note the order of vertices in the GL chart above you’ll see that all of them use their vertices slightly differently (in particular you should make note of the GL_TRIANGLE_STRIP example). Drawing a shape requires that you keep track of which drawing mode is being used and which order your vertices are declared in. If you’re thinking: “it would be nice if there were an abstraction layer for this” you’re thinking right. Enter the mesh, which is really just an abstraction of the vertex and drawing mode that we started with but which has the added bonus of managing the draw order for you. That may seem insignificant at first, but it provides some real benefits when working with complex geometry.

The following example shows an ofVbo representing an isocohedron:

```cpp

const ofIndexType Faces[] = {
	2, 1, 0,
	3, 2, 0,
	4, 3, 0,
	5, 4, 0,
	1, 5, 0,
	11, 6,  7,
	11, 7,  8,
	11, 8,  9,
	11, 9,  10,
	11, 10, 6,
	1, 2, 6,
	2, 3, 7,
	3, 4, 8,
	4, 5, 9,
	5, 1, 10,
	2,  7, 6,
	3,  8, 7,
	4,  9, 8,
	5, 10, 9,
	1, 6, 10 };

const float Verts[] = {
	0.000f,  0.000f,  1.000f,
	0.894f,  0.000f,  0.447f,
	0.276f,  0.851f,  0.447f,
	-0.724f,  0.526f,  0.447f,
	-0.724f, -0.526f,  0.447f,
	0.276f, -0.851f,  0.447f,
	0.724f,  0.526f, -0.447f,
	-0.276f,  0.851f, -0.447f,
	-0.894f,  0.000f, -0.447f,
	-0.276f, -0.851f, -0.447f,
	0.724f, -0.526f, -0.447f,
	0.000f,  0.000f, -1.000f };

ofVec3f v[12];
ofVec3f n[12];
ofFloatColor c[12];

ofVbo vbo;

void HelloWorldApp::setup()
{	

	int i, j = 0;

	for ( i = 0; i < 12; i++ )
	{
		
		c[i].r = ofRandom(1.0);
		c[i].g = ofRandom(1.0);
		c[i].b = ofRandom(1.0);
		
		v[i][0] = Verts[j] * 100.f;
		j++;
		v[i][1] = Verts[j] * 100.f;
		j++;
		v[i][2] = Verts[j] * 100.f;
		j++;
		
	}
	
	vbo.setVertexData( &v[0], 12, GL_STATIC_DRAW );
	vbo.setColorData( &c[0], 12, GL_STATIC_DRAW );
	vbo.setIndexData( &Faces[0], 60, GL_STATIC_DRAW );
	
	glEnable(GL_DEPTH_TEST);
}

void HelloWorldApp::draw(){
	ofTranslate(ofGetWidth()/2, ofGetHeight()/2, 100);
	ofRotate(ofGetElapsedTimef() * 20.0, 1, 1, 0);
	glPointSize(10.f);
	vbo.drawElements( GL_TRIANGLES, 60);
}

```
![vbo result](vbo.png)

### ofVbo() ###

### ofVbo(const ofVbo & mom) ###

Allows you copy one ofVbo from another ofVbo.

### ofVbo & operator=(const ofVbo& mom) ###

Allows you copy one ofVbo from another ofVbo using the = operator:

```cpp
ofVbo one, two;
//add some vertices and texcoords to one
two = one;
```

### ~ofVbo() ###

### void setMesh(const ofMesh & mesh, int usage) ###

This copies an ofMesh into an ofVbo, which is

### void setVertexData(const ofVec3f * verts, int total, int usage) ###

Sets vertices using ofVec3f objects. You pass a pointer to ofVec3fs, a int saying how many are in the pointer, and what kind of array you want to be created on the graphics card for the VBO to use.

```cpp
ofVec3f *v = new ofVec3f[12];
vbo.setVertexData(v, 12, GL_DYNAMIC_DRAW);

```

total Specifies the number of objects that you're passing in.

usage Specifies the expected usage pattern of the data store. The symbolic constant must be GL_STREAM_DRAW, GL_STREAM_READ, GL_STREAM_COPY, GL_STATIC_DRAW, GL_STATIC_READ, GL_STATIC_COPY, GL_DYNAMIC_DRAW, GL_DYNAMIC_READ, or GL_DYNAMIC_COPY.


### void setVertexData(const ofVec2f * verts, int total, int usage) ###

total Specifies the number of objects that you're passing in.

usage Specifies the expected usage pattern of the data store. The symbolic constant must be GL_STREAM_DRAW, GL_STREAM_READ, GL_STREAM_COPY, GL_STATIC_DRAW, GL_STATIC_READ, GL_STATIC_COPY, GL_DYNAMIC_DRAW, GL_DYNAMIC_READ, or GL_DYNAMIC_COPY.


### void setColorData(const ofFloatColor * colors, int total, int usage) ###

total Specifies the number of objects that you're passing in.

usage Specifies the expected usage pattern of the data store. The symbolic constant must be GL_STREAM_DRAW, GL_STREAM_READ, GL_STREAM_COPY, GL_STATIC_DRAW, GL_STATIC_READ, GL_STATIC_COPY, GL_DYNAMIC_DRAW, GL_DYNAMIC_READ, or GL_DYNAMIC_COPY.


### void setNormalData(const ofVec3f * normals, int total, int usage) ###

total Specifies the number of objects that you're passing in.

usage Specifies the expected usage pattern of the data store. The symbolic constant must be GL_STREAM_DRAW, GL_STREAM_READ, GL_STREAM_COPY, GL_STATIC_DRAW, GL_STATIC_READ, GL_STATIC_COPY, GL_DYNAMIC_DRAW, GL_DYNAMIC_READ, or GL_DYNAMIC_COPY.

### void setTexCoordData(const ofVec2f * texCoords, int total, int usage) ###

total Specifies the number of objects that you're passing in.

usage Specifies the expected usage pattern of the data store. The symbolic constant must be GL_STREAM_DRAW, GL_STREAM_READ, GL_STREAM_COPY, GL_STATIC_DRAW, GL_STATIC_READ, GL_STATIC_COPY, GL_DYNAMIC_DRAW, GL_DYNAMIC_READ, or GL_DYNAMIC_COPY.

### void setIndexData(const ofIndexType * indices, int total, int usage) ###

Indices are the indices of vertices that you want used to create your polygons, so like {1, 2, 3} for a triangle, would make a triangle out of vertexs at positions 1, 2, and 3 in the vertex array. QUADS need 4 indices per primitive, LINES need 2.

total Specifies the number of objects that you're passing in.

usage Specifies the expected usage pattern of the data store. The symbolic constant must be GL_STREAM_DRAW, GL_STREAM_READ, GL_STREAM_COPY, GL_STATIC_DRAW, GL_STATIC_READ, GL_STATIC_COPY, GL_DYNAMIC_DRAW, GL_DYNAMIC_READ, or GL_DYNAMIC_COPY.

### void setVertexData(const float * vert0x, int numCoords, int total, int usage, int stride=0) ###

vert0x Specifies a pointer to data that will be copied into the data store for initialization.

numCoords This is the number of complete coordinates that youre adding to the vbo

total Specifies the number of objects that you're passing in.

usage Specifies the expected usage pattern of the data store. The symbolic constant must be GL_STREAM_DRAW, GL_STREAM_READ, GL_STREAM_COPY, GL_STATIC_DRAW, GL_STATIC_READ, GL_STATIC_COPY, GL_DYNAMIC_DRAW, GL_DYNAMIC_READ, or GL_DYNAMIC_COPY.


```cpp

float Verts[] = {...};
vbo.setVertexData(&Verts[0], 12, 36, GL_DYNAMIC_DRAW);

```

### void setColorData(const float * color0r, int total, int usage, int stride=0) ###



### void setNormalData(const float * normal0x, int total, int usage, int stride=0) ###
### void setTexCoordData(const float * texCoord0x, int total, int usage, int stride=0) ###

### void updateMesh(const ofMesh & mesh) ###

This allows you add a mesh to to the vbo, like so:

```cpp
ofMesh m;
/// fill out the mesh
ofVbo v;
v.updateMesh(mesh);
```

### void updateVertexData(const ofVec3f * verts, int total) ###

If you've created your vbo with vertexes that are using GL_DYNAMIC_DRAW then you can update the vertexes at any time. This is for 3D vbos.

### void updateVertexData(const ofVec2f * verts, int total) ###

If you've created your vbo with vertexes that are using GL_DYNAMIC_DRAW then you can update the vertexes at any time. This is for 2D vbos as it only uses ofVe2f.

### void updateColorData(const ofFloatColor * colors, int total) ###

If you've created your vbo with colors that are using GL_DYNAMIC_DRAW then you can update the vertexes at any time.

### void updateNormalData(const ofVec3f * normals, int total) ###	

If you've created your vbo with normals that are using GL_DYNAMIC_DRAW then you can update the vertexes at any time.

### void updateTexCoordData(const ofVec2f * texCoords, int total) ###

If you've created your vbo with texture coordinates that are using GL_DYNAMIC_DRAW then you can update the vertexes at any time.

### void updateIndexData(const ofIndexType * indices, int total) ###

If you've created your vbo with indices that are using GL_DYNAMIC_DRAW then you can update the vertexes at any time. Note that if you're not adding or removing vertieces you probably don't need to update the vertices.

### void updateVertexData(const float * ver0x, int total) ###

If you've created your vbo with indices that are using GL_DYNAMIC_DRAW then you can update the vertexes at any time. Note that if you're not adding or removing vertieces you probably don't need to update the vertices.

### void updateColorData(const float * color0r, int total) ###

If you've created your vbo with colors that are using GL_DYNAMIC_DRAW then you can update the vertexes at any time. This version uses 3 floats for the RGB of each color instead of ofColor.

### void updateNormalData(const float * normal0x, int total) ###

If you've created your vbo with normals that are using GL_DYNAMIC_DRAW then you can update the vertexes at any time. This version uses 3 floats for each normal instead of an ofVec3f.

### void updateTexCoordData(const float * texCoord0x, int total) ###

If you've created your vbo with texture coordinates that are using GL_DYNAMIC_DRAW then you can update the vertexes at any time. This version uses 2 floats for each tex coord instead of an ofVec2f.

### GLuint getVertId() ###
### GLuint getColorId() ###
### GLuint getNormalId() ###
### GLuint getTexCoordId() ###
### GLuint getIndexId() ###

### bool getIsAllocated() ###
### bool getUsingVerts() ###
### bool getUsingColors() ###
### bool getUsingNormals() ###
### bool getUsingTexCoords() ###
### bool getUsingIndices() ###

### void draw(int drawMode, int first, int total) ###

This method allows you to draw your VBO but unlike drawElements() ignores any indices that you might have set up. This is an important distinction between the two methods.

mode
Specifies what kind of primitives to render. Symbolic constants GL_POINTS, GL_LINE_STRIP, GL_LINE_LOOP, GL_LINES, GL_TRIANGLE_STRIP, GL_TRIANGLE_FAN, GL_TRIANGLES, GL_QUAD_STRIP, GL_QUADS, and GL_POLYGON are accepted.

first
Specifies the starting index in the enabled arrays.

total
Specifies the number of indices to be rendered. This last part is pretty important: if you have more indices than vertices you'll want to make sure that you pass the number of indices, not the number of vertices.

### void drawElements(int drawMode, int amt) ###

drawElements allows you use indices, unlike draw() which ignores them.

drawMode
Specifies what kind of primitives to render. Symbolic constants GL_POINTS, GL_LINE_STRIP, GL_LINE_LOOP, GL_LINES, GL_TRIANGLE_STRIP, GL_TRIANGLE_FAN, GL_TRIANGLES, GL_QUAD_STRIP, GL_QUADS, and GL_POLYGON are accepted.

```cpp
vbo.drawElements( GL_TRIANGLES, 60);
```

amt specifies the number of indices to be rendered. This last part is pretty important: if you have more indices than vertices you'll want to make sure that you pass the number of indices, not the number of vertices.

### void bind() ###

This is for advanced users who might want to use ways of drawing other than draw() or drawElements(), it simply binds all the arrays for the VBO.

### void unbind() ###

This is for advanced users who might want to use ways of drawing other than draw() or drawElements(), it simply unbinds all the arrays for the VBO.

### void clear() ###

This erases your VBOs data from your graphics card, but not the VBO itself, so you can fill it with data again.