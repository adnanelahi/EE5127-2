---
description: >-
  Continuously broadcasts a BLE advertisement named “EE5127” that includes a
  custom Manufacturer Specific Data (AD 0xFF: 00 08 03 04) at ~100 ms intervals,
  indefinitely.
---

# BLE Advertisement

```python

# type: ignore
import time
import board
import adafruit_ble
from adafruit_ble.advertising import Advertisement
from adafruit_ble import BLERadio

# Initialize BLE radio (GAP)
ble = BLERadio()
ble.name = "EE5127"  # Set the device name

# --- GAP: Create an Advertisement (Broadcasting Information) ---
advertisement = Advertisement()
advertisement.complete_name = "EE5127"  #  Correctly sets the device name

# GAP: Add manufacturer-specific data manually
manufacturer_data = bytearray([0x00, 0x08, 0x03, 0x04])  # Example of custom data
advertisement.data_dict[0xFF] = manufacturer_data

# --- GAP: Start BLE Advertising ---

ble.start_advertising(advertisement, interval=0.1)
print("Starting to broadcast")

# Keep broadcasting indefinitely
while True:
    time.sleep(1)

```
