## ofMesh ##

An ofMesh represents a set of vertices in 3D spaces, and normals at those points, colors at those points, and texture coordinates at those points. Each of these different properties is stored in a vector. 

Vertices are passed to your graphics card and your graphics card fill in the spaces in between them in a processing usually called “the rendering pipeline”. The rendering pipeline goes more or less like this:
1. Say how you’re going to connect all the points.
2. Make some points.
3. Say that you’re done making points.

You may be thinking: “I’ll just make eight vertices and voila: a cube.” Not so quick. There’s a hitch and that hitch is that the OpenGL renderer has different ways of connecting the vertices that you pass to it and none are as efficient as to only need eight vertices to create a cube. You’ve probably seen a version of the following image somewhere before.

Generally you have to create your points to fit the drawing mode that you’ve selected because of what’s called “winding”. A vertex gets connected to another vertex in the order that the mode does it’s winding and this means that you might need multiple vertices in a given location to create the shape you want. The cube, for example, requires eighteen vertices, not the eight that you would expect. If you note the order of vertices in the GL chart above you’ll see that all of them use their vertices slightly differently (in particular you should make note of the GL_TRIANGLE_STRIP example). Drawing a shape requires that you keep track of which drawing mode is being used and which order your vertices are declared in. If you’re thinking: “it would be nice if there were an abstraction layer for this” you’re thinking right. Enter the mesh, which is really just an abstraction of the vertex and drawing mode that we started with but which has the added bonus of managing the draw order for you. That may seem insignificant at first, but it provides some real benefits when working with complex geometry.

### ofMesh() ###

This creates the mesh, using OF_PRIMITIVE_TRIANGLES and without any initial vertices.

### ofMesh([ofPrimitiveMode](../gl/ofGLUtils.htm#ofPrimitiveMode) mode, const ### vector<[ofVec3f](../math/ofVec3f.htm)>& verts) ###

This allows to you to use one of the other ofPrimitiveModes: OF_PRIMITIVE_TRIANGLES, OF_PRIMITIVE_TRIANGLE_STRIP, OF_PRIMITIVE_TRIANGLE_FAN, OF_PRIMITIVE_LINES, OF_PRIMITIVE_LINE_STRIP, OF_PRIMITIVE_LINE_LOOP, OF_PRIMITIVE_POINTS. See [ofGLUtils](../gl/ofGLUtils.htm) for more information on these types.

### void setMode([ofPrimitiveMode](../gl/ofGLUtils.htm#ofPrimitiveMode) mode) ###
Allows you to set the ofPrimitiveMode

### ofPrimitiveMode getMode() const ###

### void clear() ###
This removes all the vertices, colors, and indices from the mesh.

### void setupIndicesAuto() ###
Allow you to set up the indices automatically when you add a vertex.

### [ofVec3f](../math/ofVec3f.htm) getVertex(int i) ###
Gets the vertex at the index.

### void addVertex(const [ofVec3f](../math/ofVec3f.htm)& v) ###
Add a vertex.

### void addVertices(const ### vector<[ofVec3f](../math/ofVec3f.htm)>& verts) ###
Add multiple vertices.

### void addVertices(const [ofVec3f](../math/ofVec3f.htm)* verts, int amt) ###
Add multiple vertices.

### void removeVertex(int index) ###
Removes the vertex at the index in the vector.

### void setVertex(int index, const [ofVec3f](../math/ofVec3f.htm)& v) ###
Updates the vertex at the index in the vector.

### void clearVertices() ###
Removes all the vertices.

### [ofVec3f](../math/ofVec3f.htm) getNormal(int i) ###
Get the normal at the index in the normals vector.

### void addNormal(const [ofVec3f](../math/ofVec3f.htm)& n) ###
Adds a normal at the index in the normals vector.

### void addNormals(const ### vector<[ofVec3f](../math/ofVec3f.htm)>& norms) ###
Add normals to the the normals vector.

