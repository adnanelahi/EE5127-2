# Feather Onboard Sensors

![sensors\_Feather\_Sense\_top.jpg](https://cdn-learn.adafruit.com/assets/assets/000/089/096/medium800/sensors\_Feather\_Sense\_top.jpg?1583860491)

The Feather nRF52840 Sense is full of all kinds of goodies. Let's take a look!

![sensors\_Adafruit\_Feather\_nRF52840\_Sense\_pinout.png](https://cdn-learn.adafruit.com/assets/assets/000/110/594/medium800/sensors\_Adafruit\_Feather\_nRF52840\_Sense\_pinout.png?1649264841)

### Microcontroller and QSPI

![sensors\_Feather\_Sense\_pinouts\_MCU\_QSPI.png](https://cdn-learn.adafruit.com/assets/assets/000/099/160/medium800/sensors\_Feather\_Sense\_pinouts\_MCU\_QSPI.png?1612233319)

* **Nordic nRF52840 Bluetooth LE processor** - 1 MB of Flash, 256KB RAM, 64 MHz Cortex M4 processor.
* **QSPI flash** - 2MB of internal flash storage for datalogging or CircuitPython code. QSPI requires 6 pins, which are not broken out on the 0.1" pin headers to avoid conflicts. QSPI is neat because it allows you to have 4 data in/out lines instead of just SPI's single line in and single line out. This means that QSPI is _at least_ 4 times faster. But in reality is at least 10x faster because you can clock the QSPI peripheral much faster than a plain SPI peripheral.

### Power Pins

![sensors\_Feather\_Sense\_pinouts\_power\_pins.png](https://cdn-learn.adafruit.com/assets/assets/000/099/159/medium800/sensors\_Feather\_Sense\_pinouts\_power\_pins.png?1612233285)

* **3V**: This pin is connected to the output of the on board 3.3V regulator. It can be used to supply 3.3V power to external sensors, breakouts or FeatherWings.
* **LIPO Input (Bat)**: This is the voltage supply off the optional LIPO cell that can be connected via the JST PH connector. It is nominally \~3.5-4.2V.
* **VREG Enable (En)**: This pin can be set to GND to disable the 3.3V output from the on board voltage regulator. By default it is set high via a pullup resistor.
* **USB Power (USB)**: This is the voltage supply off USB connector, nominally 4.5-5.2V.

### Analog Pins

![sensors\_Feather\_Sense\_pinouts\_analog\_pins.png](https://cdn-learn.adafruit.com/assets/assets/000/099/346/medium800/sensors\_Feather\_Sense\_pinouts\_analog\_pins.png?1612977953)

The **6** available analog inputs (**A0 .. A5**) can be configured to generate 8, 10 or 12-bit data (or 14-bits with over-sampling), at speeds up to 200kHz (depending on the bit-width of the values generated), based on either an internal 0.6V reference or the external supply.

The following default values are used for Arduino. See this guide's [nRF52 ADC page](https://learn.adafruit.com/adafruit-feather-sense/nrf52-adc) for details about changing these settings.

* **Default voltage range**: 0-3.6V (uses the internal 0.6V reference with 1/6 gain)
* **Default resolution**: 12-bit (0..4096)
* **Default mV per lsb** (assuming 3.6V and 12-bit resolution): **1 LSB = 0.87890625 mV**

CircuitPython uses 1/4 gain with a VDD/4 reference voltage.

An additional two ADC pins are available but pre-connected to provide specific functionality:

* **AREF** (**A7 / P0.31**), which can be used as an optional external analog reference for the internal comparator (COMP) peripheral. AREF is not available for use with the ADC. This pin can be accessed in code via **PIN\_AREF** or **A7**. If using an external AREF, this **must be less than or equal to VDD**, which is usually 3.3V!
* **VOLTAGE\_MONITOR (A6 / P0.29)**: This pin is hard wired to a voltage-divider on the LIPO battery input, allowing you to safely measure the LIPO battery level on your device. If possible, you should avoid using this pin as an _input_ because you will lose the ability to read the battery voltage. You can use it as an _output_ just make sure to switch the pin to analog input when you want to do the battery read, then back to output when toggling pins

In order to avoid damaging the sensitive analog circuitry, AREF must be equal to or lower than VDD (3.3V)!

Unlike digital functions, which can be remapped to any GPIO/digital pin, the ADC functionality is tied to specified pins, labelled as A\* in the image above (A0, A1, etc.).

### PWM Outputs and I2C Pins

![sensors\_Feather\_Sense\_top.jpg](https://cdn-learn.adafruit.com/assets/assets/000/099/347/medium800/sensors\_Feather\_Sense\_top.jpg?1612978035)

**PWM Outputs**

Any GPIO pin can be configured as a PWM output, using the dedicated PWM block.

Three PWM modules can provide up to 12 PWM channels with individual frequency control in groups of up to four channels.

![sensors\_Feather\_Sense\_pinouts\_I2C.jpg](https://cdn-learn.adafruit.com/assets/assets/000/099/349/medium800/sensors\_Feather\_Sense\_pinouts\_I2C.jpg?1612979565)

**I2C Pins**

I2C pins on the nRF52840 have 4.7K pullup resistors installed and are connected to all-but-the-microphone sensors. You can connect any other sensors as long as there is not an I2C address collision

### Special Note

![sensors\_Feather\_Sense\_pinouts\_D2.png](https://cdn-learn.adafruit.com/assets/assets/000/099/348/medium800/sensors\_Feather\_Sense\_pinouts\_D2.png?1612979393)

The following pins have some restrictions that need to be taken into account when using them:

* **D2/NFC2**: The D2 pin is uses the same pad as one-half of the NFC antenna pins. By default, the nRF52840 Feather ships with these pins configured for GPIO mode, which is done by writing a value to the UICR flash config memory. If you wish to use NFC, you will need to erase the UICR memory which requires erasing the entire chip, and you will need a [Segger J-Link](https://www.adafruit.com/product/3571) to reflash the bootloader and firmware.

### Sensors

![sensors\_featherSenseAccelDouble.jpg](https://cdn-learn.adafruit.com/assets/assets/000/127/207/medium800/sensors\_featherSenseAccelDouble.jpg?1706110540)

**Gyro + Accel: y**our Feather Sense may have either an **LSM6DS33** or an **LSM6DS3TR-C**&#x20;

These sensors are 6-DoF IMU accelerometer + gyroscope. The 3-axis accelerometer can tell you which direction is down towards the Earth (by measuring gravity) or how fast the Feather Sense is accelerating in 3D space. The 3-axis gyroscope can measure spin and twist. Pair with a triple-axis magnetometer to create a 9-DoF inertial measurement unit that can detect its orientation in real-space thanks to Earth's stable magnetic field. **Both** **sensors are I2C on standard pins, have address 0x6A and IRQ pin on digital pin 3.**

As of January 10, 2024 - We have replaced the discontinued LSM6DS33 with an LSM6DS3TR-C 6 DoF sensor. The performance is improved however new firmware libraries will need to be used in order to read the accelerometer and gyroscope.

![sensors\_Feather\_Sense\_pinouts\_mag.png](https://cdn-learn.adafruit.com/assets/assets/000/099/351/medium800/sensors\_Feather\_Sense\_pinouts\_mag.png?1612979642)

**Magnetometer: LIS3MDL** - Sense the magnetic fields that surround us with this handy triple-axis magnetometer (compass) module. Magnetometers can sense where the strongest magnetic force is coming from, generally used to detect magnetic north, but can also be used for measuring magnetic fields. This sensor tends to be paired with a 6-DoF (degree of freedom) accelerometer/gyroscope to create a 9-DoF inertial measurement unit that can detect its orientation in real-space thanks to Earth's stable magnetic field. **Sensor is I2C on standard pins, address 0x1C**

![sensors\_Feather\_Sense\_pinouts\_proximity.png](https://cdn-learn.adafruit.com/assets/assets/000/099/352/medium800/sensors\_Feather\_Sense\_pinouts\_proximity.png?1612979715)

**Light + Gesture + Proximity: APDS9960** - Detect simple gestures (left to right, right to left, up to down, down to up are currently supported), return the amount of red, blue, green, and clear light, or return how close an object is to the front of the sensor. This sensor has an integrated IR LED and driver, along with four directional photodiodes that sense reflected IR energy from the LED. Since there are four IR sensors, you can measure the changes in light reflectance at each of the cardinal locations over time and turn those changes into gestures. **Sensor is I2C on standard pins, address 0x39 and IRQ pin on digital pin 36**

![sensors\_Feather\_Sense\_pinouts\_humidity.png](https://cdn-learn.adafruit.com/assets/assets/000/099/353/medium800/sensors\_Feather\_Sense\_pinouts\_humidity.png?1612979792)

**Humidity: SHT30** - This sensor has an excellent ±2% relative humidity and ±0.5°C accuracy for most uses. **Sensor is I2C on standard pins, address 0x44**

![sensors\_Feather\_Sense\_pinouts\_pressure.png](https://cdn-learn.adafruit.com/assets/assets/000/099/358/medium800/sensors\_Feather\_Sense\_pinouts\_pressure.png?1612980052)

**Temp + Pressure: BMP280** - This sensor is a precision sensing solution for measuring barometric pressure with ±1 hPa absolute accuracy, and temperature with ±1.0°C accuracy. Because pressure changes with altitude, and the pressure measurements are so good, you can also use it as an altimeter with ±1 meter accuracy. It has a low altitude noise of 0.25m and a fast conversion time. **Sensor is I2C on standard pins, address 0x77**

![sensors\_Feather\_Sense\_pinouts\_PDM\_mic.png](https://cdn-learn.adafruit.com/assets/assets/000/099/357/medium800/sensors\_Feather\_Sense\_pinouts\_PDM\_mic.png?1612979978)

**PDM Microphone sound sensor: MP34DT01-M** - PDM sound sensor. In CircuitPython, `board.MICROPHONE_DATA` is PDM data, and `board.MICROPHONE_CLOCK` is PDM clock. In Arduino, `D34` is PDM data, and `D35` is PDM clock.

### USB and Battery

![sensors\_Feather\_Sense\_pinouts\_USB\_battery.png](https://cdn-learn.adafruit.com/assets/assets/000/099/356/medium800/sensors\_Feather\_Sense\_pinouts\_USB\_battery.png?1612979922)

* **USB Micro** - This USB port is used for programming and/or powering the Feather Sense. It is a standard USB Micro connector.
* **Battery** - 2-pin JST PH connector for a battery. Power the Feather Sense from any 3V-6V power source, as it has internal regulator and protection diodes. You can also charge LiPoly batteries plugged into this connector using USB power.

Check that the batteries you are using are the the same as Adafruit polarity. Wrong polarity batteries will destroy the charging circuitry

### Buttons

![sensors\_Feather\_Sense\_pinouts\_buttons.png](https://cdn-learn.adafruit.com/assets/assets/000/099/355/medium800/sensors\_Feather\_Sense\_pinouts\_buttons.png?1612979880)

* **Reset button** - The button on the left next to the USB connector resets the board. Press once to reset. Quickly press twice to enter the bootloader.
* **User button** - The button on the right is both usable by the bootloader and user-controllable. Address it in code using `board.SWITCH` in CircuitPython and `D7` in Arduino.

### NeoPixel and Status LEDs

![sensors\_Feather\_Sense\_pinouts\_NeoPixel\_status\_LEDs.png](https://cdn-learn.adafruit.com/assets/assets/000/099/354/medium800/sensors\_Feather\_Sense\_pinouts\_NeoPixel\_status\_LEDs.png?1612979832)

* **NeoPixel** - The addressable RGB NeoPixel LED is used as a status LED by the bootloader and CircuitPython, but is also controllable using code. Control it using `board.NEOPIXEL` in CircuitPython and `D8` in Arduino.
* **Red status LED** - This little red LED, labeled D13, works as a status LED in the bootloader. Otherwise, it is controllable using code by addressing `board.RED_LED` in CircuitPython, and `D13` in Arduino.
* **Blue status LED** - This little blue LED, labeled Conn, works as a connectivity status LED in Arduino, and is user-controllable in both Arduino and CircuitPython. Control it in code by addressing `board.BLUE_LED` in CircuitPython and `D4` in Arduino.
* **Charge status LED** - The little LED, labeled CHG, below the USB connector is the charge status LED. When no battery is connected, it flashes. When a battery is connected and charging, the LED is steady amber.

This guide was first published on Mar 11, 2020. It was last updated on Jan 25, 2024.

This page (Pinouts) was last updated on Jan 24, 2024.

Text editor powered by [tinymce](https://www.tiny.cloud/).
