# BLE Eddystone Beacon

```python
import time
from adafruit_ble import BLERadio
from adafruit_ble_eddystone import uid, url

# ------------------------ BLE RADIO ------------------------
# BLERadio is the CircuitPython BLE stack entry point.
# It handles advertising and (if needed) connections.
ble = BLERadio()
ble.name = "EE5127EddystoneBeacon"  # optional: set a custom device name

print(":".join(f"{b:02X}" for b in ble.address_bytes))  # print the board's BLE address (for convenience)

# ------------------------ CONFIG ---------------------------
# INSTANCE_ID must be EXACTLY 6 bytes for Eddystone-UID.
# Using the board's BLE address is a convenient, unique default.
# (You can replace this with your own stable 6-byte value.)
INSTANCE_ID = ble.address_bytes              # 6 bytes (48-bit BLE address)
# Example custom instance instead:
# INSTANCE_ID = bytes.fromhex("A1B2C3D4E5F6")

# NAMESPACE_ID must be EXACTLY 10 bytes for Eddystone-UID.
# Your library supports `namespace_id=...`, so we can set it explicitly.
# Choose a project/company/site-wide namespace so all your beacons "belong together".
NAMESPACE_ID = b"CircuitPy!"                   # 10 bytes here (yes, exactly 10 chars)

# Measured power = calibrated RSSI at ~1 meter.
# Apps use this to estimate distance from RSSI.
# Typical values are around -59 dBm (but CALIBRATE with your phone!).
TX_POWER_DBM = -30

# ------------------------ HELPERS --------------------------
def dbm_to_byte(dbm: int) -> int:
    """
    Convert a signed dBm value (-128..127) to the 0..255 raw byte
    the Eddystone helper expects. This avoids 'value must fit in 1 byte'
    errors when you pass negative dBm values like -59.
    (Two's complement mapping: -59 -> 197 (0xC5))
    """
    x = int(round(dbm))
    if x < -128:
        x = -128
    if x > 127:
        x = 127
    return (x + 256) % 256

# Sanity checks (fail early with a clear message if lengths are off)
assert len(INSTANCE_ID) == 6,  "Eddystone Instance ID must be exactly 6 bytes"
assert len(NAMESPACE_ID) == 10, "Eddystone Namespace ID must be exactly 10 bytes"

# Convert signed dBm to the raw one-byte format expected by the library
TX_POWER_BYTE = dbm_to_byte(TX_POWER_DBM)

# ------------------------ EDDYSTONE FRAMES -----------------
# UID frame: carries a 10-byte Namespace + 6-byte Instance.
# Why: ideal for proximity/zone IDs; receiver compares RSSI vs. tx_power to estimate distance.
eddystone_uid = uid.EddystoneUID(
    INSTANCE_ID,
    namespace_id=NAMESPACE_ID,  # your custom 10-byte Namespace
    tx_power=TX_POWER_BYTE      # raw byte form of measured power (avoid negative-int errors)
)

# (Optional) URL frame: broadcasts a short link.
# Why: handy for "tap to open" behavior in scanners; not needed for proximity, but nice to include.
eddystone_url = url.EddystoneURL("https://adafru.it/discord")

# ------------------------ ADVERTISING LOOP -----------------
# Strategy: alternate short bursts of UID and URL advertising.
# Why alternate? A single radio can only send one advertising payload at a time.
# Short bursts (≈0.5 s) let scanners see both frames without waiting too long.
# interval=0.1 -> ~100 ms advertising interval (good for phones to discover quickly).
while True:
    # --- UID burst (proximity / zone identification) ---
    ble.start_advertising(eddystone_uid, interval=0.1)  # non-connectable by default
    time.sleep(0.6)                                     # send several packets (~0.6 s is plenty)
    ble.stop_advertising()

    # --- URL burst (optional) ---
    ble.start_advertising(eddystone_url, interval=0.1)
    time.sleep(0.6)
    ble.stop_advertising()

    # Pause between cycles.
    # Why: reduces duty cycle & power, and prevents constant radio use.
    # Adjust to taste (shorter = more responsive; longer = lower power).
    time.sleep(4.0)

```
