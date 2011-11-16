
## ofTrueTypeFont ##

The ofTrueTypeFont class provides an interface to load fonts into openframeworks. The fonts are converted to textures, and can be drawn on screen. There are some options when you load the font - what size the font is rendered at, wether or not it is anti-aliased, and wether the font object will be the full character set or a subset (ie, extended ascii, which can include accents, umlauts, or normal ascii). The default is anti-aliased, non-full character set. The library uses freetype, which has certain patent problems in regards to true type hinting, especially at small sizes, so non-anti-aliased type doesn't always render beautifully. But we find it quite adequate, and at larger sizes it seems to works well.

### void loadFont(string filename, int fontsize) ###

description Loads a fonts of a given filename in, and renders it to a texture at a given size (fontsize). It will look for the font file in the data/ folder. For example, to load the font arial at type size 32:


```cpp
ofFont myFont;
myFont.loadFont("arial.ttf", 32);
```

### void loadFont(string filename, int fontsize, bool _bAntiAliased, bool _bFullCharacterSet, bool makeContours) ###

This loads a font, but in addition to setting the font name and size, you can also pass in two flags: is this font antiAliased, and whether it includes the full character set.

### float getLineHeight() ###

Returns a float, which is the line height for the type face. description The line height is computed, based on the font size, and can be adjusted. Useful if you are print multi-line text. 

### void setLineHeight(float height) ###

description Sets the line height for text that is drawn on screen. stringWidth(...) 

### float stringWidth(string s) ###

Returns this width, in pixels, for a given string drawn with that typeface. description stringHeight(...) 

### float stringHeight(string s) ###

Returns the height, in pixels, for a given string drawn with that typeface. 

###ofRectangle getStringBoundingBox(string s, float x, float y) ###

Returns an ofRectangle wich is the Bounding Box containing our TrueTypeFont This rectangle depends on the TruTypeFont size. description e.g:

```cpp
//in setup() 
franklinBook.loadFont("frabk.ttf", 32);

//in update()
char tempString[255];
ofRectangle rect = franklinBook.getStringBoundingBox(tempString, 0,0);
//in draw
ofSetColor(0xcccccc);

ofRect(rect.x, rect.y, rect.width, rect.height);
````

### void drawString(string s, float x, float y) ###
description Draws a string with that typeface, on screen, at point(x,y). For example, you can write some text on screen like this:

```cpp
// in the h file:
ofFont myfont;

// in setup:
myfont.loadFont("arial.ttf", 32);

// in draw:
myfont.drawString("hi!!", 100,100);
```

Your strings can even be multiline:

```cpp
myfont.drawString("a test of multiline text", 300,300);
```

you can also using dynamically generated strings. For example, to print the frame rate:

```
string fpsStr;
fpsStr <<  "frame rate" << ofGetFrameRate();
myfont.drawString(fpsStr, 100,100);
```

### void drawStringAsShapes(string s, float x, float y) ###
description drawStringAsShapes function draws the s string as if it was a geometrical shapes using the information contained in ofTTFContour and ofTTFCharacter. Parameters x and y sets the position of the shape. 

### ofTTFCharacter getCharacterAsPoints(int character) ###
Returns ofTTFCharacter object used by ofTrueTypeFont. Basically contains geometrical information of ofPoints that define diferent ofTrueTypeFont content (strings with a certain format). 

### bool bLoadedOk ###

bLoadedOk is a boolean variable containing true if the font was successfully loaded. bAntiAlised ofTrueTypeFont::bAntiAlised type bool description A variable which tells you if the font is antiAliased. 

### bool bFullCharacterSet ###

A variable which tells you if the font contains the full character set, or a subset. nCharacters ofTrueTypeFont::nCharacters type int description nCharacters contains the number of characters that our font has. 

## ofTTFContour ##

ofTTFContour contains a vector of ofPoints defining the type contour.

### vector<ofPoint> pts ###

## ofTTFCharacter ##

ofTTFCharacter contain a vector with all the ofTTFContour.

## ofTTFCharacter Variables ##

### vector<ofTTFContour> contours ###