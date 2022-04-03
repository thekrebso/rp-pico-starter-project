# RP-Pico-Starter-Project

I'am using non-LTS Ubuntu on WSL2

&nbsp;

## VS Code Extensions

- Microsoft's [C/C++ Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
- Microsoft's [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools)
- marus25's [Cortex-Debug](https://marketplace.visualstudio.com/items?itemName=marus25.cortex-debug)

&nbsp;

## How to set up OpenOCD



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

&nbsp;

## How to attach picoprobe device to linux through WSL2

### Windows

```powershell
winget install --interactive --exact dorssel.usbipd-win
usbipd wsl list

# this step you will need to do every time you launch wsl
usbipd wsl attach --busid <busid of the device>
```

### Linux

```sh
# create picoprobe.rules with contents: 
#  # Raspberry Pi Pico probe
#  ATTRS{idVendor}=="2e8a", ATTRS{idProduct}=="0004", MODE="0666"
sudo nano /etc/udev/rules.d/60-picoprobe.rules

sudo service udev restart

sudo udevadm control --reload-rules

sudo udevadm trigger
```

&nbsp;

## Useful resources

- Official [Getting Started With Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)
- Official [Raspberry Pi Pico C/C++ Sdk](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-c-sdk.pdf)
- Shawn Hymel's [Raspberry Pi Pico and RP2040 - C/C++ Part 2: Debugging with VS Code](https://www.digikey.be/en/maker/projects/raspberry-pi-pico-and-rp2040-cc-part-2-debugging-with-vs-code/470abc7efb07432b82c95f6f67f184c0)
- Ravi Teja's [How to Program Raspberry Pi Pico with Visual Studio Code?](https://www.electronicshub.org/program-raspberry-pi-pico-with-visual-studio-code/)