### void addNormals(const [ofVec3f](../math/ofVec3f.htm)* norms, int amt) ###
Add multiple normals at the index in the normals vector.

### void removeNormal(int index) ###
Remove a normal.

### void setNormal(int index, const [ofVec3f](../math/ofVec3f.htm)& n) ###
Set the normal at the index.

### void clearNormals() ###
Remove all the normals.

### [ofFloatColor](../types/ofColor.htm) getColor(int i) ###
Get the color at the index in the colors vector.

### void addColor(const [ofFloatColor](../types/ofColor.htm)& c) ###
Add a color at the index in the colors vector.

### void addColors(const ### vector<[ofFloatColor](../types/ofColor.htm)>& cols) ###
Add multiple colors at the index in the colors vector.

### void addColors(const [ofFloatColor](../types/ofColor.htm)* cols, int amt) ###
Add colors to the colors vector.

### void removeColor(int index) ###
Remove a color at the index in the colors vector.

### void setColor(int index, const [ofFloatColor](../types/ofColor.htm)& c) ###
Set the color at the index in the colors vector.

### void clearColors() ###
Clear all the colors.

### [ofVec2f](../math/ofVec2f.htm) getTexCoord(int i) ###
Get the Vec2f representing the texture coordinate. Because OF uses ARB textures these are in pixels rather than 0-1 normalized coordinates.

### void addTexCoord(const [ofVec2f](../math/ofVec2f.htm)& t) ###
Add a Vec2f representing the texture coordinate. Because OF uses ARB textures these are in pixels rather than 0-1 normalized coordinates.

### void addTexCoords(const ### vector<[ofVec2f](../math/ofVec2f.htm)>& tCoords) ###
Add multiple Vec2f representing the texture coordinate. Because OF uses ARB textures these are in pixels rather than 0-1 normalized coordinates.

### void addTexCoords(const [ofVec2f](../math/ofVec2f.htm)* tCoords, int amt) ###
Add multiple Vec2f representing the texture coordinate. Because OF uses ARB textures these are in pixels rather than 0-1 normalized coordinates.

### void removeTexCoord(int index) ###
Remove a Vec2f representing the texture coordinate.

### void setTexCoord(int index, const [ofVec2f](../math/ofVec2f.htm)& t) ###
Set a Vec2f representing the texture coordinate. Because OF uses ARB textures these are in pixels rather than 0-1 normalized coordinates.

### void clearTexCoords() ###
Clear all the texture coordinates.

### ofIndexType getIndex(int i) ###
Get the index from the index vector. Each index represents the index of the vertex in the vertices vector. This determines the way that the vertices are connected into the polgoynon type set in the primitiveMode.

### void addIndex(ofIndexType i) ###
Add an index from the index vector. Each index represents the index of the vertex in the vertices vector. This determines the way that the vertices are connected into the polgoynon type set in the primitiveMode.

### void addIndices(const ### vector<ofIndexType>& inds) ###
Add multiple indices to the index vector. Each index represents the index of the vertex in the vertices vector. This determines the way that the vertices are connected into the polgoynon type set in the primitiveMode.

### void addIndices(const ofIndexType* inds, int amt) ###
Add multiple indices to the index vector. Each index represents the index of the vertex in the vertices vector. This determines the way that the vertices are connected into the polgoynon type set in the primitiveMode.

### void removeIndex(int i) ###
Removes an index.

### void setIndex(int i, ofIndexType val) ###
This sets the index at i.

### void clearIndices() ###
Remove all the indices of the mesh. This means that your mesh will be a point cloud.

### void addTriangle(ofIndexType index1, ofIndexType index2, ofIndexType index3) ###
Adding a triangle means using three of the vertices that have already been added to create a triangle. This is an easy way to create triangles in the mesh. The indices refer to the index of the vertex in the vector of vertices.

### int getNumVertices() const ###
How many vertices that the mesh contains.

### int getNumColors() const ###
How many colors that the mesh contains.

### int getNumNormals() const ###
How many normals that the mesh contains.

