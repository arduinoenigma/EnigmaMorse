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

There are two ways to encode messages. The wrong one and the right one.
The wrong one is just for unimportant messages, just start typing the message once the machine is setup.
For example, if the wheels are set to AAAA and the phrase THE WEATHER IS FINE is typed, it results in OPCE RWHV WXBA KQON 
If the wheels are reset to AAAA and the phrase THE WEATHER IS COLD is types, it comes out as OPCE RWHV WXBA QCVS.
Notice the two encoded messages are almost identical, revealing the fact that they contain a very similar message.

The right way to send messages involves message keys. A message key is a random starting position to be used with that message only.
The daily starting position is set (AAAA), then the random message key (WXKI) is typed, resulting in KSMQ. Then the wheels are turned to WXKI and the message THE WEATHER IS FINE is typed, resulting in JENQ VHWB ZUPT PTLI. Thus the whole message is KSMQ JENQ VHWB ZUPT PTLI.

For a second message, another random message key is selected: RXTD. The machine wheels are set to the daily starting position (AAAA) and RXTD is typed, resulting in VSHL. Then the rotors are turned to RXTD and the message THE WEATHER IS COLD is typed, giving us PIWI VRKO HNNG SVWL. Thus the whole message is VSHL PIWI VRKO HNNG SVWL. Notice that this is very different to KSMQ JENQ VHWB ZUPT PTLI, even though the clear text is almost the same.

To decode, set the rotors to the daily starting position (AAAA) and type the first four letters of the mesage: KSMQ and WXKI comes out. Now, set the rotors to WXKI and continue typing JENQ VHWB ZUPT PTLI, the decrypted text comes out as THEW EATH ERIS FINE.

How is the weather?
DDKW NDUB UYWE XBLK OHNX EEWT

The enigma machine traffic decoded at Bletchley Park was based on the fact that a letter never encoded to itelf and that certain words in the message were known (WEATHER). Once the daily key was broken for one message, all other messages encoded with the same daily key were broken.

The enigma machine can be used twice to create messages that are more difficult to break. For example, if the rotors are set to ABCD and JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ JJJJ is typed, it comes out as XBYG IXBL HXGW TXYX BQLH OTHO GPVR PHTE NDNP RDBC DVPD TXEN RVMO QVFA GNEC DCUV MKPI SKGM, notice there are no J on this encrypted text. If the wheels are set to EFGH and XBYG IXBL HXGW TXYX BQLH OTHO GPVR PHTE NDNP RDBC DVPD TXEN RVMO QVFA GNEC DCUV MKPI SKGM is typed, FVLY GGOW USDH EGVL LFYQ NDXG XTEF HPPH EKRX NCKU HISB BEAX IDYV TMRI QEYK MLQP NCIB DIQJ comes out, notice that the double encrypted message ends with a J, thus when encrypted twice with different settings, a letter can encrypt to itself.

To decrypt, set the rotors to EFGH and type FVLY..., XBYG... will come out, then set the rotors to ABCD and type XBYG..., JJJJ... will come out.
