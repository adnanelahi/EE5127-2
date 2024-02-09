# BLE Communication

For BLE communication between IoT Gateway and IoT Device (Feather nRF52840 Sense), we are using the Adafruit [Blinka bleio library](https://github.com/adafruit/Adafruit\_Blinka\_bleio) ().&#x20;

Create a folder for EE5127 lab work and within this folder create a new [Virtual Environment. ](https://www.geeksforgeeks.org/python-virtual-environment/)

Change the current working directory to the newly created folder using the following command. This command will need to be executed every time Raspberry Pi is started for Python work

```bash
cd /home/Documents/ee5127
```

Use the following command to create the new Virtual Environment within the above folder.

```python
python3 -m venv env
```

Activate the following by running the following command in the same Terminal. This command will need to be executed every time Raspberry Pi is started for Python work.

```
source env/bin/activate
```

Install the BLE library by running the following commands:

```bash
pip install wheel
```

```bash
pip install --upgrade adafruit-blinka-bleio adafruit-circuitpython-ble
```

```bash
sudo reboot
```

Open VS Code, select a Python 3 interpreter by opening the Command Palette (Ctrl+Shift+P), start typing the Python: Select Interpreter command to search, then select the command. Select the interpreter that has the prefix of `env` so that VS Code uses the Python version where we have installed BLE libraries.

### BLE Peripheral Device

Run the following code on Feather Sense to transmit data using BLE

```python
# Provide a remote sensing service over Bluetooth Low-Energy (BLE).

# ----------------------------------------------------------------
# Import the standard Python time functions.
import time
import digitalio
import board

# Import the Adafruit Bluetooth library.  Technical reference:
# https://circuitpython.readthedocs.io/projects/ble/en/latest/api.html
from adafruit_ble import BLERadio
from adafruit_ble.advertising.standard import ProvideServicesAdvertisement
from adafruit_ble.services.nordic import UARTService

# ----------------------------------------------------------------
# Initialize global variables for the main loop.
ledpin= digitalio.DigitalInOut(board.BLUE_LED)
ledpin.direction = digitalio.Direction.OUTPUT

ble = BLERadio()
uart = UARTService()
advertisement = ProvideServicesAdvertisement(uart)

# Flags for detecting state changes.
advertised = False
connected  = False

# The sensor sampling rate is precisely regulated using the following timer variables.
sampling_timer    = 0.0
last_time         = time.monotonic()
sampling_interval = 0.10

# ----------------------------------------------------------------
# Begin the main processing loop.

while True:

    # Read the accelerometer at regular intervals.  Measure elapsed time and
    # wait until the update timer has elapsed.
    now = time.monotonic()
    interval = now - last_time
    last_time = now
    sampling_timer -= interval
    if sampling_timer < 0.0:
        sampling_timer += sampling_interval
        x, y, z = (10,20,30)
    else:
        x = None

    if not advertised:
        ble.start_advertising(advertisement)
        print("Waiting for connection.")
        advertised = True

    if not connected and ble.connected:
        print("Connection received.")
        connected = True
        ledpin.value = True
        
    if connected:
        if not ble.connected:
            print("Connection lost.")
            connected = False
            advertised = False
            ledpin.value = False            
        else:
            if x is not None:
                uart.write(b"%.3f,%.3f,%.3f\n" % (x, y, z))
```

### BLE Central Device

Run the following code on Raspberry Pi to read data using BLE.

```python
 ----------------------------------------------------------------
# Import the Adafruit Bluetooth library, part of Blinka.  Technical reference:
# https://circuitpython.readthedocs.io/projects/ble/en/latest/api.html

from adafruit_ble import BLERadio
from adafruit_ble.advertising.standard import ProvideServicesAdvertisement
from adafruit_ble.services.nordic import UARTService

# ----------------------------------------------------------------
# Initialize global variables for the main loop.
ble = BLERadio()
uart_connection = None

# ----------------------------------------------------------------
# Begin the main processing loop.

while True:
    if not uart_connection:
        print("Trying to connect...")
        # Check for any device advertising services
        for adv in ble.start_scan(ProvideServicesAdvertisement):
            # Print name of the device
            name = adv.complete_name
            if name:
                print(name)
            # Print what services that are being advertised
            for svc in adv.services:
                print(str(svc))
            # Look for UART service and establish connection
            if UARTService in adv.services:
                uart_connection = ble.connect(adv)
                print("Connected")
                break
        ble.stop_scan()
    # Once connected start receiving data
    if uart_connection and uart_connection.connected:
        uart_service = uart_connection[UARTService]
        while uart_connection.connected:
            print(uart_service.readline().decode("utf-8").rstrip())
```
