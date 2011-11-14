
## ofUtils ##

A collection of util methods in openFrameworks that make your life easier.

### int ofNextPow2(int input)###

### void ofResetElapsedTimeCounter()###
// this happens on the first frame

###  float ofGetElapsedTimef()###

### int ofGetElapsedTimeMillis()###

### unsigned long ofGetElapsedTimeMicros()###

### int ofGetFrameNum()###

### int ofGetSeconds()###

### int ofGetMinutes()###

### int ofGetHours()###

### unsigned int ofGetUnixTime() ###
//number of seconds since 1970

### unsigned long ofGetSystemTime( )###
system time in milliseconds

### unsigned long ofGetSystemTimeMicros( )###
system time in microseconds

### string ofGetTimestampString()###

### string ofGetTimestampString(string timestampFormat)###

### int ofGetYear()###

### int ofGetMonth()###

### int ofGetDay()###

### int ofGetWeekday()###

### void ofLaunchBrowser(string url)###

### void ofEnableDataPath()###

### void ofDisableDataPath()###

### string ofToDataPath(string path, bool absolute=false) ###

### void ofRandomize(vector<T>& values) ###

### void ofRemove(vector<T>& values, BoolFunction shouldErase) ###

### void ofSort(vector<T>& values) ###

### int ofFind(const vector<T>& values, const T& target) ###

### bool ofContains(const vector<T>& values, const T& target) ###

### void ofSetDataPathRoot( string root )###
//set the root path that ofToDataPath will use to search for files relative to the app
//the path must have a trailing slash (/) !!!!

### string ofToString(const T& value) ###


### string ofToString(const T& value, int precision) ###

### string ofToString(const vector<T>& values) ###

### string ofToHex(const T& value) ###
 // pretend that the value is a bunch of bytes
 
 // the number of bytes is determined by the datatype
 
 // the bytes are stored backwards (least significant first)
 
  // print each byte out as a 2-character wide hex value
 

###string ofToHex(const string& value) ###

### string ofToHex(const char* value)###

### int ofHexToInt(const string& intHexString)###

### char ofHexToChar(const string& charHexString)###

### float ofHexToFloat(const string& floatHexString)###

### string ofHexToString(const string& stringHexString)###

### int ofToInt(const string& intString)###

### char ofToChar(const string& charString)###

### float ofToFloat(const string& floatString)###

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

### void ofSaveFrame(bool bUseViewport = false)###

### void ofSaveViewport(string filename) ###

### vector <string> ofSplitString(const string & source, const string & delimiter, bool ignoreEmpty = false, bool trim = false)###

### string ofJoinString(vector <string> stringElements, const string & delimiter)###

### void ofStringReplace(string& input, string searchStr, string replaceStr)###

### bool ofIsStringInString(string haystack, string needle)###

### string ofToLower(const string & src) ###

### string ofToUpper(const string & src)###

### string ofVAArgsToString(const char * format, ...)###

### string ofVAArgsToString(const char * format, va_list args)###

