# OS-Espresso
The Open Source Espresso Controller


## Project Requirements {#requirements}
1. Store and edit extraction profiles.
2. Monitor and control the extraction process.
3. Display to control the system, via UART.
4. Wifi connection to turn on/off machine, edit profiles, and view history.

Would be nice features...
- I2S or audio output

### Hardware requirements
Inputs:
- Tank 1 temp (MAX6675 SPI)
- Tank 2 temp (MAX6675 SPI)
- Pressure 1 (ADS1015 I2C)
- Pressure 2 (ADS1015 I2C)
- Reservoir level (I2C)
- Scale 1 (HX711 CLK,DT)
- Scale 2 (HX711 CLK,DT)
- Dimmer Z/C (GPIO)
- Overtemp (GPIO)
- Power (GPIO)
- Brew (GPIO)
- Steam (GPIO)
- Other (GPIO)

Outputs:
- Heater 1 (GPIO)
- Heater 2 (GPIO)
- Dimmer control (GPIO)
- 3 way valve control (GPIO)
- RGBW status light (I2C)
- Display (UART)
- Internet (UART)

Total:
- 10 GPIO
- 1 I2C
- 1 SPI, 2 inputs
- 3 GPIO for HX711
- 1 UART
- plan for 20 pins minimum

## Software Design
The software design will be moduler. The main controller will monitor and control the system. It communicates to the display and/or wifi via UART.

The system is designed to run on the WeAct Blackpill v2 STM32F411CE board which can be ordered from aliexpress.
Since the software is framework based, it should also be able to work with the teensy 4 which I may switch to eventually.


## Other Components
During compiliation of the controller, you will need to specify the level of output. For example, a display or wifi server will need less information than a debugging output.

### Display
For a display I'm going to be using the 3.5" nextion discovery display, also from aliexpress. This module communicates over UART to the main microcontroller.

### WIFI
Currently wifi is not being developed. My plan is to use an ESP32 board to run the webserver, and it will get its data from the controller via UART.
