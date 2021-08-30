
# Embedded Devices and Platforms

In this article I'll be talking in brief about some of the different microcontrollers, FPGA boards I have used and whats my take on it, 
along with some of the projects I have implemented over them. I have also provided links to some resources for reference. 
In the end, I have discussed the latest development tools like [MicroPython](https://micropython.org/) and [Low.js](https://www.lowjs.org/) as well.


### Pynq Z2
<img align="left" src="https://media-exp1.licdn.com/dms/image/C5112AQHodDAavDw7tg/article-inline_image-shrink_1000_1488/0/1569670873318?e=1635984000&v=beta&t=Gi1R897h_ho_5sTBnCypcYLXEfL8YX-UJvLSWREhcP0">

Pynq is an open-source project from Xilinx enabling designing an embedded system with Xilinx Zynq SoCs. 
It has Zynq Z7020 with 512MB DDR3 having 1 Arduino, 2 RPi header and 2xPmod GPIO. In Pynq we can use overlays to accelerate your processing speed for certain programs in Python. 
I use Vivado HLS to create all the IP core used in my project, which is later included in the design in Vivado and after generating Bit-stream the hardware is exported. 
This IP is then tested in Vivado SDK. All FPGA board having Zynq architecture (eg: Zybo board and Zedboard) can have similar code, design.


#### Projects:

[Hand-Number Recognition](https://www.harshmittal.tech/blogs/2020/03/12/IEEE-2019.html): Created an IP core for Hand-Number recognition using Vivado HLS. The model was trained over Matlab. 
This same project was also implemented over Zybo and Zedboard.



### Arduino UNO

<img align="left" src="https://media-exp1.licdn.com/dms/image/C5112AQGvg3BOxp9isQ/article-inline_image-shrink_1000_1488/0/1569669645025?e=1635984000&v=beta&t=mOSFBph_olwiQXAbKwRjZ5F4gzUkESttFHaVOFEEIPY">

Arduino is one of the most popular open-source hardware and software company. 
They have created tons of hardware which mostly consists of the 8-bit AVR microcontroller. 
For beginners Arduino Uno is recommended as programming on it is not difficult and it is also backed by a strong open source community if you get stuck somewhere. 
It is meant for rapid development and education. Arduino Uno has ATmega328p microcontroller with 14 digital, 6 analog pins and can be programmed using Arduino IDE. 
It also supports Serial/UART, SPI, PWM, External Interrupts, I2C, AREF (Analog Reference).

#### Projects:

- [Smoke Detection](https://github.com/harshmittal2210/Optical-Smoke-Alarm-Using-Arduino): I had used MOC7811 along with a buzzer for detecting smoke and alerting the user.
- Bot: A bot that can be controlled using HC-08 Bluetooth module, having 4 wheels and a gripper.


### Arduino Mega 2560

<img align="center" src="https://media-exp1.licdn.com/dms/image/C5112AQGCeyZLPKuLrQ/article-inline_image-shrink_1000_1488/0/1569670495419?e=1635984000&v=beta&t=Th7EPfVBwB5kR3n1GNagT_5dFfCcDIX4g5E3kyqpyJc">

This is generally used in place of Arduino UNO if you want a greater number of pins/memory. It is based on ATmega2560 and has 54 digital, 16 analog pins. It has all the advantage of Arduino UNO but the price is higher.

### Projects:
RSA Encryption for IoT system: This was first implemented over UNO but due to need of more memory I had to switch over to Mega board.
NodeMCU


> Both Arduino UNO and Arduino Mega has one disadvantage to use it for IoT application you need to connect it with external devices like ESP8266 to have Wi-Fi connectivity. NodeMCU is part of Arduino family which have ESP8266 on board thus it is considered ideal for small IoT applications. Small because it has a smaller number of pins as compared to UNO and Mega. NodeMCU has one more disadvantage that only one ADC pin is present, thus limiting the number of sensors that can be attached.

### Project:
Controlling LED wirelessly: This I had done in two ways, first using Adafruit and second by creating a local server.
Design an IoT network using sensors and actuators for smart home automation.

**Q: Is Arduino used in Industry?**

This depends upon the company. But most of the companies do not prefer using Arduino. Arduino is not meant to be used in harsh climates and there is no protection from noise, over-voltage and other factors. Thus, it is mostly used for rapid prototyping.

**Q: Want to try Arduino for free?**

If you want to try Arduino before buying you can try making some projects over Tinkercad. It is very simple to use and have several demos available online. Many sensors and actuators are also present for prototyping. I use it extensively when I don’t have a board around or I just want to try out my design when I don’t have the required hardware.
 
 
### Raspberry Pi
Raspberry is a small portable single board computer which you can connect to monitor, attach peripherals and use it for various projects. The latest model is the Raspberry Pi 4(RPi 4) but RPi 3 is most commonly used as of today. RPi 4 has a better processor (Cortex A72) and have upgraded RAM from LPDDR2 to LPDDR4. Apart from it, there are up-gradation in graphics, USB ports, Bluetooth and shifting to Type C for power. A major advantage of Type C is having more current thus providing more power to the processor for processing.
No alt text provided for this image


#### Projects:
Created an application using PyQt for Smart Home Automation and Security to control different sensors around the house using NodeMCU via MQTT. Implemented ARIMA and LSTM model for power consumption prediction over a year. The model was trained using Tensorflow and Keras.

**Q: Raspberry Pi vs Arduino?**

If you want to do more processes than controlling sensors/actuators use RPi else Arduino. It is true you can connect sensors to RPi itself, but the major problem is input voltage and current for the sensors. RPi provides 3.3V only and many sensors work on 5V and require more current than RPi can offer. Arduino is meant for performing repetitive tasks over and over.

**Q: Which OS is best for RPi?**

This is mostly project dependent. I use Raspbian (official) as it is lightweight, and you can easily find troubleshooting for Raspbian. You can try Windows 10 IoT core, it is considered best for just coding and programming. It is not same as the windows 10 version you have on the laptop but is a simpler version of it.

**Q: Can you use RPi without a monitor?**

Yes! For installation use headless installation and later communicate to RPi using LAN/Wifi


### Beaglebone Black

This development platform is similar to RPi. It also runs on Linux. It has Cortex A8 processor with 4GB 8-bit eMMC on-board flash storage with 2x42 pin headers. One of the best features about this device is we can start development using a single USB cable. I had also used BBB for getting started with the Yocto Project.


#### Projects:

- Made a Linux OS from scratch using the Yocto project.
- Tested Authentication Algorithm.



**Q: BBB vs RPi3**

BBB has better I/O capabilities than RPi but RPi is better if you want to work on audio/video.


### Tiva TM4C123G

This I feel is one of the best-embedded devices that I had used so far. It is based on Cortex M4F microcontroller. It has onboard ICDI (In-Circuit Debug Interface),2 RGB LED and two switches. For the coding purpose, I use Keil. If someone wants to learn proper Embedded C, this is where you should invest your time. It supports I2C, Serial UART, CAN, SPI and have multiple ports for them thus enabling many devices to be connected in a single network.


#### Projects:

- Developed a game called Space Invaders.
- Several small projects to understand it’s working.



**Q: TM4C123 vs Arduino?**

On the surface, it may seem like they are common in terms of GPIO, ADC, timers etc but there internal working is different. Coding using Keil / Code Composer Studio can be difficult and will need a basic knowledge of how things work but to simplify things there is an open-source development environment called Energia for programming Tiva board. In Arduino port, initialization is easy as compared to Tiva when using Keil. You have to set different register bits during initialization.

**Q: Best Resources for learning it?**

Embedded Systems - Shape The World: Microcontroller Input/Output is the best course to get started.


### Atmega 16 Microcontroller


This is the most commonly used AVR microcontroller used in the Atmel family. It has 40 Pins and has UART, SPI for serial communication. It is a single chip that comes with CPU, ROM, RAM, EEPROM, Timers, ADC, and 4 8bit ports. I had used CodeVision AVR for making different projects.

#### Projects:
Prototype for Martian bot with a camera on board with a 180-degree field of vision with the help of servo along with a gripper to remove obstacles. This device was controlled HC-08 Bluetooth module.


## Some new platforms
1.     MicroPython
Embedded C rules the Embedded Systems. Almost every microcontroller is programmed using Embedded C. On the other hand, Python is considered one of the best languages for development in most of the application and have lots of strengths to become a great language for embedded systems. This is where MicroPython comes in, it bridges the gap between and uses a subset of Python 3 and is optimized to be run over microcontrollers. To try it out you can use the online simulator for running your codes and have basic knowledge about it. Right now, it is in its beta stage only.
PyBoard


To try on actual hardware, you can use PyBoard which with the combination of MicroPython makes a Python OS. It has 30 GPIO, I2C, UART, SPI, PWM, ADC, DAC, timers, LEDs, accelerometer. When you connect it to computer it is connected as a USB device as well as a Serial device. And since Python is an interpreter language, we can make use of that as well, thus making debugging easy.

MicroPython has also some disadvantages like it is a bit slow as compared to C/C++ code and uses little more space. It also does not support all the libraries that are offered in Python 3.
2.     Low.js


Node.js is one of the best API for internet application but since it uses lot of resources it cannot be used directly on embedded devices. Low.js is a part of JavaScript runtime Node.js enabling us to implement scalable IoT related applications easily and efficiently over embedded devices. Low.js enable perform multiple task at same time and has additional advantages over Arduino like following protocols according to defined standards. Choosing between Low.js and MicroPython is difficult. It is almost same as choosing between Node.js and Python. This totally comes down to the fact that in which language you are more comfortable, and which is the main language in your project. Low.js runs on any ESP-32 WROVER module. Two boards which fully supports it are Neonious one and Generic ESP32-WROVER Board.




I hope you found this article helpful. For any more queries feel free to contact me. You can check www.harshmittal.tech as well for more projects.

Thank You
