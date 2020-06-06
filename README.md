# Robo HAT MM1 - Bootloader Tools

Tools for building UF2 firmware and flashing blank ATMEL SAM D21G chips.


## Setting up your environment

In order to compile the bootloader, you must install `arm-none-eabi-gcc`.  Please follow the below instructions for setting up your environment.

```
sudo add-apt-repository ppa:team-gcc-arm-embedded/ppa
sudo apt-get update
sudo apt-get install gcc-arm-embedded
```

Clone the repository:

```
git clone https://github.com/Microsoft/uf2-samdx1
cd uf2-samdx1
```


Build the bootloader:

```
make -j4 BOARD=robohatmm1_m4
```

## Build UF2

Please see the mm1-hat-bootloader/uf2 folder for further details.  Alternatively: https://github.com/Microsoft/uf2-samdx1

