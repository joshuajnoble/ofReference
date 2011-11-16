
## ofUtils ##

A collection of util methods in openFrameworks that make your life easier.

### int ofNextPow2(int input)###

### void ofResetElapsedTimeCounter()###
// this happens on the first frame

###  float ofGetElapsedTimef()###

### int ofGetElapsedTimeMillis()###

returns the amount of elapsed time, in milliseconds since the app started
(1000 = 1 second)

### unsigned long ofGetElapsedTimeMicros()###

### int ofGetFrameNum()###

Returns the number of frames since the app started.

### int ofGetSeconds()###

Returns the system time's seconds (0-59).

### int ofGetMinutes()###

Returns the system times's minutes (0-59).

### int ofGetHours()###

Returns the system time's hours (0-23).

### unsigned int ofGetUnixTime() ###
number of seconds since 1970

### unsigned long ofGetSystemTime( )###
system time in milliseconds

### unsigned long ofGetSystemTimeMicros( )###
system time in microseconds

### string ofGetTimestampString()###

### string ofGetTimestampString(string timestampFormat)###

### int ofGetYear()###
Get the year as an int, 2011 for example

### int ofGetMonth()###
Get the month as an int, 0 = Sunday, 11 = Saturday

### int ofGetDay()###
depending on local zone, Get the day as an int, 0 = Sunday, 6 = Saturday


### int ofGetWeekday()###
depending on local zone, 0 - sun .. 6 sat or 0 - mon .. 6 sun

### void ofLaunchBrowser(string url)###
Opens your computer's default browser and loads the specified url.

### void ofEnableDataPath()###

### void ofDisableDataPath()###

### string ofToDataPath(string path, bool absolute=false) ###
Returns the 


### void ofRandomize(vector<T>& values) ###
Randomize the values in the vector

### void ofRemove(vector<T>& values, BoolFunction shouldErase) ###

### void ofSort(vector<T>& values) ###
Sorts the vector of values according to the default std::sort().

### int ofFind(const vector<T>& values, const T& target) ###
Finds the target in the vector of values.

### bool ofContains(const vector<T>& values, const T& target) ###

### void ofSetDataPathRoot( string root )###
//set the root path that ofToDataPath will use to search for files relative to the app
//the path must have a trailing slash (/) !!!!

### string ofToString(const T& value) ###


To make adding numbers to a string easy we have the ofToString object which
takes a number and turns it into a string representation of that number. For
floating point numbers 'precision' is the number of decimal places you want to
use. There is a default value for 'precision' of 7 decimal places, so if you
don't wish to specifiy it you can just pass the first argument.
  
This example makes a custom string to show the framerate in the window title.
      
```cpp
    string str = "framerate is "; 						  
    
    str += ofToString(ofGetFrameRate(), 2)+"fps";   
    
    ofSetWindowTitle(str);  
    
    //set the window title to "framerate is 45.30fps"  
```

### string ofToString(const T& value, int precision) ###

### string ofToString(const vector<T>& values) ###

### string ofToHex(const T& value) ###
pretend that the value is a bunch of bytes 
the number of bytes is determined by the datatype
the bytes are stored backwards (least significant first)
print each byte out as a 2-character wide hex value
 

###string ofToHex(const string& value) ###
Converts a string to a hex string.

### string ofToHex(const char* value)###

### int ofHexToInt(const string& intHexString)###
Converts a hex string to an integer.

### char ofHexToChar(const string& charHexString)###
Converts a char string of hex numbers to an integer.

### float ofHexToFloat(const string& floatHexString)###

### string ofHexToString(const string& stringHexString)###

### int ofToInt(const string& intString)###
Returns the converted int value.

### char ofToChar(const string& charString)###

### float ofToFloat(const string& floatString)###
Converts the string "floatString" into a float value.

### bool ofToBool(const string& boolString)###

### string ofToBinary(const T& value) ###

### string ofToBinary(const string& value)###

### string ofToBinary(const char* value)###

### int ofBinaryToInt(const string& value)###

### char ofBinaryToChar(const string& value)###

### float ofBinaryToFloat(const string& value)###

### string ofBinaryToString(const string& value)###

### string ofGetVersionInfo()###

### void ofSaveScreen(string filename)###

Saves the current screen image into a given file name (string filename).

Example:

    
      
```cpp
    string filename;  
    
    fileName = "screen1.png";  
    
    ofSaveScreen(fileName);  
```
    

### void ofSaveFrame(bool bUseViewport = false)###

Similar to save scrren, except that it allows you use the current viewport in case you have an [ofCamera](../3d/ofCamera.htm) instance

### void ofSaveViewport(string filename) ###

### vector <string> ofSplitString(const string & source, const string & delimiter, bool ignoreEmpty = false, bool trim = false)###


This function is used to delete some parts of a given string (str). We set in
delimiter the parts we want to delete. For example if we call ofSplitSpring in
my setup function:

    
      
    
    result=ofSplitString("of rocks", "of");  
    
    

  
we obtain:

result[0]=r

result[1]=cks

this is the result of deleting o and f letters in the string.

  
We can find a very useful application if we use delimiter = " ":

    
      
    
    result=ofSplitString("of rocks", " ");  

### string ofJoinString(vector <string> stringElements, const string & delimiter) ###

### void ofStringReplace(string& input, string searchStr, string replaceStr) ###

### bool ofIsStringInString(string haystack, string needle) ###
Similar to the way that you do str.find("somestring") in some other languages.

### string ofToLower(const string & src) ###
Returns the string to lower case characters. 

### string ofToUpper(const string & src) ###
Returns the string to upper case characters. 

### string ofVAArgsToString(const char * format, ...) ###
Allows you return the vaargs to a function that takes vaargs as a string, so for instance with the following function:

```cpp
void check(int val, ...) {
	ofVAArgsToString("%i", ...);
}
```
You could use ofVAArgsToString()

```cpp
check(9, 10, 11); // would print 10, 11
```

### string ofVAArgsToString(const char * format, va_list args) ###

