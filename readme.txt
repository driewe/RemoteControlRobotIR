Received my board of education arduuino robot shield last Friday and the first thing I wanted to try after assembling it was to control it with an IR remote using Ken Shirrifs IR Library.

The motors on the robot are 360 degree servos that are controlled by sending them a digital pulse ranging in duration from 1300 to 1700 microseconds every 20milliseconds.  The width of the pulse determines the speed and direction they rotate.  1500 would be no motion at all, 1300 full speed counter clockwise and 1700 full speed counter clockwise.  While this is modifying the width of the pulse it is not the same as the PWM functions found in the Arduino library.

When polling for commands from the IR receiver I found that that this particular remote requires me give it at least 175 ms before attempting to read its next transmission.   That, combined with the IR remote being single channel makes for a choppy RC because within 200 ms the servos have already repeated the last command 10 times.

Oh and if you are wondering why no beeping from the Robot it is because the tone function is unable to access TIMER2 because it is being used by the IR Library   The servo library uses TIMER1.

Here is a short video
https://youtu.be/fsBSJAT_SEQ

