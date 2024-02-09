# Built-In Modules

There is a set of modules used in most CircuitPython programs. One or more of these modules is always used in projects involving hardware. Often hardware requires installing a separate library from the Adafruit CircuitPython Bundle. But, if you try to find `board` or `digitalio` in the same bundle, you'll come up lacking. So, where do these modules come from? They're built into CircuitPython! You can find an comprehensive list of built-in CircuitPython modules and the technical details of their functionality from CircuitPython [here](https://circuitpython.readthedocs.io/en/latest/shared-bindings/index.html#modules) and the Python-like modules included [here](https://circuitpython.readthedocs.io/en/latest/docs/library/index.html). However, **not every module is available for every board** due to size constraints or hardware limitations. How do you find out what modules are available for your board?

There are two options for this. You can check the [support matrix](https://circuitpython.readthedocs.io/en/latest/shared-bindings/support\_matrix.html), and search for your board by name. Or, you can use the REPL.

Plug in your board, connect to the serial console and enter the REPL. Type the following command.

<figure><img src="../../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
