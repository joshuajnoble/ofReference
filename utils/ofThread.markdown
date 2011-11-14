## ofThread ##

### ofThread() ### 

### virtual ~ofThread() ### 

### virtual ofThread() ### 

### bool isThreadRunning() ### 

### void startThread(bool _blocking = true, bool _verbose = true) ### 

### bool lock() ### 

### bool unlock() ### 

### void stopThread(bool close = true) ### 

### void waitForThread(bool stop = true) ### 

### virtual void threadedFunction() ### 
you need to overide this with the function you want to thread



### myThread ###
HANDLE or pthread_t

### ofMutex mutex ### 

### bool threadRunning ### 

### bool blocking ### 

### bool verbose ### 

