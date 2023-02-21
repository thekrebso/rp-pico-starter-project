# RP-Pico-Starter-Project

I'am using non-LTS Ubuntu on WSL2

&nbsp;

## VS Code Extensions

- Microsoft's [C/C++ Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
- Microsoft's [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools)
- marus25's [Cortex-Debug](https://marketplace.visualstudio.com/items?itemName=marus25.cortex-debug)

&nbsp;

## How to attach picoprobe device to linux through WSL2

### On Windows do

```powershell
winget install usbipd
usbipd wsl list

# this step you will need to do every time you launch wsl
usbipd wsl attach --busid <busid of the device>
```

### Then on Linux

[For setting up and wiring picoprobe and downloading and installing openocd](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)

[Might be useful?](https://github.com/dorssel/usbipd-win/wiki/WSL-support)

[Settings for picoprobe to work](https://github.com/raspberrypi/picoprobe/issues/48)

```sh

# use "interface/cmsis-dap.cfg" 
# with "openOCDLaunchCommands": ["adapter speed 5000"]

# to add user to plugdev\
$> groups # lists groups
$> sudo groupadd plugdev
$> sudo gpasswd -a yourusername plugdev
$> sudo udevadm control --reload

# to reload rules
$> sudo service udev restart
$> sudo udevadm control --reload-rules
$> sudo udevadm trigger

# list connected devices
$> lsusb
$> dmesg | grep tty
```

&nbsp;

## Other Useful resources

- [Raspberry Pi Pico SDK](https://github.com/raspberrypi/pico-sdk)
- [Raspberry Pi Pico SDK Examples](https://github.com/raspberrypi/pico-examples)
- Official documentation [Getting Started With Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)
- Official documentation [Raspberry Pi Pico C/C++ Sdk](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-c-sdk.pdf)
- Shawn Hymel's [Raspberry Pi Pico and RP2040 - C/C++ Part 2: Debugging with VS Code](https://www.digikey.be/en/maker/projects/raspberry-pi-pico-and-rp2040-cc-part-2-debugging-with-vs-code/470abc7efb07432b82c95f6f67f184c0)
- Ravi Teja's [Programming Raspberry Pi Pico using C | Getting Started with C SDK](https://www.electronicshub.org/program-raspberry-pi-pico-using-c/)
- Ravi Teja's [How to Program Raspberry Pi Pico with Visual Studio Code?](https://www.electronicshub.org/program-raspberry-pi-pico-with-visual-studio-code/)
