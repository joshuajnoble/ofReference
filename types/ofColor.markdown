
## ofColor ##

ofColor represents a color in openFrameworks and enables a lot of extra functionality like using RGB or HSB color spectrums, lerping or linearly interpolating between colors, or inverting colors, among other things. You're probably familiar with RGB colors already, but HSB is a big part of ofCOlor and it uses a hue value between 0 and 360 to determine what the hue of a color will be:

![HSB](../types/hsb.png)

The saturation determines how much of the hue versus white is present and brightness determines how much hue versus black is present:

![SB](../types/hsb-cone.jpg)

ofColor is templated, which means that it has several different ways it can be created. These are probably best to leave as they are because there's already a few kinds type-deffed for you. You can make an ofFloatColor if you want to work with floating point numbers, ofShortColor if you want to work with ints, or the default ofColor, which uses unsigned char values.

### ofColor_<PixelType>

This is either ofColorShort(), ofColorFloat() or ofColor, or, if you're up to something crazy, ofColor_<type>.

### ofColor_<PixelType> (float _r, float _g, float _b, float _a = 255.0f) ###

This creates a color using RGB

### ofColor_<PixelType> (const ofColor_<PixelType> & color) ###

This copies a color:

```cpp
ofColor mom(255, 0, 0);
ofColor c(mom);
```

### ofColor_<PixelType> (const ofColor_<PixelType> & color, float _a) ###

```cpp
ofColor mom(255, 0, 0);
ofColor c(mom, 122); // now c is 50% alpha red
```

### ofColor_<PixelType> (float gray, float _a = 255.0f) ###

```cpp
ofColor c(0.5, 122); // now c is 50% alpha gray, ooh, dismal
```

### ofColor_<PixelType> (const ofColor_<SrcType> & color) ###

```cpp
ofColor mom(255, 0, 0);
ofColor c(mom, 122); // now c is 50% alpha red
```

### static ofColor_<PixelType> fromHsb (float hue, float saturation, float brightness, float alpha = 255.f) ###

Allows you create a color from HSB settings. Important to note is that h is between 0 and 360, while s and b are between 0 and 1. The f

### static ofColor_<PixelType> fromHex (int hexColor, float alpha = 255.f) ###

This allows you to create a color from a hexadecimal value like 0xffffff (white) or oxff000088 (red with 1/2 alpha). You get an ofColor instance back from the method so you can use it like:

```cpp
ofColor yellow = ofColor::fromHex(0xffff00);
ofColor halfYellow = ofColor::fromHex(0xffff00, 122);
```

### static const ofColor_<PixelType> gray ###

A color that you can use in your OF application.

### static const ofColor_<PixelType> white ###

A color that you can use in your OF application.

### static const ofColor_<PixelType> red ###

A color that you can use in your OF application.

### static const ofColor_<PixelType> green ###

A color that you can use in your OF application.

### static const ofColor_<PixelType> blue ###

A color that you can use in your OF application.

### static const ofColor_<PixelType> cyan ###

A color that you can use in your OF application.

### static const ofColor_<PixelType> magenta ###

A color that you can use in your OF application.

### static const ofColor_<PixelType> yellow ###

A color that you can use in your OF application.

### static const ofColor_<PixelType> black ###

A color that you can use in your OF application.

### void set (float _r, float _g, float _b, float _a = 255.0f) ###

Set a color using RGB.

```cpp
ofColor c(255, 0, 0); // red
```

### void set (float _gray, float _a = 255.0f) ###

Grayscale, for the emo among us.

```cpp
ofColor c(0.5, 122); // now c is 50% alpha gray
```

### void set (ofColor_<PixelType> const & color) ###



### void setHex (int hexColor, float alpha = 255.0f) ###
### int getHex () const ###

Gets the value of the color as RGB hex, so for instance, 0xffff00, which would be yellow. Usually when we look at these colors in print they're hex, so don't be surprised if they don't look familiar when you print them as decimal.

### ofColor_<PixelType>& clamp () ###

This clamps the values of your color in case they're too high or low for their types, in case you go negative or too use values that are too high, like anything >255.0.

### ofColor_<PixelType>& invert () ###

Flips your color. You probably can guess what this looks like.

### ofColor_<PixelType>& normalize () ###

The following

