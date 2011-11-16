

### Functions

### void ofSoundSetVolume(float vol)

Sets the volume of all ofSoundPlayer objects to the volume (vol) specified.
0.0 - 1.0 range. 0.0 is silent and 1.0 is full volume.


### void ofSoundStopAll()

Stops all sounds being played by all ofSoundPlayer objects.



### float* ofSoundGetSpectrum(int nBands)

Returns a floating point array of frequency bands (nBands in size) to a
maximum of 512 bands, representing the fft spectrum of all the sounds currently playing.

  
note: Make sure that you call ofSoundSetUseSpectrum(true) first if you wish to
use this function.



### Classes

## ofSoundPlayer

The ofSoundPlayer class wraps fmod, which is a powerful audio utility library.
The ofSoundPlayer allows you to load sound files and control and manipulate
their playback and properties.


### void loadSound(string fileName, bool stream)

Loads a sound file given by fileName. Sound files can be in .wav, .aif, .mp3,
.mp2, .ogg or .raw format. The program will look for the file relative to the
data/ folder. If you set the optional 'bool stream' argument to true the file
will be streamed from disk instead of being completely loaded into memory. It
makes a lot of sense to stream files if you are dynamically loading large
sound files into your program, which would normally cause the program to
freeze for a short time as the whole sound is read into memory.

  
Examples:

  
Load a Sound
```cpp
    
    ofSoundPlayer mySound;  
    
    mySound.loadSound("beat.mp3");
```
  
  
Load a Sound with Folder Path
```cpp
    
    ofSoundPlayer mySound;  
    
    mySound.loadSound("sounds/beat.mp3");
```
  
  
### void unloadSound()


Stops and unloads the current sound.

  
Example:
```cpp
```cpp
    
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.play();  
    
    mySound.unloadSound(); //Stops sound from playing, unloads "beat.mp3"
````


### void play()

description

Plays the sound. If setMultiPlay() has been set to true each play() command
will spawn a new copy of the sound on a new channel, letting the existing
sounds continue until they are finished. If setMultiPlay() is set to false it
will restart the playback of the song.

  
Examples:
```cpp
  
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.play(); //Plays sound  
    
    mySound.play(); //Restarts and plays sound
```
  
  
Multiplay:
```cpp
    
    ofSoundPlayer mySound;  
    
    mySound.setMultiPlay(true);  
    
    mySound.load("beat.mp3");  
    
    mySound.play(); //Plays sound  
    
    mySound.play(); //Adds new copy of sound to channel and plays over currently playing sound
```


### void stop()

Stops the sound currently playing.

  
Example:
```cpp

```cpp    
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.play(); //Begins playback of sound  
    
    mySound.stop(); //Ends playback, stops audio
```


### void setVolume(float vol)

Sets the volume (vol) of the sound. 0.0 - 1.0 range. 0.0 is silent and 1.0 is
full volume.

  
Example:
```cpp

```cpp    
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.play();  
    
    mySound.setVolume(0.1f); //Sets volume at 10% of maximum

```

### void setPan(float vol)

Sets the pan position (pct) of the sound. 0.0 - 1.0 range. 0.5 is center pan,
0.0 is full left pan and 1.0 is full right pan.

  
Example:
```cpp

```cpp
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.play();  
    
    mySound.pan(0.2f); //Pans to the left  
    
    mySound.pan(0.8f); //Pans to the right  
    
    mySound.pan(0.5f); //Back to center
```


### void setSpeed(float spd)

Sets the playback speed (spd) of the sound. 1.0 is the normal speed. 2.0 is
double the normal speed etc.

  
Example:
```cpp
    
    ofSoundPlayer mySound;  
    
    mySound.loadSound("beat.mp3");  
    
    mySound.play();  
    
    mySound.setSpeed(2.0f); //Chipmunk Voice  
    
    mySound.setSpeed(0.2f); //Isaac Hayes on Muscle Relaxers  
    
    mySound.setSpeed(1.0f); //Normal again
```



### void setPaused(bool bP)

Pauses and un-pauses the playback of the sound.

  
Example:
```cpp
    
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.play();  
    
    mySound.setPaused(true); //Sound is paused  
    
    mySound.setPaused(false); //Sound is unpaused, playback continues
```


### void setLoop(bool bLp)

Loops the sound if set to true. Does not loop the sound if set to false.
Default is false.

  
Example:
```cpp

    
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.setLoop(true); //Sound will loop  
    
    mySound.play();
```

### void setMultiPlay(bool bMp)

Allows a sound to be played multiple times at once. When set to true the
play() function will start playing the sound on a new channel, letting the old
channels continue until they are done playing. When set to false the play()
function will stop the channel before playing the sound.

  
Example:
```cpp

  

    
    ofSoundPlayer mySound;  
    
    mySound.setMultiPlay(true);  
    
    mySound.load("beat.mp3");  
    
    mySound.play(); //Plays sound  
    
    mySound.play(); //Adds new copy of sound to channel and plays over currently playing sound
```

### void setPosition(float pct)

Sets the playback-head to the position (pct) specified. 0.0 - 1.0 range. 0.0
is the beginning of the sound file and 1.0 is the end.

  
Example:
```cpp

    
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.play();  
    
    mySound.setPosition(0.5f); //Moves the playhead to halfway through the sound  
    
    mySound.setPosition(0.0f); //Moves the playhead back to the beginning of the sound


### float getPosition()

Returns the current position of the playback-head in the sound. 0.0 - 1.0
range. 0.0 is the beginning of the sound file and 1.0 is the end.

  
Example:
```cpp    
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.play();  
    
    mySound.getPosition(); //Returns the current position as a percent 0.0-1.0
```


### bool getIsPlaying()

Returns true if sound is currently playing, otherwise returns false.


Example:
```cpp

    
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.getIsPlaying(); //Returns false  
    
    mySound.play();  
    
    mySound.getIsPlaying(); //Returns true
```


### float getSpeed()

Returns the pan position of the sound. 0.0 - 1.0 range.
0.5 is center pan, 0.0 is full left pan and 1.0 is full right pan.

  
Example:
```cpp

    
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.getSpeed(); //Returns 1.0  
    
    mySound.setSpeed(2.0f);  
    
    mySound.getSpeed(); //Returns 2.0f
```

### float getPan()


Returns the pan position of the sound. 0.0 - 1.0 range.

0.5 is center pan, 0.0 is full left pan and 1.0 is full right pan. Default is
0.5

  
Example:
```cpp

    
    ofSoundPlayer mySound;  
    
    mySound.load("beat.mp3");  
    
    mySound.play();  
    
    mySound.getPan();//Returns 0.5  
    
    mySound.setPan(0.2f);  
    
    mySound.getPan();//Returns 0.2
```


### bool isStreaming

This boolean variable tells if the sound we are using is streaming or not.



### bool bMultiPlay

Allows a sound to be played multiple times at once. See setMultiPlay(bool bMp)
function for more info.



### bool bLoop

bLoop variable controls if we are playing the sound as a loop.



### bool bLoadedOk

bLoadedOk is a boolean variable containing true if the sound was successfully
loaded.



### bool bPaused

bPaused contain true if we pause the sound.



### float pan

Contains the pan position of the sound. Going from 0 to 1.



### float volume

Contains the value of the volume of our sound.



### float speed

Contains the playback speed of the sound. 1.0 is the normal speed. 2.0 is
double the normal speed, -1 is backwards etc.



### int length

The length of the loaded sound in milliseconds 
