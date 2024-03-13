This guide will go over the basics of programming in C of the M5Stick CPlus device, which is based on the ESP32 microcontroller. It shows the steps of setting up the development environment as well as the way to use example projects to get you started.

## The Device

Here you can find the [specifications](https://shop.m5stack.com/products/m5stickc-plus-esp32-pico-mini-iot-development-kit?variant=43983456764161#:~:text=IoT%20development%20kit-,Specification,-Resources) of the M5Stick CPlus, along with all the sensors it contains. The backside of the device shows that the base chip is the ESP32 Pico. More details on the other parts later.

![](attachment/Pasted%20image%2020240311162438.png)

## Install Visual Studio Code & Extension

We will be using Visual Studio Code as the main IDE for this work. [Start here](https://github.com/espressif/vscode-esp-idf-extension/blob/master/docs/tutorial/install.md) and follow along the detailed steps on installation.

Make sure to [install the ESP-IDF VS Code extension](https://marketplace.visualstudio.com/items?itemName=espressif.esp-idf-extension). This is our main method of interaction with the device.

### Configure the Extension

![](attachment/Drawing%202024-03-13%2011.21.19.excalidraw.png)

![](attachment/Drawing%202024-03-13%2011.25.42.excalidraw.png)

## Check the Command Palette for the New ESP-IDF Commands

![](attachment/Pasted%20image%2020240312160232.png)

![](attachment/Drawing%202024-03-13%2011.31.10.excalidraw.png)

## Launch Simple Example #1 (hello world)

![](attachment/Drawing%202024-03-13%2011.50.15.excalidraw.png)

![](attachment/Pasted%20image%2020240313115520.png)

![](attachment/Drawing%202024-03-13%2011.56.18.excalidraw.png)

![](attachment/Pasted%20image%2020240313115853.png)

Again, pick/create a folder such that the full path contains no whitespace, e.g. (C:\\ESP32Sample\\hello_world)

Use the command palette to configure the device

1. Set the device target to ESP32 chip (USB bridge)
2. Set the COM port (you will find it in your device manager, see below)
3. Set the flash baud rate to 115200
4. Look at the code under /main/hello_world_main.c
5. Build the code (remember the shortcut). This takes a while the first time.
6. If you see this on the terminal output, all good!

![](attachment/Pasted%20image%2020240313121550.png)

7. Flash the program on your device, pick UART as the method.
8. Success

![](attachment/Pasted%20image%2020240313121748.png)

### Which COM Port?

- In Windows, right click your "This PC" icon and go to the Device Manager.
- You should be able to see this when you connect the device via USB cable.
- It should disappear when you disconnect it.

![](attachment/Pasted%20image%2020240313120326.png)

If this is not the case, consider downloading and [installing the COM port driver](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/get-started/establish-serial-connection.html).

## Launch Simple Example #2 (blink a LED)

Follow all the same steps as before, selecting the blink example instead of hello_world

![](attachment/Pasted%20image%2020240311155254.png)

Look at blink_example_main.c

![](attachment/Pasted%20image%2020240313122912.png)

We can edit the configuration of this project, which holds some of the values used by the #define compiler directives

- Run command (ctrl + shift + p) "Configure project SDKConfig for coverage"
- Scroll down until you see this
  
![](attachment/Pasted%20image%2020240313123201.png)

- We need to flash the on-board red LED. Which Pin is it?
	- It's general-purpose input/output (GPIO) Pin 10

![](attachment/Pasted%20image%2020240313122614.png)

- change the Blink GPIO number to 10, then save
- Build, flash, run as before
- If all works well, you should see a red LED blinking on your device.
