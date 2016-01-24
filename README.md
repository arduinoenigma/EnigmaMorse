# EnigmaMorse
Implements an enigma machine in an Arduino Pro Mini. Flashes encoded letters in morse code

This is a stand alone project, built using the enigma encryption engine from the <a href="http://arduinoenigma.blogspot.com">Arduino Enigma Machine Simulator</a> project.

It can be uploaded either to an Arduino Uno or an Arduino Pro Mini. It uses the built-in LED to flash the enigma encoded letters as Morse Code.

Download the three files and save the sketch as EnigmaMorse.

To use, open the Serial Monitor at 9600 baud.

By default it is configured as an M4 machine with thin B reflector, additional wheel Beta, wheels 1, 2, 3. All wheel settings are set to A. No plugs are installed.

If you start typing, it will encrypt it and flash the output on the LED.
If you type BDZG OWCX, it will be decrypted to AAAA AAAA and the LED will flash dot(short) dash(long) (pause) eight times. 

The enigma wheels will be advanced as keys are typed. To reset them to a known position, send !
The next characters sent after the exclamation mark will be the new wheel position.

if you send !AAAA the wheels will be reset back to the starting position.
Sending AAAA AAAA will encode to BDZG OWCX and it will be flashed out as Morse also.
