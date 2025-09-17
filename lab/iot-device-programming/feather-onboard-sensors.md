---
hidden: true
---

# Feather Onboard Sensors

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

**Magnetometer: LIS3MDL** - Sense the magnetic fields that surround us with this handy triple-axis magnetometer (compass) module. Magnetometers can sense where the strongest magnetic force is coming from, generally used to detect magnetic north, but can also be used for measuring magnetic fields. This sensor tends to be paired with a 6-DoF (degree of freedom) accelerometer/gyroscope to create a 9-DoF inertial measurement unit that can detect its orientation in real-space thanks to Earth's stable magnetic field. **Sensor is I2C on standard pins, address 0x1C**

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Gyro + Accel: y**our Feather Sense may have either an **LSM6DS33** or an **LSM6DS3TR-C**&#x20;

These sensors are 6-DoF IMU accelerometer + gyroscope. The 3-axis accelerometer can tell you which direction is down towards the Earth (by measuring gravity) or how fast the Feather Sense is accelerating in 3D space. The 3-axis gyroscope can measure spin and twist. Pair with a triple-axis magnetometer to create a 9-DoF inertial measurement unit that can detect its orientation in real-space thanks to Earth's stable magnetic field. **Both** **sensors are I2C on standard pins, have address 0x6A and IRQ pin on digital pin 3.**

As of January 10, 2024 - We have replaced the discontinued LSM6DS33 with an LSM6DS3TR-C 6 DoF sensor. The performance is improved however new firmware libraries will need to be used in order to read the accelerometer and gyroscope.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Light + Gesture + Proximity: APDS9960** - Detect simple gestures (left to right, right to left, up to down, down to up are currently supported), return the amount of red, blue, green, and clear light, or return how close an object is to the front of the sensor. This sensor has an integrated IR LED and driver, along with four directional photodiodes that sense reflected IR energy from the LED. Since there are four IR sensors, you can measure the changes in light reflectance at each of the cardinal locations over time and turn those changes into gestures. **Sensor is I2C on standard pins, address 0x39 and IRQ pin on digital pin 36**

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Humidity: SHT30** - This sensor has an excellent ±2% relative humidity and ±0.5°C accuracy for most uses. **Sensor is I2C on standard pins, address 0x44**

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Temp + Pressure: BMP280** - This sensor is a precision sensing solution for measuring barometric pressure with ±1 hPa absolute accuracy, and temperature with ±1.0°C accuracy. Because pressure changes with altitude, and the pressure measurements are so good, you can also use it as an altimeter with ±1 meter accuracy. It has a low altitude noise of 0.25m and a fast conversion time. **Sensor is I2C on standard pins, address 0x77**

<figure><img src="../../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**PDM Microphone sound sensor: MP34DT01-M** - PDM sound sensor. In CircuitPython, `board.MICROPHONE_DATA` is PDM data, and `board.MICROPHONE_CLOCK` is PDM clock. In Arduino, `D34` is PDM data, and `D35` is PDM clock.

### USB and Battery

<figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>

* **USB Micro** - This USB port is used for programming and/or powering the Feather Sense. It is a standard USB Micro connector.
* **Battery** - 2-pin JST PH connector for a battery. Power the Feather Sense from any 3V-6V power source, as it has internal regulator and protection diodes. You can also charge LiPoly batteries plugged into this connector using USB power.

Check that the batteries you are using are the the same as Adafruit polarity. Wrong polarity batteries will destroy the charging circuitry

### Buttons

<figure><img src="../../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>

* **Reset button** - The button on the left next to the USB connector resets the board. Press once to reset. Quickly press twice to enter the bootloader.
* **User button** - The button on the right is both usable by the bootloader and user-controllable. Address it in code using `board.SWITCH` in CircuitPython and `D7` in Arduino.

### NeoPixel and Status LEDs

<figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

* **NeoPixel** - The addressable RGB NeoPixel LED is used as a status LED by the bootloader and CircuitPython, but is also controllable using code. Control it using `board.NEOPIXEL` in CircuitPython and `D8` in Arduino.
* **Red status LED** - This little red LED, labeled D13, works as a status LED in the bootloader. Otherwise, it is controllable using code by addressing `board.RED_LED` in CircuitPython, and `D13` in Arduino.
* **Blue status LED** - This little blue LED, labeled Conn, works as a connectivity status LED in Arduino, and is user-controllable in both Arduino and CircuitPython. Control it in code by addressing `board.BLUE_LED` in CircuitPython and `D4` in Arduino.
* **Charge status LED** - The little LED, labeled CHG, below the USB connector is the charge status LED. When no battery is connected, it flashes. When a battery is connected and charging, the LED is steady amber.
