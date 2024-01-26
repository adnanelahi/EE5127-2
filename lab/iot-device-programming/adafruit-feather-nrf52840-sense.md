# Adafruit Feather nRF52840 Sense

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

The Feather nRF52840 Sense is full of all kinds of goodies. Let's take a look!

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

### Microcontroller in Adafruit nRF52840 Feather Sense Board

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

* **Nordic nRF52840 Bluetooth LE processor** - 1 MB of Flash, 256KB RAM, 64 MHz Cortex M4 processor.
* **QSPI flash** - 2MB of internal flash storage for datalogging or CircuitPython code. QSPI requires 6 pins, which are not broken out on the 0.1" pin headers to avoid conflicts. QSPI is neat because it allows you to have 4 data in/out lines instead of just SPI's single line in and single line out. This means that QSPI is _at least_ 4 times faster. But in reality is at least 10x faster because you can clock the QSPI peripheral much faster than a plain SPI peripheral.

### Power Pins

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

* **3V**: This pin is connected to the output of the on board 3.3V regulator. It can be used to supply 3.3V power to external sensors, breakouts or FeatherWings.
* **LIPO Input (Bat)**: This is the voltage supply off the optional LIPO cell that can be connected via the JST PH connector. It is nominally \~3.5-4.2V.
* **VREG Enable (En)**: This pin can be set to GND to disable the 3.3V output from the on board voltage regulator. By default it is set high via a pullup resistor.
* **USB Power (USB)**: This is the voltage supply off USB connector, nominally 4.5-5.2V.

### Analog Pins

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

**I2C Pins**

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

I2C pins on the nRF52840 have 4.7K pullup resistors installed and are connected to all-but-the-microphone sensors. You can connect any other sensors as long as there is not an I2C address collision

**PWM Outputs**

Any GPIO pin can be configured as a PWM output, using the dedicated PWM block.

Three PWM modules can provide up to 12 PWM channels with individual frequency control in groups of up to four channels.
