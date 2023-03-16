# BLE Installation

For BLE communication between IoT Gateway and IoT Device (Feather nRF52840 Sense), we are using the Adafruit [Blinka bleio library](https://github.com/adafruit/Adafruit\_Blinka\_bleio) (). The library may not be compatible with the latest Python 3.9. Therefore, ensure that the Python3 version being used on the Raspberry Pi is 3.8.16 (the latest 3.8 version, at the time of this writing). Use the following command to check the version:

```bash
python3 -V
```

```bash
export PATH=$PATH:/home/$USER/.local/bin
```

```bash
python3 -m pip install --upgrade pip
```

```bash
python3 -m pip install wheel
```

```bash
python3 -m pip install --upgrade adafruit-blinka-bleio adafruit-circuitpython-ble
```

```bash
sudo reboot
```

``
