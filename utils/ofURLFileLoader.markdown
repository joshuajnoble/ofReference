
## ofHttpRequest ##

### ofHttpRequest()  ### 

### ofHttpRequest(string url,string name,bool saveTo=false) ### 

### 	string				url ### 
### string				name ### 
### bool				saveTo ### 


## ofHttpResponse ##

### 	ofHttpResponse()  ### 

### ofHttpResponse(ofHttpRequest request,const ofBuffer & data,int status, string error)  ### 

### 	ofHttpResponse(ofHttpRequest request,int status,string error)  ### 

### operator ofBuffer&()  ### 


## ofURLFileLoader ##
extends [ofThread](../utils/ofThread.htm) 

### ofURLFileLoader() ### 

### ofHttpResponse get(string url) ### 

### int getAsync(string url, string name="") ### 
returns id

### ofHttpResponse saveTo(string url, string path) ### 

### int saveAsync(string url, string path) ### 

### void remove(int id) ### 

### void clear() ### 

### void threadedFunction() ### 

### void start() ### 

### void stop() ### 

### void update(ofEventArgs & args) ### 

## ofURLFileLoader ##

### ofHttpResponse ofLoadURL(string url) ###

### int ofLoadURLAsync(string url, string name="") ###
returns id

### ofHttpResponse ofSaveURLTo(string url, string path) ###

### int ofSaveURLAsync(string url, string path) ###

### void ofRemoveURLRequest(int id) ###

### void ofRemoveAllURLRequests() ###

### void ofRegisterURLNotification(T * obj) ### 

### void ofUnregisterURLNotification(T * obj) ### 