### int getNumTexCoords() const ###
How many texture coordinates that the mesh contains.

### int getNumIndices() const ###
How many indices that the mesh contains.

### [ofVec3f](../math/ofVec3f.htm)* getVerticesPointer() ###
Get a pointer to the vertices that the mesh contains.

### [ofFloatColor](../types/ofColor.htm)* getColorsPointer() ###
Get a pointer to the colors that the mesh contains.

### [ofVec3f](../math/ofVec3f.htm)* getNormalsPointer() ###
Get a pointer to the normals that the mesh contains.

### [ofVec2f](../math/ofVec2f.htm)* getTexCoordsPointer() ###
Get a pointer to the texture coords that the mesh contains.

### ofIndexType* getIndexPointer() ###
Get a pointer to the indices that the mesh contains.

### const [ofVec3f](../math/ofVec3f.htm)* getVerticesPointer() const ###
Get a pointer to the vertices that the mesh contains.

### const [ofFloatColor](../types/ofColor.htm)* getColorsPointer() const ###
Get a pointer to the colors that the mesh contains.

### const [ofVec3f](../math/ofVec3f.htm)* getNormalsPointer() const ###
Get a pointer to the normals that the mesh contains.

### const [ofVec2f](../math/ofVec2f.htm)* getTexCoordsPointer() const ###
Get a pointer to the ofVec2f texture coordinates that the mesh contains.

### const ofIndexType* getIndexPointer() const ###
Get a pointer to the indices that the mesh contains.

### vector<[ofVec3f](../math/ofVec3f.htm)> & getVertices() ###
Get the vector that contains all of the vertices of the mesh.

### vector<[ofFloatColor](../types/ofColor.htm)> & getColors() ###
Get the vector that contains all of the colors of the mesh, if it has any.

### vector<[ofVec3f](../math/ofVec3f.htm)> & getNormals() ###
Get the vector that contains all of the normals of the mesh, if it has any.

### vector<[ofVec2f](../math/ofVec2f.htm)> & getTexCoords() ###
Get the vector that contains all of the vertices of the tex coords, if it has any.

### vector<ofIndexType> & getIndices() ###
Get the vector that contains all of the indices of the mesh, if it has any.

### vector<int>& getFace(int faceId) ###
Get the vector that contains all of the faces of the mesh. This isn't currently implemented.

### void setName(string name_) ###
Each mesh can have a name, here's where you set it.

### bool haveVertsChanged() ###
If the vertices of the mesh have changed, been added or removed.

### bool haveColorsChanged() ###
If the colors of the mesh have changed, been added or removed.

### bool haveNormalsChanged() ###
If the normals of the mesh have changed, been added or removed.

### bool haveTexCoordsChanged() ###
If the texture coords of the mesh have changed, been added or removed.

### bool haveIndicesChanged() ###
If the indices of the mesh have changed, been added or removed.

### bool hasVertices() ###
Whether the mesh has any vertices.

### bool hasColors() ###
Whether the mesh has any colors.

### bool hasNormals() ###
Whether the mesh has any normals.

### bool hasTexCoords() ###
Whether the mesh has any textures assigned to it.

### bool hasIndices() ###
Whether the mesh has any indices assigned to it.

### friend std::ostream& operator<<(std::ostream& os, ofMesh& data) ###

### void drawVertices() ###
This allows you draw just the vertices, meaning that you'll have a point cloud.

### void drawWireframe() ###
This draws the mesh as GL_LINES, meaning that you'll have a wireframe.

### void drawFaces() ###
This draws the mesh as faces, meaning that you'll have a collection of faces.

### void draw() ###
This draws the mesh using its primitive type, meaning that if you set them up to be triangles, this will draw the triangles.

### virtual ### void draw(ofPolyRenderMode renderType) ###
This draws the mesh using its renderType type, meaning that if you pass OF_PRIMITIVE_TRIANGLES, this will draw the mesh as OF_PRIMITIVE_TRIANGLES, but you may need to alter the indices so that the drawing.
