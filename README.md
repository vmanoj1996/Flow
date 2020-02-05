## PX4Flow Firmware
1. Verify the update rate and maximum speed that you want to measure before using this sensor
2. The stable branch of this repo runs at 400 Hz. However it is based on a 2014 commit of PX4/Flow (quite old). In case you want the master branch to run at 400Hz, kindly change the EXPOSURE_MAX to 40. Refer https://github.com/PX4/Flow/issues/122
2. This repo is not compatible with px4/flow. 
3. The default firmware shipped (as of Feb 2019) with px4flow sensor is based on a 2014 commit. The stable branch of this repo is based on that particular commit. Further the I2C frame is modified to suit my needs. Please change them before using it in your project. Gyro compensation of flow data is not done here. Please do it externally if needed.


[![Build Status](https://travis-ci.org/PX4/Flow.svg?branch=master)](https://travis-ci.org/PX4/Flow)

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/PX4/Firmware?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

PX4 FLOW is a smart camera processing optical flow directly on the camera module. It is optimized for processing and outputs images only for development purposes. Its main output is a UART or I2C stream of flow measurements at ~400 Hz.

Project:
http://px4.io/modules/px4flow

Dev guide / toolchain installation:
http://px4.io/dev/px4flow

For help, run:

```
make help

```


To build, run:
```
  make archives - this needs to be done only once
  make

```

To flash via the PX4 bootloader (first run this command, then connect the board):
```
  make upload-usb
```

By default the px4flow-v1_default is uploaded to upload a different version

```
  make <target> upload-usb
```
Where <target> is one of the px4flow tatgets listed by ```make help```
  
  NOTE:
  1. This fork will not output the same data. i2c frame output is modified to suit my needs
  2. This fork won't compensate the angular velocity using its internal gyroscope
