# RP-Pico-Starter-Project

## VS Code Extensions required

- Microsoft's [C/C++ Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
- Microsoft's [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools)
- marus25's [Cortex-Debug](https://marketplace.visualstudio.com/items?itemName=marus25.cortex-debug)

## OpenOCD & Picoprobe

I'am using non-LTS Ubuntu on WSL2

### OpenOCD setup

```sh
sudo apt install automake autoconf build-essential texinfo libtool libftdi-dev libusb-1.0-0-dev

git clone https://github.com/raspberrypi/openocd.git --branch picoprobe --depth=1 --no-single-branch

cd openocd/

./bootstrap

./configure --enable-picoprobe --disable-werror

# if there are any errors while running make, try to reinstall pkg-config
# sudo apt reinstall pkg-config
make

# and if you want
sudo make install
```

I assume you have already built picoprobe and uploaded to your Pico _(Check useful sites at the bottom)_

```sh
```

-----
Useful sites:

- [Getting Started With Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)
- [Raspberry Pi Pico C/C++ Sdk](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-c-sdk.pdf)
- [Digi-Key's "Raspberry Pi Pico and RP2040 - C/C++ Part 2: Debugging with VS Code"](https://www.digikey.be/en/maker/projects/raspberry-pi-pico-and-rp2040-cc-part-2-debugging-with-vs-code/470abc7efb07432b82c95f6f67f184c0)
