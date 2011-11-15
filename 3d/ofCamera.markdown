## ofCamera() ##

ofCamera provides a camera onto a 3D scene. Some of the different properties of the camera are shown in the picture below:

![FOV](/fov.gif)

The far and near clip planes are the boundaries of what's visible in the camera. If you need more information on these, check http://www.falloutsoftware.com/tutorials/gl/gl0.htm

### void setFov(float f) ###
Here you can set the field of view of the camera.

### void setNearClip(float f) ###
This sets the near clip plane.

### void setFarClip(float f) ###
Sets the far clip plane

### void enableOrtho() ###
Orthographic, or parallel, projections consist of those that involve no perspective correction. There is no adjustment for distance from the camera made in these projections, meaning objects on the screen will appear the same size no matter how close or far away they are. Calling enableOrtho() sets the ofCamera to orthographic mode.

### void disableOrtho() ###
Calling disableOrtho() turns off the orthographic mode.

### bool getOrtho() const ###
Get whether the camera is in orthographic mode.

### float getImagePlaneDistance([ofRectangle](types/ofRectangle.htm) viewport = ofGetCurrentViewport()) const ###
This allows you to get the image plane distance from any viewport passed in. By default this is the current viewport, but it can be whatever you find useful.

### virtual void begin([ofRectangle](types/ofRectangle.htm) viewport = ofGetCurrentViewport()) ###
set the matrices that the camera will use.

### virtual void end() ###
set the matrices

### void cacheMatrices(bool cache=true) ###
This caches the projection matrix for the ofCamera.

### ofMatrix4x4 getProjectionMatrix(ofRectangle viewport = ofGetCurrentViewport()) ###	
Access to the projection matrix.

### ofMatrix4x4 getModelViewMatrix() ###
Access to the projection matrix.

### ofMatrix4x4 getModelViewProjectionMatrix(ofRectangle viewport = ofGetCurrentViewport()) ###
Access to the projection ModelViewProjectionMatrix.

### ofVec3f worldToScreen(ofVec3f WorldXYZ, ofRectangle viewport = ofGetCurrentViewport()) ### 
When you have a position in world coordinates you can get what it would be in world coordinates, transforming it using the ofCamera.

### ofVec3f screenToWorld(ofVec3f ScreenXYZ, ofRectangle viewport = ofGetCurrentViewport()) ###
When you have a position in screen coordinates you can get what it would be in world coordinates, transforming it using the ofCamera.

### ofVec3f worldToCamera(ofVec3f WorldXYZ, ofRectangle viewport = ofGetCurrentViewport()) ###
When you have a position in world coordinates you can get what it would be in camera coordinates, transforming it using the ofCamera.

### ofVec3f cameraToWorld(ofVec3f CameraXYZ, ofRectangle viewport = ofGetCurrentViewport()) ###
When you have a position in camera coordinates you can get what it would be in world coordinates, transforming it using the ofCamera.
