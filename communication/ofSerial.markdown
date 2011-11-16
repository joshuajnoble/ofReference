
## ofSerial

ofSerial provides a cross platform system for interfacing with the serial
port. You can choose the port and baud rate, and then read and send data.
Please note that the port must be set manually in the code, so you should be
clear what port your device is on. For example, Arduino users should check the
arduino app to see what port their device is on. Alternatively the ofSerial
class can attempt to communicate with the first available device it finds.


void enumerateDevices()

Prints out the available serial devices:

On mac and linux it might list something like this:

    
      
```cpp    
    device 0 - cu.modem   
    
    device 1 - cu.USA19H181P1.1  
```
    

  
and on a pc, like:

```cpp 
    device 0 - COM2   
    
    device 1 - COM4  
    
    

### void close()

description

Closes the connection to the serial device.



### bool setup()

Returns true if successful and false if setup fails.

Attempts to setup the first available device at a baud rate of 9600.

    
      
```cpp
    ofSerial mySerial;  
    
    if( mySerial.setup() ){  
    
    	printf("serial is setup!  
    
    ");	  
    
    } 
``` 
    
    

### bool setup(string portName, int baudrate)

Opens the serial port, with the given name and baud rate. On mac and linux, it
might look like:

    
      
```cpp    
    ofSerial mySerial;  
    
    mySerial.setup("/dev/cu.USA19H181P1.1", 9600);  
    
```

  
and on a pc, like:

```cpp 
      
    
    ofSerial mySerial;  
    
    mySerial.setup("COM4", 9600);  
```
    



### bool setup(int deviceNumber, int baudrate)

description

Returns true if successful and false if setup fails. Opens the serial port based on the order in which is listed and sets the baud
rate. The code bellow would open the first serial device found by the system:

    
      
```cpp
    ofSerial mySerial;  
    
    mySerial.setup(0, 9600);  
```

### int readBytes(unsigned char * buffer, int length)

Returns an int value telling the number of bytes that have been read, or
OF_SERIAL_NO_DATA if no data was available, or OF_SERIAL_ERROR if an error
occurred during reading.
Tries to read 'length' bytes from the connected serial device. In some cases
it may read less than 'length' bytes, so for reliable reading of >1 bytes of
data the return value must be checked against the number of bytes requested,
and if fewer bytes than requested were read then the call must be tried again.

  
This function should only be called when Serial.available() is reporting >0
bytes available.

  
An example of how to reliably read 8 bytes:

```cpp
    // we want to read 8 bytes  
    
    int bytesRequired = 8;  
    
    unsigned char bytes[bytesRequired];  
    
    int bytesRemaining = bytesRequired;  
    
    // loop until we've read everything  
    
    while ( bytesRemaining > 0 )  
    
    {  
    
      // check for data  
    
      if ( serial.available() > 0 )  
    
      {  
    
        // try to read - note offset into the bytes[] array, this is so  
    
        // that we don't overwrite the bytes we already have  
    
        int bytesArrayOffset = bytesRequired - bytesRemaining;  
    
        int result = serial.readBytes( &bytes;[bytesArrayOffset],  
    
          bytesRemaining );  
    
      
    
        // check for error code  
    
        if ( result == OF_SERIAL_ERROR )  
    
        {  
    
          // something bad happened  
    
          ofLog( OF_LOG_ERROR, "unrecoverable error reading from serial" );  
    
          // bail out  
    
          break;  
    
        }  
    
        else if ( result == OF_SERIAL_NO_DATA )  
    
        {  
    
          // nothing was read, try again  
    
        }  
    
        else  
    
        {  
    
          // we read some data!  
    
          bytes_remaining -= result;  
    
        }  
    
      }  
    
    }  
```
    
### int writeBytes(unsigned char * buffer, int length)

Returns number of bytes written, or OF_SERIAL_ERROR if an error occured.

Writes a string of bytes to the connected serial device. As with readBytes()
the return code should be checked and the call to writeBytes() repeated with
the remaining data until all bytes have been written.

    
      
```cpp    
    ofSerial mySerial;  
    
    mySerial.setup(0, 9600);  
    
    int numSent = mySerial.writeBytes("Hello World");  
    
    // numSent is how many bytes written; for example if numSent   
    
    // is 3 then "Hel" has been written and the call should be retried  
    
    // with "lo World" to complete the write.  
```
    

### bool writeByte(unsigned char singleByte)

Returns true if successful. Writes a single byte to the connected serial device. Check the return value to
be sure the data was written.

    
```cpp
    
    ofSerial mySerial;  
    
    mySerial.setup(0, 9600);  
    
    unsigned char myByte = 225;  
    
    bool byteWasWritten = mySerial.writeByte(myByte);  
    
    if ( !byteWasWritten )  
    
      printf("byte was not written to serial port");  
    
```   

  
### int readByte()

Returns a single byte, or OF_SERIAL_NO_DATA if no data was read, or
OF_SERIAL_ERROR if an error occurred.


Reads and returns a single byte from the requested device.

    
```cpp    
    
    ofSerial mySerial;  
    
    mySerial.setup(0, 9600);  
    
    int myByte = 0;  
    
    myByte = mySerial.readByte();  
    
    if ( myByte == OF_SERIAL_NO_DATA )  
    
      printf("no data was read");  
    
    else if ( myByte == OF_SERIAL_ERROR )  
    
      printf("an error occurred");  
    
    else  
    
      printf("myByte is %d", myByte);  
```
    
void flush(bool flushIn, bool flushOut)

Clears data from one or both of the serial buffers. Any data in the cleared
buffers is discarded. flushIn = true clears the incoming data buffer and
fluhOut = true clear the outcoming data buffer.


### int available()

Returns the number of available bytes.
Lets you query how many bytes are available.

