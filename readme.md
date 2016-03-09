# Infra Red Controlled Robot
This is the first experiment I tried with the board of education arduuino robot shield.  The experiment involves using [Ken Shirrifs IR Library](https://github.com/z3t0/Arduino-IRremote) along with any IR Receiver.  In order to use this example you will first need to determine what the IR codes are for the transmitter you wish to use.  The examples/IRrecvDemo sketch in the library provides a simple example of how to receive codes.  See [Kens Blog](http://www.righto.com/2009/08/multi-protocol-infrared-remote-library.html) for more info.

[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/fsBSJAT_SEQ/0.jpg)](http://www.youtube.com/watch?v=fsBSJAT_SEQ)

The motors on the robot are 360 degree servos that are controlled by sending them a digital pulse ranging in duration from 1300 to 1700 microseconds every 20milliseconds.  The width of the pulse determines the speed and direction they rotate.  1500 would be no motion at all, 1300 full speed counter clockwise and 1700 full speed counter clockwise.  While this is modifying the width of the pulse it is not the same as the PWM functions found in the Arduino library.

When polling for commands from the IR receiver I found that that this particular remote requires me give it at least 175 ms before attempting to read its next transmission.   That, combined with the IR remote being single channel makes for a choppy RC because within 200 ms the servos have already repeated the last command 10 times.

Oh and if you are wondering why no beeping from the Robot it is because the tone function is unable to access TIMER2 because it is being used by the IR Library   The servo library uses TIMER1.


[Source Code](https://github.com/driewe/RemoteControlRobotIR/blob/master/sourcecode/RemoteRobotWithFunctions.ino)
