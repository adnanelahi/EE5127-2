# Sensor Demo

The Feather Sense is full of sensors including proximity, color, temperature, pressure, altitude, magnetometer, accelerometer, gyro, humidity and sound. CircuitPython makes it super simple to get data from these sensors to use however you like. This CircuitPython demo sets up each of the sensors and prints the data from them to the serial console.

Remember, you'll need to have[ CircuitPython installed ](../install-circuitpython.md)before continuing.

To use onboard sensors with CircuitPython, you need to have [relevant libraries](install-libraries.md) in the lib folder on your **CIRCUITPY** drive. Then you need to update **code.py** with the example script.

```python
# SPDX-FileCopyrightText: 2020 Kattni Rembor for Adafruit Industries
#
# SPDX-License-Identifier: MIT
#
"""Sensor demo for Adafruit Feather Sense. Prints data from each of the sensors."""
import time
import array
import math
import board
import audiobusio
from adafruit_apds9960.apds9960 import APDS9960
from adafruit_bmp280 import Adafruit_BMP280_I2C
from adafruit_lis3mdl import LIS3MDL
from adafruit_sht31d import SHT31D

i2c = board.I2C()  # uses board.SCL and board.SDA
# i2c = board.STEMMA_I2C()  # For using the built-in STEMMA QT connector on a microcontroller

# check for LSM6DS33 or LSM6DS3TR-C
try:
    from adafruit_lsm6ds.lsm6ds33 import LSM6DS33 as LSM6DS
    lsm6ds = LSM6DS(i2c)
except RuntimeError:
    from adafruit_lsm6ds.lsm6ds3 import LSM6DS3 as LSM6DS
    lsm6ds = LSM6DS(i2c)

apds9960 = APDS9960(i2c)
bmp280 = Adafruit_BMP280_I2C(i2c)
lis3mdl = LIS3MDL(i2c)
sht31d = SHT31D(i2c)
microphone = audiobusio.PDMIn(board.MICROPHONE_CLOCK, board.MICROPHONE_DATA,
                              sample_rate=16000, bit_depth=16)

def normalized_rms(values):
    minbuf = int(sum(values) / len(values))
    return int(math.sqrt(sum(float(sample - minbuf) *
                             (sample - minbuf) for sample in values) / len(values)))

apds9960.enable_proximity = True
apds9960.enable_color = True

# Set this to sea level pressure in hectoPascals at your location for accurate altitude reading.
bmp280.sea_level_pressure = 1013.25

while True:
    samples = array.array('H', [0] * 160)
    microphone.record(samples, len(samples))

    print("\nFeather Sense Sensor Demo")
    print("---------------------------------------------")
    print(f"Proximity: {apds9960.proximity}")
    print(f"Red: {apds9960.color_data[0]}, Green: {apds9960.color_data[1]}, " +
          f"Blue: {apds9960.color_data[2]}, Clear: {apds9960.color_data[3]}")
    print(f"Temperature: {bmp280.temperature:.1f} C")
    print(f"Barometric pressure: {bmp280.pressure}")
    print(f"Altitude: {bmp280.altitude:.1f} m")
    print(f"Magnetic: {lis3mdl.magnetic[0]:.3f} {lis3mdl.magnetic[1]:.3f} " +
                      f"{lis3mdl.magnetic[2]:.3f} uTesla")
    print(f"Acceleration: {lsm6ds.acceleration[0]:.2f} " +
          f"{lsm6ds.acceleration[1]:.2f} {lsm6ds.acceleration[2]:.2f} m/s^2")
    print(f"Gyro: {lsm6ds.gyro[0]:.2f} {lsm6ds.gyro[1]:.2f} {lsm6ds.gyro[2]:.2f} dps")
    print(f"Humidity: {sht31d.relative_humidity:.1f} %")
    print(f"Sound level: {normalized_rms(samples)}")
    time.sleep(0.3)
```

Set the `sea_level_pressure` to match the sea level pressure at your location in hectoPascals for the most accurate altitude reading. Update the following line:

```
bmp280.sea_level_pressure = 1013.25
```

Let's take a quick look at the code.

First the code imports all the libraries needed, creates the I2C object, and instantiates all of the sensors. There is a try/except for importing either the LSM6DS33 or the LSM6DS3TR-C, with newer versions of the Feather Sense having an LSM6DS3TR-C onboard.

Next is a helper function for getting sound level.

Then the code enables proximity and color sensing on the APDS9960.

Next you set the sea level pressure to match your location if you want a more accurate altitude reading.

Inside the loop, we first gather raw data from the sound sensor.

Then, we print a list of all of the sensor data to the serial console, formatted for appropriate precision and followed by appropriate units where applicable.

Finally, we have a `time.sleep()` so the serial console is readable - without the `sleep` it moves too quickly to read!

That's all there is to reading sensor data on the Feather Sense using CircuitPython! You can easily adapt this example to print only the sensor data you're interested in, or use the sensor data for other purposes. Give it a try!
