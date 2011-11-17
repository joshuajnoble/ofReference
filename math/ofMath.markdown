[![openFrameworks](http://www.openframeworks.cc/wp-content/themes/ofw/images
/ofw-logo.gif)](http://www.openframeworks.cc/)

[about](http://www.openframeworks.cc/about) /
[setup](http://www.openframeworks.cc/setup) /
[download](http://www.openframeworks.cc/download) /
[addons](http://www.openframeworks.cc/addons) /
[docs](http://www.openframeworks.cc/documentation) /
[gallery](http://www.openframeworks.cc/gallery) /
[community](http://www.openframeworks.cc/community) /
[forum](http://www.openframeworks.cc/forum/) ![new
window](http://www.openframeworks.cc/wp-content/themes/ofw/images/icon-tiny-
open.gif) / [wiki](http://wiki.openframeworks.cc/) ![new
window](http://www.openframeworks.cc/wp-content/themes/ofw/images/icon-tiny-
open.gif) / [rss feeds](http://www.openframeworks.cc/rss-feeds) ![new
window](http://www.openframeworks.cc/wp-content/themes/ofw/images/icon-tiny-
feed.gif)

[Register](http://www.openframeworks.cc/register) / Login

# [documentation](./documentation) : ofMath.h

This document refers to version **0.06**

**Show advanced?**  
[yes](documentation?detail=ofMath&adv=yes) / no

### Functions

ofSeedRandom()

syntax

ofSeedRandom()

description

Seeds the random number generator to the clock time, so that random numbers
will always be different.

[index](documentation) up

ofSeedRandom(...)

syntax

ofSeedRandom(int val)

description

Seeds the random number generator to a value passed in (val) so that random
numbers will always be the same.

[index](documentation) up

ofRandom(...)

syntax

ofRandom(float val0, float val1)

returns

float

Returns a random number between val0 and val1.

description

For example, ofRandom(-30,20) will return a random number between -30 and 20.

[index](documentation) up

ofRandomf()

syntax

ofRandomf()

returns

float

Returns a random number between -1 and 1.

[index](documentation) up

ofRandomuf()

syntax

ofRandomuf()

returns

float

Returns a random number between 0 and 1.

[index](documentation) up

ofNextPow2(...)

syntax

ofNextPow2(int input , )

returns

int

returns the next largest power of 2 number from the input given.

description

eg: for an input of 50 ofNextPow2 will return 64 and for an input of 401 it
will return 512.

[index](documentation) up

ofNormalize(...)

syntax

ofNormalize(float value, float min, float max)

returns

float

Returns the normalized float number.

description

Normalizes a number from a given range (min,max) into a value between 0 and 1.

  
note: we are getting a clamp number between 0 and 1 of "value-min/max-min"

[index](documentation) up

ofMap(...)

syntax

ofMap(float value, float inputMin, float inputMax, float outputMin, float
outputMax)

returns

float

Returns the number in the new range.

description

Re-maps a number from one range to another. We convert the number value where
inputMin < value < inputMax into a number beetween outputMin and outputMax.

e.g:

  

    
      
    
    float x, newx;  
    
    x=5;  
    
    // 0 < x < 10  
    
    newx = ofMap(x, 0, 10, 21, 22) //newx = 21.5 a value between 21 and 22  
    
    

  
  

[index](documentation) up

ofClamp(...)

syntax

ofClamp(float value, float min, float max)

returns

float

If the value is bigger than max clamp function returns max. If value is
smaller than min it returns min. "If min < value < max" it returns value.

description

Restricts a value to be within a specified range defined by values min and
max.

e.g:

  

    
      
    
      
    
    float val, newval;  
    
      
    
    val=10;  
    
      
    
    newval=ofClamp(val,30,40); //newval = 30  
    
      
    
    newval=ofClamp(val,0,5); //newval = 5  
    
      
    
    newval=ofClamp(val,0,20); //newval = 10  
    
      
    
    

  
  
  
  
  
  
  

[index](documentation) up

ofLerp(...)

syntax

ofLerp(float start, float stop, float amt)

returns

float

Returns a number between start and stop.

description

Calculates a number between two numbers (start,stop) at a specific increment
(amt).

If we want the new number to be between start,stop numbers amp needs to be a
number between 0 and 1.

e.g:

    
      
    
    float init,end,increment,result;  
    
    increment=0.2;  
    
    init = 1;  
    
    end =2;  
    
    result=ofLerp(init, end, increment); //result = 1.2  
    
      
    
    //We are doing init+increment*(end-init)  
    
    

[index](documentation) up

ofDist(...)

syntax

ofDist(float x1, float y1, float x2, float y2 )

returns

float

Returns the distance between two points. Points are defined by parameters
x1,y1 for the first point and x2,y2 for the second point.

[index](documentation) up

ofDistSquared(...)

syntax

ofDistSquared(float x1, float y1, float x2, float y2 )

returns

float

Returns the square of the distance between two points. Points are defined by
parameters x1,y1 for the first point and x2,y2 for the second point.

[index](documentation) up

ofSign(...)

syntax

ofSign(float n )

returns

int

Returns 1 if the value n is bigger than zero. Returns -1 if n is smaller than
0 and returns zero if n is zero.

[index](documentation) up

ofInRange(...)

syntax

ofInRange(float t, float min, float max)

returns

bool

Returns true if the value t is in between min and max values.

[index](documentation) up

ofRadToDeg(...)

syntax

ofRadToDeg(float radians)

returns

float

Returns the converted value of a radians angle in degrees.

description

Convert an angle value expressed in Radians into an angle in Degrees. For
example if we call this function for radians=PI/2 we obtain 90.

[index](documentation) up

ofDegToRad(...)

syntax

ofDegToRad(float degrees)

returns

float

Returns the converted value of a degrees angle in radians.

description

Convert an angle value expressed in Degrees into an angle in Radians. For
example if we call this function for degrees=90 we obtain PI/2.

[index](documentation) up

ofRandomWidth()

syntax

ofRandomWidth()

returns

float

Returns a value between 0 and the width of the screen.

[index](documentation) up

ofRandomHeight()

syntax

ofRandomHeight()

returns

float

Returns a value between 0 and the height of the screen.

[index](documentation) up

