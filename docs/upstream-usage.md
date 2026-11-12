# Upstream usage record

The text below is preserved from the inherited README. It describes the upstream single-ID
example and package workflow, not a new test of this fork. Paths, package versions and system
administration commands are historical records rather than current installation instructions.
Use the [repository README](../README.md#install-and-scan) to install this checkout.


Tested on `Linux raspberrypi 5.15.61-v8+ #1579 SMP PREEMPT Fri Aug 26 11:16:44 BST 2022 aarch64`.
Python version `Python 3.9.2`.

### Method 1. Clone repositry

```
$ cd /usr/src/
$ sudo git clone https://github.com/Adam-Software/Feetech-Servo-SDK.git
$ sudo chown -R pi Feetech-Servo-SDK
$ cd Feetech-Servo-SDK/scsservo_sdk_example
$ python3 ping.py
Succeeded to open the port
Succeeded to change the baudrate
[ID:001] ping Succeeded. SCServo model number : 1540
```

### Method 2. Install pip package

Copy the sample file to any location convenient for you. In the example I use `/home/pi/FeetechTestFiles`

```
$ pip install feetech-servo-sdk
$ cd /home/pi/FeetechTestFiles
$ python3 ping.py
Succeeded to open the port
Succeeded to change the baudrate
[ID:001] ping Succeeded. SCServo model number : 1540
```
