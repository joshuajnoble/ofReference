#pragma once

#include "ofConstants.h"
#include "ofFileUtils.h"
#include "ofTypes.h"

### ofLogLevel ###
	OF_LOG_VERBOSE,
	OF_LOG_NOTICE,
	OF_LOG_WARNING,
	OF_LOG_ERROR,
	OF_LOG_FATAL_ERROR,
	OF_LOG_SILENT	// this one is special and should always be last,
					// set ofSetLogLevel to OF_SILENT to not recieve any messages
}

### void ofSetLogLevel(ofLogLevel logLevel) ###
### void ofSetLogLevel(string module, ofLogLevel logLevel) ###
### ofLogLevel ofGetLogLevel() ###

### void ofSetLoggerChannel(ofPtr<ofBaseLoggerChannel> loggerChannel) ### 
### string ofGetLogLevelName(ofLogLevel level) ### 

### void ofLogToFile(const string & path, bool append=false) ### 
### void ofLogToConsole() ### 

## ofLog ##
    
		/// use the default log level
		ofLog();
		
		/// set the log level
		ofLog(ofLogLevel logLevel);
		
		/// the legacy ofLog interfaces
		ofLog(ofLogLevel logLevel, const string & message);
		ofLog(ofLogLevel logLevel, const char* format, ...);

        ### virtual ~ofLog(); ###
        /// does the actual printing when the ostream is done

		### ofLog& operator<<(const T& value) ###
		/// catch the << ostream with a template class to read any type of data

        ### ofLog& operator<<(std::ostream& (*func)(std::ostream&))  ###
        /// catch the << ostream function pointers such as std::endl and std::hex

        ###  void setChannel(ofPtr<ofBaseLoggerChannel> channel) ### 
		
	protected:
		 ### ofLogLevel level;			///< log level ### 
		 ### bool bPrinted;				///< has the msg been printed in the constructor?   ### 
		 ### string module  ### 

	
		/// print a log line
		 ### void _log(ofLogLevel level, const string & module, const string & message)  ### 
		 ### bool checkLog(ofLogLevel level, const string & module)  ### 

	private:
        std::ostringstream message;	///< temp buffer
		
		ofLog(ofLog const&) {}        					// not defined, not copyable
        ofLog& operator=(ofLog& from) {return *this;}	// not defined, not assignable

        static ofPtr<ofBaseLoggerChannel> channel;
};


## class ofLogVerbose ##
 ofLog
 ### 		ofLogVerbose(const string &module="OF")  ### 
	 ### 	ofLogVerbose(const string & module, const string & message)  ### 


## ofLogNotice ##
 public ofLog{

 ### 		ofLogNotice(const string & module="OF")  ### 
	 ### 	ofLogNotice(const string & module, const string & message)  ### 
};

## ofLogWarning ##
ofLog{

 ### 		ofLogWarning(const string & module="OF")  ### 
	 ### 	ofLogWarning(const string & module, const string & message)  ### 

## ofLogError ##
 ofLog

 ### 		ofLogError(const string & module="OF")  ### 
		 ### ofLogError(const string & module, const string & message)  ### 
};

## ofLogFatalError ##
ofLog

 ### 		ofLogFatalError(const string & module="OF")  ### 
		 ### ofLogFatalError(const string & module, const string & message)  ### 
};

## ofBaseLoggerChannel ##

 ### 	virtual ~ofBaseLoggerChannel(){};
	 ### virtual void log(ofLogLevel level, const string & module, const string & message)=0  ### 
	 ### virtual void log(ofLogLevel logLevel, const string & module, const char* format, ...)=0  ### 
	 ### virtual void log(ofLogLevel logLevel, const string & module, const char* format, va_list args)=0  ### 
};

## ofConsoleLoggerChannel ## 

 ### 	virtual ~ofConsoleLoggerChannel(){}; ### 
	 ### void log(ofLogLevel level, const string & module, const string & message)  ### 
	 ### void log(ofLogLevel logLevel, const string & module, const char* format, ...)  ### 
	 ### void log(ofLogLevel logLevel, const string & module, const char* format, va_list args)  ### 
};

## ofFileLoggerChannel ##
ofBaseLoggerChannel

	 ### ofFileLoggerChannel(); ### 
	 ### ofFileLoggerChannel(const string & path, bool append); ### 
	 ### virtual ~ofFileLoggerChannel();  ### 

	 ### void setFile(const string & path,bool append=false); ### 

	 ### void log(ofLogLevel level, const string & module, const string & message); ### 
	 ### void log(ofLogLevel logLevel, const string & module, const char* format, ...); ### 
	 ### void log(ofLogLevel logLevel, const string & module, const char* format, va_list args); ### 

	 ### void close()  ### 

