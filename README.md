# mm1-hat-openocd
Tools for flashing blank chips

# Programm the ATSAMD21G18 on the MM1 Hat

### Install necessary software:

```
sudo apt install gcc-arm-none-eabi dirmngr libtool autoconf libusb-dev
```

### Clone the OpenOCD repository 
Note: (as of writing 322d2fa12c9b5520e06c1d581ce8b4e3c75750ca):

```
git clone https://git.code.sf.net/p/openocd/code openocd-code
cd openocd-code
./bootstrap
./configure --enable-sysfsgpio --enable-bmc8235gpio
make
sudo make install
```

### Flashing

Lets flash the Arduino Zero (or Adafruit Feather m0) bootloader:

```
cd openocd
wget -O samd21_sam_ba.bin https://github.com/arduino/ArduinoCore-samd/blob/master/bootloaders/zero/samd21_sam_ba.bin?raw=true
openocd -f bootloader.cfg
```

We can flash any firmware we want now (possibly including a bootloader).

Note:  Must pad the firmware before you can upload other parts

```
truncate -s 8192 samd21_sam_ba.bin; cat samd21_sam_ba.bin firmware.bin > boot-firmware.bin
```

Lets flash the SeeSaw (or CircuitPython) bootloader:

```
cd openocd
wget -O samd21_sam_ba.bin https://github.com/robotics-masters/mm1-hat-seesaw/blob/master/firmware/seesaw-roboticsmasters_mm1.bin?raw=true
openocd -f mm1-hat.cfg -c "program seesaw-mm1-hat.bin verify 0x2000"
```
