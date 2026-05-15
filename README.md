# Description
This is proof of concept of USBIP in esp32 S2/S3 SoC.

## Start usbip driver
After installing `usbip` on linux, we need to modeprobe module.
`sudo modprobe vhci-hcd`

## Linux commands
Basic commands to list, attach and deatach devices:
- `usbip list -r 192.168.0.108`
- `usbip --tcp-port 3240 list -r 192.168.0.108`
- `sudo usbip attach --remote 192.168.0.108 -b 1-1`
- `sudo usbip detach -p 0`

- `sudo ln -s /var/lib/usbutils/usb.ids /usr/share/hwdata/usb.ids`



## Build

### Example: Install Espressive IDF Tools; build for ESP32S2:
    # create a build root directory, set environment
    export BUILDROOT=~/esp-build
    mkdir -p ${BUILDROOT}
    export IDF_TARGET=esp32s2
    export IDF_PATH=esp-idf
   
    # clone IDF tools, python environment, compiler for selected ESP CPU
    cd ${BUILDROOT}
    git clone --recursive git@github.com:espressif/esp-idf.git
    cd esp-idf
    python3 "${IDF_PATH}/tools/idf_tools.py" "install-python-env" 
    ./install.sh ${IDF_TARGET}
   
    cd ${BUILDROOT}
    # clone this repository to here, too
    git clone chegewara/esp32-usbip-poc
    cd esp32-usbip-poc
    mkdir build
    cd build
    cmake ..
