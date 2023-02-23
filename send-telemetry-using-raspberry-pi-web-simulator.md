# Send telemetry using Raspberry Pi web simulator

## Overview of Raspberry Pi web simulator <a href="#overview-of-raspberry-pi-web-simulator" id="overview-of-raspberry-pi-web-simulator"></a>

Click the button to launch Raspberry Pi online simulator.

> [Start Raspberry Pi simulator](https://azure-samples.github.io/raspberry-pi-web-simulator/build/index.html)

There are three areas in the web simulator.

* Assembly area - The default circuit is that a Pi connects with a BME280 sensor and an LED. The area is locked in preview version so currently you cannot do customization.
* Coding area - An online code editor for you to code with Raspberry Pi. The default sample application helps to collect sensor data from BME280 sensor and sends to your Azure IoT Hub. The application is fully compatible with real Pi devices.
* Integrated console window - It shows the output of your code. At the top of this window, there are three buttons.
  * **Run** - Run the application in the coding area.
  * **Reset** - Reset the coding area to the default sample application.
  * **Fold/Expand** - On the right side there is a button for you to fold/expand the console window.

> The Raspberry Pi web simulator is now available in preview version. We'd like to hear your voice in the [Gitter Chatroom](https://gitter.im/Microsoft/raspberry-pi-web-simulator). The source code is public on [Github](https://github.com/Azure-Samples/raspberry-pi-web-simulator).

![Overview of Pi online simulator](https://docs.microsoft.com/en-us/azure/iot-hub/media/iot-hub-raspberry-pi-web-simulator/0\_overview.png)

## Run a sample application on Pi web simulator <a href="#run-a-sample-application-on-pi-web-simulator" id="run-a-sample-application-on-pi-web-simulator"></a>

1. In coding area, make sure you are working on the default sample application. Replace the placeholder in Line 15 with the Azure IoT hub device connection string.&#x20;

![](.gitbook/assets/1\_connectionstring.png)

* Click **Run** or type `npm start` to run the application.
* You should see the following output that shows the sensor data and the messages that are sent to your IoT hub

![](.gitbook/assets/2\_run\_application.png)
