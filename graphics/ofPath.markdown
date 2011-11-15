ofPath() ###

### void clear() ###

### void newSubPath() ###
// creates a new subpath

### void close() ###
// closes current path, next command starts a new one

### void lineTo(const ofPoint & p) ###
### void lineTo(float x, float y) ###
### void lineTo(float x, float y, float z) ###

### void moveTo(const ofPoint & p) ###
// starts a new subpath with current parameters for winding, stroke, fill...
// the new subpath starts in p

### void moveTo(float x, float y, float z=0) ###

### void curveTo(const ofPoint & p) ###
### void curveTo(float x, float y) ###
### void curveTo(float x, float y, float z) ###

### void bezierTo(const ofPoint & cp1, const ofPoint & cp2, const ofPoint & p) ###
### void bezierTo(float cx1, float cy1, float cx2, float cy2, float x, float y) ###
### void bezierTo(float cx1, float cy1, float cz1, float cx2, float cy2, float cz2, float x, float y, float z) ###

### void quadBezierTo(const ofPoint & cp1, const ofPoint & cp2, const ofPoint & p) ###
### void quadBezierTo(float cx1, float cy1, float cx2, float cy2, float x, float y) ###
### void quadBezierTo(float cx1, float cy1, float cz1, float cx2, float cy2, float cz2, float x, float y, float z) ###

### void arc(const ofPoint & centre, float radiusX, float radiusY, float angleBegin, float angleEnd) ###
### void arc(float x, float y, float radiusX, float radiusY, float angleBegin, float angleEnd) ###
### void arc(float x, float y, float z, float radiusX, float radiusY, float angleBegin, float angleEnd) ###

### void setPolyWindingMode(ofPolyWindingMode mode) ###
### void setFilled(bool hasFill) ###
// default true

### void setStrokeWidth(float width) ###
// default 0

### void setColor( const [ofColor](../types/ofColor.htm)& color ) ###
### void setHexColor( int hex ) ###
### void setFillColor(const [ofColor](../types/ofColor.htm) & color) ###
### void setFillHexColor( int hex ) ###
### void setStrokeColor(const [ofColor](../types/ofColor.htm) & color) ###
### void setStrokeHexColor( int hex ) ###


### ofPolyWindingMode getWindingMode() const ###
### bool isFilled() const ###
// default true

### [ofColor](../types/ofColor.htm) getFillColor() const ###
### [ofColor](../types/ofColor.htm) getStrokeColor() const ###
### float getStrokeWidth() const ### // default 0
### bool hasOutline() const ###

### void draw(float x, float y) ###
### void draw() ###

### vector<ofSubPath> & getSubPaths() ###
Returns all the sub paths that the ofPath contains.

### const vector<ofSubPath> & getSubPaths() const ###

### vector<[ofPolyline](../graphics/ofPolyline.htm)> & getOutline() ###
### ofMesh & getTessellation() ###

### void simplify(float tolerance=0.3) ###

### void flagShapeChanged() ###
// only needs to be called when path is modified externally

### void setMode(Mode mode) ###

### void setCurveResolution(int curveResolution) ###
### int getCurveResolution() ###

### void setArcResolution(int res) ###
### int getArcResolution() ###

### void setUseShapeColor(bool useColor) ###
### bool getUseShapeColor() ###

### void tessellate() ###

### void translate(const ofPoint & p) ###
### void rotate(float az, const ofVec3f& axis ) ###
### void scale(float x, float y) ###

## Mode ##

### PATHS ###
### POLYLINES ###