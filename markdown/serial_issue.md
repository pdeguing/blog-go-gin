# Serial issue
#robotic

### The results we want:

-> Being able to send a request to Arduino, read the answer and use the data to draw on the image for each capture we take with PiCamera. It needs to be reasonably fast for high speed driving.

### The problem we have:

-> The RPi becomes extremely slow as soon as we open the serial port device, making it impossible to not only read the data from Arduino but also to run the script normally. We end up taking a picture every 5 seconds at minima which is unacceptable for high speed driving.
It’s working perfectly on the Mac and nobody is reporting the issue online. So it’ must be due to something specific to our situation. But it is not due to the Pi itself or the Arduino, since the problem persists when trying other devices.

### Possible causes:

1. SSH via wifi is competing with serial stream (weird since I must not be the first one to try that).
	-> test: run a booting script to measure runtime without ssh
2. Vision bonnet is competing with serial stream (possible since much less people must have tried that before):
	-> test: run the test scripts on a native Pi Zero
3. Power supply problem, usb hubs drains power away from CPU causing it to run slower (would make sense since we had a performance problem before due to defectors battery):
	-> test: use self-power hub or direct usb-usb cable
4. Problem of version with pyserial, the Mac is running python 3.7 but the Pi is running 3.5:
	-> test: find a way to update Pi to Python 3.7 out of Raspbian packages