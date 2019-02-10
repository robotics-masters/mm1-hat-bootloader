
## Instructions

Pad File:

```
truncate -s 8192 samd21_sam_ba.bin; cat samd21_sam_ba.bin firmware.bin > boot-firmware.bin
```

Upload/Flash:

```
sudo openocd
```

## files

```
openocd
  ./firmware  - contains bin files
  ./interface - contains config files for openocd
  ./target    - contains atsamd21 for openocd
```


