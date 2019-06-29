## PX4Flow Firmware
1. USE THE STABLE BRANCH ONLY!!!
2. This repo is not compatible with px4/flow. 
3. The master branch of PX4/Flow (or this repo) seems to compute optical flow at lesser rate than the advertised 400Hz (its somewhere around 50Hz). This problem limits the maximum optical flow (and by extension, the maximum speed measurable) below usable levels. The default firmware shipped with px4flow sensor is based on a 2014 commit. The stable branch of this repo is based on that particular commit.
4. Further the I2C frame is modified to suit my needs. Please change them before using it in your project


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
  3. Stable branch of this fork runs at 400Hz(as of March 12,2019). But master code runs at 50Hz(the internal flow calculations). That limits the maximum velocity that the sensor can measure.
  