```cpp
	ofColor c(122, 122, 0);
	ofSetColor(c);
	ofCircle(100, 100, 100);
	c.normalize();
	ofSetColor(c);
	ofCircle(300, 100, 100);
```

will create this:

![ofNorm](../types/ofNormalize.png)



### ofColor_<PixelType>& lerp(const ofColor_<PixelType>& target, float amount) ###

This awesome method allows you set a color based on a another color and the amount of that color that you want it to be set to, so for instance, if you had red and wanted halfway between red and blue, you could do this:

```cpp
ofColor r = ofColor::red;
ofColor b = ofColor::blue;
b.lerp(r, 0.5); // now purple!
```

### ofColor_<PixelType> getClamped () const ###

Returns the clamped version of the color.

### ofColor_<PixelType> getInverted () const ###

Returns the inverted version of the color.

### ofColor_<PixelType> getNormalized () const ###

Returns the normalized version of the color.

### ofColor_<PixelType> getLerped(const ofColor_<PixelType>& target, float amount) const ###

Returns the lerped version of the color so you can make a new color from it, which is fun.

### float getHue () const ###

Gets the hue of the color, between 0 and 360

### float getSaturation () const ###

Gets the saturation of the color, between 0 and 1, that is, how much hue there is. No saturation and full brightness = white.

### float getBrightness () const ###

Gets the brightness of the color, that is, how black it is. No brightness = black.

### float getLightness () const ###

creates average of the components

### void getHsb(float& hue, float& saturation, float& brightness) const ###

### void setHue (float hue) ###

Sets the hue. Note the color wheel at the top. Hue values are from 0 to 360.0.

### void setSaturation (float saturation) ###

Sets the saturation, note the color, em, diamond at the top. Saturation values are 0 to 1.0

### void setBrightness (float brightness) ###

Sets the brightness, note the color gem at the top. Saturation values are 0 to 1.0

### void setHsb(float hue, float saturation, float brightness, float alpha) ###

Sets the HSB all at once, with alpha included.

### void setHsb(float hue, float saturation, float brightness) ###

Sets the HSB all at once, no need for alpha.

### ofColor_<PixelType> & operator = (ofColor_<PixelType> const & color) ###

Operator overloading for a color, so you can do:

```cpp
ofColor newRed = ofColor::red;
```

### ofColor_<PixelType> & operator = (ofColor_<SrcType> const & color) ###

Operator overloading for a color, so you can do:

```cpp
ofColor newRed = ofColor::red;
```

### ofColor_<PixelType> & operator = (float const & val) ###

### bool operator == (ofColor_<PixelType> const & color) ###

### bool operator != (ofColor_<PixelType> const & color) ###

### ofColor_<PixelType> operator + (ofColor_<PixelType> const & color) const ###

### ofColor_<PixelType> operator + (float const & val) const ###

### ofColor_<PixelType> & operator += (ofColor_<PixelType> const & color) ###

### ofColor_<PixelType> & operator += (float const & val) ###

### ofColor_<PixelType> operator - (ofColor_<PixelType> const & color) const ###

### ofColor_<PixelType> operator - (float const & val) const ###

### ofColor_<PixelType> & operator -= (ofColor_<PixelType> const & color) ###

### ofColor_<PixelType> & operator -= (float const & val) ###

### ofColor_<PixelType> operator * (ofColor_<PixelType> const & color) const ###

### ofColor_<PixelType> operator * (float const & val) const ###

### ofColor_<PixelType> & operator *= (ofColor_<PixelType> const & color) ###

### ofColor_<PixelType> & operator *= (float const & val) ###

### ofColor_<PixelType> operator / (ofColor_<PixelType> const & color) const ###

### ofColor_<PixelType> operator / (float const & val) const ###

### ofColor_<PixelType> & operator /= (ofColor_<PixelType> const & color) ###

### ofColor_<PixelType> & operator /= (float const & val) ###

### const PixelType & operator [] (int n) const ###

Gives you access to the color as an array:

[0] = r
[1] = g
[2] = b
[3] = a

### PixelType & operator [] (int n) ###

Gives you access to the color as an array:

[0] = r
[1] = g
[2] = b
[3] = a


### typedef ofColor_<unsigned char> ofColor ###
### typedef ofColor_<float> ofFloatColor ###
### typedef ofColor_<unsigned short> ofShortColor ###
