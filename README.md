<h2>twoArduinos</h2>

ROS connection of two Arduinos to Raspberry Pi
 
This repository contains changes I made to make the programs work in my environment.  The orignals and explanations of them are listed at:
 
https://www.intorobotics.com/how-to-use-rosserial-with-two-arduinos-and-raspberry-pi/

<h4>My Environment:</h4>

<h5>Operating System</h5>

- Using Ubuntu 20.04.02 LTS (Focal Fossa) 64-bit
- Kernal Linux 5.4.0-1029-raspi aarch64
- MATE 1.24.0

<h5>ROS version:</h5>

- noetic

<h5>Computers</h5>

- Raspberry Pi 4B
- Arduino 101
- Arduino Nano

<h4>Details:</h4>

Initial attempt to make the software work in this environment failed.  This is a list of changes made:

1.  Memcpy does not work in the Arduino ROS library, so msg.h has been change to use the C language equivalent.  3 lines changed.  The file should be in directory /home/*user*/Arduino/libraries/Rosserial_Arduino_Library/src/ros/
2.  The random_number Arduino does not send a number immediately, so the twoArduinos_Pi.py script receives a message with untyped data.  This is solved by embedding the if statements using the numeric value of the msg.data inside an if statement to check if the data is None.
3.  Each of the Arduino sketches had a comment starting with a # instead of //.  Both sketches have been changed.
4.  The launch script has not been changed, but is included for completeness.
