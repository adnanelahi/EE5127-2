# BLE Custom Service

```python
import time
import board
import random
import adafruit_ble
from adafruit_ble.advertising import Advertisement
from adafruit_ble.services import Service
from adafruit_ble.uuid import StandardUUID
from adafruit_ble.characteristics.int import IntCharacteristic
from adafruit_ble.characteristics import Attribute
from adafruit_ble.advertising.standard import ProvideServicesAdvertisement

# Initialize BLE radio
ble = adafruit_ble.BLERadio()

# GAP: Create an advertisement (device name, appearance)
advertisement = Advertisement()
advertisement.complete_name = "BLE_Sensor"
advertisement.appearance = 0x300  # Generic Temperature Sensor


# GATT: Define a custom Profile with a Service and Characteristic
class TemperatureService(Service):
    """Custom Temperature Sensor Service (GATT)"""
    uuid = StandardUUID(0x1809)  # Standard UUID for Health Thermometer Service

    temperature = IntCharacteristic(
        format_string="h",  # 'h' = signed 16-bit integer
        min_value=-40, 
        max_value=125,
        uuid=StandardUUID(0x2A1C),  # UUID for Temperature Measurement
        properties=IntCharacteristic.READ | IntCharacteristic.NOTIFY,
        read_perm=Attribute.OPEN,
        write_perm=Attribute.NO_ACCESS,
        initial_value=25
    )

# Create the service instance
temperature_service = TemperatureService()

# Create an advertisement that includes the service
advertisement = ProvideServicesAdvertisement(TemperatureService)

# Add the service to BLE stack
ble.services = [temperature_service]

# **Check if already advertising before starting**
ble.start_advertising(advertisement)
print("Started advertising as BLE_Sensor")

print("Advertising as BLE Sensor...")

while True:
    if ble.connected:
        print("Connected! Sending temperature data...")

        while ble.connected:
            # Simulate temperature changes
            new_temp = random.randint(20, 30)
            temperature_service.temperature = new_temp  # Update characteristic value
            print(f"Updated Temperature: {new_temp}°C")

            time.sleep(5)  # Send new value every 5 seconds

    else:
        print("Waiting for connection...")
        # **Check if already advertising before starting**
        if not ble.advertising:
            ble.start_advertising(advertisement)
            print("Started advertising as BLE_Sensor")
        time.sleep(2)

```
