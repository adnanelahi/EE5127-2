# Board Pins

CircuitPython is designed to run on microcontrollers and allows you to interface with all kinds of sensors, inputs and other hardware peripherals. Hardware peripherals are interfaced or connected to a  microcontroller using its input/output pins. CircuitPython code requires various modules, such as `board` or `digitalio` to access or control these pins in a program. You import these modules and then use them in your code.&#x20;

### `import board`

The `board` module is built into CircuitPython and is used to provide access to a series of board-specific objects, including pins. Therefore, the import board will almost always be part of your code when you are using any kind of hardware peripherals wired up to your microcontroller board.

Take a look at your microcontroller board. You'll notice that next to the pins are pin labels. You can always access a pin by its pin label. However, there are almost always multiple names for a given pin.

To see all the available board-specific objects and pins for your board, you can enter the REPL (`>>>`) and run the following commands:

Here is the output for the Feather Sense board. **If you have a different board, this list might vary, based on the board.**

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

You can use the pin names on the physical board, regardless of whether they seem to be specific to a certain protocol. For example, you do not _have_ to use the SDA pin for I2C - you can use it for a button or LED.

Note that most of the pins are named in an IO# style, such as **IO1** and **IO2**. Those pins on the physical board are labeled only with a number, so an easy way to know how to access them in CircuitPython, is to run those commands in the REPL and find the pin naming scheme.

If your code is failing to run because it can't find a pin name you provided, verify that you have the proper pin name by running these commands in the REPL.

### I2C, SPI, and UART

You'll also see there are often (_**but not always!**_) three special board-specific objects included: `I2C`, `SPI`, and `UART` - each one is for the default pin-set used for each of the three common protocol busses they are named for. These are called _singletons_.

What's a singleton? When you create an object in CircuitPython, you are _instantiating_ ('creating') it. Instantiating an object means you are creating an instance of the object with the unique values that are provided, or "passed", to it.

For example, When you instantiate an I2C object using the `busio` module, it expects two pins: clock and data, typically SCL and SDA. It often looks like this:

```python
i2c = busio.I2C(board.SCL, board.SDA)
```

Then, you pass the I2C object to a driver for the hardware you're using. For example, if you were using the TSL2591 light sensor and its CircuitPython library, the next line of code would be:

```python
tsl2591 = adafruit_tsl2591.TSL2591(i2c)
```

However, CircuitPython makes this simpler by including the `I2C` singleton in the `board` module. Instead of the two lines of code above, you simply provide the singleton as the I2C object. So if you were using the TSL2591 and its CircuitPython library, the two above lines of code would be replaced with:

```python
tsl2591 = adafruit_tsl2591.TSL2591(board.I2C())
```

The board.I2C(), board.SPI(), and board.UART() singletons do not exist on all boards. They exist if there are board markings for the default pins for those devices.

This eliminates the need for the `busio` module, and simplifies the code. Behind the scenes, the `board.I2C()`  object is instantiated when you call it, but not before, and on subsequent calls, it returns the same object. Basically, it does not create an object until you need it, and provides the same object every time you need it. You can call `board.I2C()` as many times as you like, and it will always return the same object.

The UART/SPI/I2C singletons will use the 'default' bus pins for each board - often labeled as RX/TX (UART), MOSI/MISO/SCK (SPI), or SDA/SCL (I2C). &#x20;
