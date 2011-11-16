
## Functions

void ofSoundStreamSetup(int nOutputs, int nInputs, ofSimpleApp * OFSA)

description

Sets up the audio, with nOutputs channels of audio out, nInputs channels of
audio in. You also must pass in a pointer to the ofSimpleApp, so you can just
use the word "this". For example, for 2 channel output, call in the setup
function:

    
      
```cpp    
    ofSoundStreamSetup(2,0,this);  
```
    

  
In this simplified call, the bufferSize, sampleRate, and number of buffers
(for latency) are all set to defaults.

### ofSoundStreamSetup(int nOutputs, int nInputs, ofSimpleApp * OFSA, int
sampleRate, int bufferSize, int nBuffers)


Sets up the audio, but allows you to control more precise details of the audio
system.



void ofSoundStreamStop()

Stops (pauses) the audio stream.



void ofSoundStreamStart()

Starts (un-pauses) the audio stream. The stream starts automatically with
ofSoundStreamSetup, so you only need to call this if the stream has been
stopped.


void ofSoundStreamEnd()


Ends the audio stream.

void ofSoundStreamEnumerateDevices()

Prints out a list of devices that ofSoundStreamSetup can call from. At this
point, there is not interfeace to choose devices (default devices are used)
but that ability to choose is coming shortly.



