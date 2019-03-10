# OpenOCD Toolkit

This contains the files required to use the Raspberry Pi as a programmer on GPIO24 and GPIO25.  


## Usage

**Note:** Remember to update openocd.cfg before uploading.  Make sure correct bootloader/firmware is being uploaded.

```
sudo openocd
```

## Directory Stucture

```
openocd
  ./firmware  - contains bin files
  ./interface - contains config files for openocd
  ./target    - contains atsamd21 for openocd
```


## Padding File

OpenOCD does not allow for uploading of bin files without a firmware attached.  To overcome this, all firmware (CircuitPython, Seesaw, etc) needs to be padded by 0x2000 bits (8 kbytes) for the bootloader.  Use below if you plan on using OpenOCD for uploading new firmware.

```
truncate -s 8192 samd21_sam_ba.bin; cat samd21_sam_ba.bin firmware.bin > boot-firmware.bin
```

* samd21_sam_ba.bin - bootloader
* firmware.bin - firmware binary (CircuitPython, Seesaw, etc)
* boot-firmware.bin - output file to be uploaded using `sudo openocd`