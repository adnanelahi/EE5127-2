# Install CircuitPython!

CircuitPython may already be installed on your Feather Sense nRF52840. However, you may want to update the version of CircuitPython already installed on your board. The steps are the same for installing and updating.&#x20;

You only have to install CircuitPython ONCE. After that you are free to code all you like without going through this process again until it's time to upgrade!

### Download the latest version!

The first thing you'll want to do is download the most recent version of CircuitPython.

Always back up your code before installing or updating CircuitPython!

**ALWAYS BACKUP YOUR CODE BEFORE INSTALLING OR UPDATING CIRCUITPYTHON.**&#x20;

[Download the latest CircuitPython](https://adafruit-circuit-python.s3.amazonaws.com/bin/feather\_bluefruit\_sense/en\_GB/adafruit-circuitpython-feather\_bluefruit\_sense-en\_GB-8.1.0.uf2) for the Feather Sense nRF52854 board.

Next, you'll want to plug in your board using a known-good USB data cable. **Make sure the USB cable is a data cable!** Some cables work only for charging and can lead to a lot of frustration.

### Start the UF2 Bootloader

The downloaded bootloader file from the above step should have the extension UF2 (USB Flashing Format) which makes installing and updating CircuitPython a quick and easy process. The bootloader is the mode your board needs to be in for the CircuitPython **.uf2** file you downloaded to work.&#x20;

Find the reset button on your board. It's a small, black button, and on most of the boards, it will be the only button available. It is typically labelled **RESET** or **RST** on the board.&#x20;

![circuitpython\_ResetButton.jpg](https://cdn-learn.adafruit.com/assets/assets/000/048/977/medium800/circuitpython\_ResetButton.jpg?1512750806)

Tap this button twice to enter the bootloader. If it doesn't work on the first try, don't be discouraged. The rhythm of the taps needs to be correct and sometimes it takes a few tries.&#x20;

### Bootloader Mode

Once successful, the board's RGB status LED(s) will flash red and stay green. A new drive will show up on your computer.

The drive will be called _**boardname**_**BOOT** where _**boardname**_ is a reference to your specific board. For example, Feather will have **FEATHERBOOT**

![circuitpython\_FeatherBootWindows.png](https://cdn-learn.adafruit.com/assets/assets/000/048/978/medium800/circuitpython\_FeatherBootWindows.png?1512750806)

Going forward, the bootloader drive will be referred to as the **boot** drive.

The board is now in bootloader mode! This is what you need to install or update CircuitPython.

### Install CircuitPython

Now find the file you downloaded. Drag that file to the **boot** drive on your computer.

![circuitpython\_circuit\_playground\_drag.png](https://cdn-learn.adafruit.com/assets/assets/000/049/259/medium800/circuitpython\_circuit\_playground\_drag.png?1513181045)

The lights should flash again, **boot** will disappear and a **new** drive will show up on your computer called **CIRCUITPY**.

![circuitpython\_adafruit\_gemma\_circuipy.png](https://cdn-learn.adafruit.com/assets/assets/000/048/980/medium800/circuitpython\_adafruit\_gemma\_circuipy.png?1512750807)

Congratulations! You've successfully installed or updated CircuitPython!

### What's the difference between **CIRCUITPY** and _**boardname**_**BOOT**&#x20;

When you plug a CircuitPython board into your computer, your computer will see the board's flash memory as a USB flash drive where files can be stored. When you have successfully installed CircuitPython, you'll see the **CIRCUITPY** drive. When you double-tap the reset button on most boards, you'll see the _**boardname**_**BOOT** drive. You can drag files to the **boot** drives and **CIRCUITPY**, but only **CIRCUITPY** will run your CircuitPython code.

Normally, when you drag a file to a mounted USB drive, the file copies to the drive and then is able to be seen in your file explorer. However, when you drag the CircuitPython UF2 file to the **boot** drive, it seems to disappear, and the drive disconnects. This is normal! The UF2 is essentially an installer file, and does not simply sit on the drive, but installs CircuitPython if the board is in bootloader mode (i.e. the **boot** drive).

You will be able to copy other files to the **boot** drive but they will not run or be accessible to CircuitPython. So make sure that once you're done installing CircuitPython, that you're dragging to and editing files on the **CIRCUITPY** drive!

### References and Acknowledgement

This page is an edited version of [Installing CircuitPython](https://learn.adafruit.com/welcome-to-circuitpython/installing-circuitpython) published by Kattni Rembor in the [Welcome to CircuitPython](https://learn.adafruit.com/welcome-to-circuitpython/overview) guide on the Adafruit website.
