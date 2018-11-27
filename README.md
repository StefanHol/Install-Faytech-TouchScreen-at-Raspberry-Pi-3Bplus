# How to install driver for FayTech resistive TouchScreen for Rasbperry Pi 3B+ with Raspbian
## Requirement
- Raspberry Pi 3B+
- Preinstalled Raspbian Image "https://www.raspberrypi.org/downloads/raspbian/"
- Change password
- Enable ssh for remote connection and establish connection to your Pi


## Documentation

Documentaion can be found here at driver download:
- https://www.faytech.com/catalogue/product/10-resistive-touch-monitor-ft10tmb/
 - - more information: check the downloaded ZIP-File **"Touch Driver, Resistive, standard_driver EETI-chipset based.zip"** -> Raspberry Pi-support -> **"eGalax Treiber_Driver Installation resistive for raspberry PI.pdf"**
- and here
- https://stackoverflow.com/questions/48067023/egalax-touchscreen-raspberry-pi


## Installation Steps

### Connect to your Pi
Update
- `sudo apt-get update`
- `sudo apt-get install xserver-xorg-input-evdev`
- `sudo apt-get install libx11-dev libxext-dev libxi-dev x11proto-input-dev`


### Driver Installation:
- go to Downloads Folder
- -  `cd ~/Downloads/`
- Download Touch Driver
- - `wget http://home.eeti.com.tw/touch_driver/Linux/20141009/eGTouch_v2.5.4330.L-ma.zip`
- Unzip Driver
- - `unzip -a eGTouch_v2.5.4330.L-ma.zip`
- - `cd eGTouch_v2.5.4330.L-ma`
- - `chmod +x setup.sh`

#### Start setup sript
 - `sudo setup.sh`
 - - **`2`** - (ARMhf)
 - - **`y`** - (License)
 - - **`2`** - (USB)
 - - **`Enter`**
 - - **`y`** - (to blacklist)
 - - **`y`** - (Already Patched) (not sure here, but it works for me)
 - - **`1`** - (one controller)

### Display Calibration
- `sudo apt-get install libx11-dev libxext-dev libxi-dev x11proto-input-dev`
- Download **xinput_calibrator-0.7.5.tar.gz**
 - `cd ~/Downloads/`
 - `wget https://github.com/downloads/tias/xinput_calibrator/xinput_calibrator-0.7.5.tar.gz`
 - `tar -xzvf xinput_calibrator-0.7.5.tar.gz`
 - `cd xinput_calibrator-0.7.5`
`./configure`
`make`
`sudo make install`

#### How To Calibrate
- it was not necceary to calibrate my display
- more information here:
**"eGalax Treiber_Driver Installation resistive for raspberry PI.pdf"** s.a.


### If this does not work jet:
- `sudo nano /usr/share/X11/xorg.conf.d/40-libinput.conf`
- - at the lines with touchscreen driver replace `libinput` by `evdev`
- - source https://stackoverflow.com/questions/48067023/egalax-touchscreen-raspberry-pi
