# CircuitPython Blink Program

Visual Studio Code is the recommended editor for CircuitPython and Python programming in this module.&#x20;

Download and install [Visual Studio Code](https://code.visualstudio.com/) on your laptop.

Install necessary Visual Studio Code (VS Code) extensions. These include "Python", "Visual Studio IntelliCode" from Microsoft and "CircuitPython". Restart VS Code after installing each extension.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Installing extensions in Visual Study Code </p></figcaption></figure>

Open `CIRCUITPY` directory in VS Code

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Copy the following sample code to the `code.py` file. Create a `code.py` file if doesn't exist

```python
import board
import digitalio
import time

led = digitalio.DigitalInOut(board.LED)
led.direction = digitalio.Direction.OUTPUT

while True:
    led.value = True
    time.sleep(0.5)
    led.value = False
    time.sleep(0.5)
```

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Save the `code.py` file on your `CIRCUITPY` drive. The little LED on the board should now be blinking as soon as you save the file provided that the Feahter board is connected and its name, Adafruit Industries LLC: Feather Bluefruit Sense, appears in the bottom right corner of VSCode.

{% hint style="info" %}
Note that under the `while True:` line, the next four lines begin with four spaces to indent them, and they're indented exactly the same amount. All the lines before that have no spaces before the text.
{% endhint %}

{% hint style="info" %}
The CircuitPython code on your board detects when the files are changed or written and will automatically run your code from the start. If you unplug or reset the board before your computer finishes writing the file to your board, you can corrupt the drive.
{% endhint %}

It is a good idea to save the workspace in `CIRCUITPY` drive using `File > Save Workspace as` option. You can give any name to the workspace or simply `feather-sense.code-workspace`.

### References and Acknowledgement

This page is an edited version of [Creating and Editing Code](https://learn.adafruit.com/welcome-to-circuitpython/creating-and-editing-code) published by Kattni Rembor in the [Welcome to CircuitPython](https://learn.adafruit.com/welcome-to-circuitpython/overview) guide on the Adafruit website.
