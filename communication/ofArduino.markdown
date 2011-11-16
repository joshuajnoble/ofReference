## ofArduino

This is a way to control an ARduino that has had the firmata library loaded onto it from OF. To load firmata onto your Arduino,  run the Arduino IDE, open the Examples > Firmata > StandardFirmata sketch, and upload it to the Arduino board.

Once the ofArduino instance returns true from isArduinoReady() you can set the mode of the different digital pins using sendDigitalPinMode()

```cpp
sendDigitalPinMode(9, ARD_INPUT)
```

This sets pin 9 to input so that it can read a button press, while:

```cpp
sendDigitalPinMode(9, ARD_PWM)
```

sets pin 9 to be a PWM out pin. Note that this only works on pins that are PWM enabled.

### int connect(string device, int baud)
opens a serial port connection to the arduino

### void disconnect()
closes the serial port connection. Does not turn the Arduino off.

### void update()

polls data from the serial port, this has to be called periodically

### void setUseDelay(...)

### bool isInitialized()
eturns true if a succesfull connection has been established and the Arduino has reported a firmware

### void sendDigitalPinMode(int pin, int mode)
On the Arduino Uno pin: 2-13 mode: ARD_INPUT, ARD_OUTPUT, ARD_PWM setting a pins mode to ARD_INPUT turns on reporting for the port the pin is on Note: analog pins 0-5 can be used as digitial pins 16-21 but if the mode of _one_ of these pins is set to ARD_INPUT then _all_ analog pin reporting will be turned off

### void sendAnalogPinReporting(int pin, int mode)

### void sendDigital(int pin, int value, bool force)

### void sendPwm(int pin, int value, bool force = false);
On the Uno this will work on pins: 3, 5, 6, 9, 10 and 11 value: 0 (always off) to 255 (always on). the pins mode has to be set to ARD_PWM
TODO check if the PWM bug still is there causing frequent digital port reporting...


### void sendString(string str)
firmata can not handle strings longer than 12 characters.

### void sendReset()
This will cause your Arduino to reset and boot into the program again.

### void sendByte(unsigned char byte)
sends a byte without wrapping it in a firmata message, data has to be in the 0-127 range,
values > 127 will be interpreted as commands.

###int getPwm(int pin)

On the Arduino Uno pin: 3, 5, 6, 9, 10 and 11
returns the last set PWM value (0-255) for the given pin
the pins mode has to be ARD_PWM
Note: pin 16-21 can also be used if analog inputs 0-5 are used as digital pins

### int getDigital(int pin)
On the Arduino Uno pin: 2-13
returns the last received value (if the pin mode is ARD_INPUT) or the last set value (if the pin mode is ARD_OUTPUT) for the given pin
Note: pin 16-21 can also be used if analog inputs 0-5 are used as digital pins

Returns whether the pin is reading high or low, 1 or 0. You can test agsinst this with an if() statement which is handy:

### int getAnalog(int pin)

Returns the analog in value that the pin is currently reading. because the Arduino has a 10 bit ADC you get between 0 and 1023 for possible values.

### string getString()

### vector<unsigned char> getSysEx();
returns the last received SysEx message

### string getString();
returns the last received string

### int getMajorProtocolVersion();
returns the major firmware version

### int getMinorProtocolVersion();
returns the minor firmware version

### int getMajorFirmwareVersion();
returns the major firmware version

### int getMinorFirmwareVersion();
returns the minor firmware version

### string getFirmwareName();
returns the name of the firmware

### list<int>* getDigitalHistory(int pin);
On the Arduino Uno pin: 2-13
returns a pointer to the digital data history list for the given pin
Note: pin 16-21 can also be used if analog inputs 0-5 are used as digital pins

### list<int>* getAnalogHistory(int pin);
On the Arduino Uno pin: 0-5
returns a pointer to the analog data history list for the given pin

### list<vector<unsigned char> >* getSysExHistory();
returns a pointer to the SysEx history

### list<string>* getStringHistory();
returns a pointer to the string history

### int getDigitalPinMode(int pin);
returns ARD_INPUT, ARD_OUTPUT, ARD_PWM, ARD_SERVO, ARD_ANALOG

### int getAnalogPinReporting(int pin);
returns ARD_ON, ARD_OFF

### int getValueFromTwo7bitBytes(unsigned char lsb, unsigned char msb);
useful for parsing SysEx messages

### ofEvent<const int> EDigitalPinChanged;
triggered when a digital pin changes value, the pin that changed is passed as an argument

### ofEvent<const int> EAnalogPinChanged;
triggered when an analog pin changes value, the pin that changed is passed as an argument

### ofEvent<const vector<unsigned char> > ESysExReceived;
triggered when a SysEx message that isn't in the extended command set is received, the SysEx message is passed as an argument

### ofEvent<const int> EProtocolVersionReceived;
triggered when a protocol version is received, the major version is passed as an argument

### ofEvent<const int> EFirmwareVersionReceived;
triggered when a firmware version is received, the major version is passed as an argument

### ofEvent<const int> EInitialized;
triggered when the firmware version is received upon connect, the major firmware version is passed as an argument
from this point it's safe to send to the Arduino.

### ofEvent<const string> EStringReceived;
triggered when a string is received, the string is passed as an argument

### void sendServo(int pin, int value, bool force=false);
On the Arduino Uno pin: 9, 10
the pin has to have a servo attached for this to work.

angle parameter DEPRECATED as of Firmata 2.2
### void sendServoAttach(int pin, int minPulse=544, int maxPulse=2400, int angle=180);
On the Arduino Uno pin: 9, 10 attaches a servo to a pin

sendServoDetach DEPRECATED as of Firmata 2.2
### void sendServoDetach(int pin);
On the Arduino Uno pin: 9, 10 detaches a servo from a pin, the pin mode remains as OUTPUT

### int getServo(int pin);
returns the last set servo value for a pin if the pin has a servo attached
