# Transmit Sensor Data using Gateway Device

### In this article

In this quickstart, you send telemetry from a physical Raspberry Pi device through Azure IoT Hub to a back-end application for processing. IoT Hub is an Azure service that enables you to ingest high volumes of telemetry from your IoT devices into the cloud for storage or processing. This quickstart uses a pre-written Python application to send the telemetry. Before you run this application, you create an IoT hub and register a device with the hub.

## Prerequisites <a href="#prerequisites" id="prerequisites"></a>

* An Azure account with an active subscription. [Create one for free](https://azure.microsoft.com/free/?ref=microsoft.com\&utm\_source=microsoft.com\&utm\_medium=docs\&utm\_campaign=visualstudio).
* [Python 3.7+](https://www.python.org/downloads/). For other versions of Python supported, see [Azure IoT Device Features](https://github.com/Azure/azure-iot-sdk-python/tree/master/azure-iot-device#azure-iot-device-features).
* [A sample Python project](https://github.com/Azure-Samples/azure-iot-samples-python/archive/master.zip).
* Port 8883 open in your firewall. The device sample in this quickstart uses MQTT protocol, which communicates over port 8883. This port may be blocked in some corporate and educational network environments. For more information and ways to work around this issue, see [Connecting to IoT Hub (MQTT)](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-mqtt-support#connecting-to-iot-hub).

## Install Python Library for Azure IoT Device

Install **azure.iot.device** using the following command in the terminal. Click Terminal > New Terminal in VS Code and run the following command.

<pre class="language-python"><code class="lang-python"><strong>python3 -m pip install azure.iot.device
</strong></code></pre>

Use of `python3` -m option with `pip` command ensures that the correct version of `pip` is used for package installation. In the above command `pip` version corresponding to the default python3 will be used.&#x20;

### Download and organise sample code

* Download the[ sample Python project](https://github.com/Azure-Samples/azure-iot-samples-python/archive/master.zip) in Raspberry Pi.&#x20;
* Right click the downloaded archive (.zip) and select **Extract here**
* Rename the extracted folder _azure-iot-samples-python-master_ to azure-iot-samples-python and move it to the _Documents_ folder in Raspberry Pi.
* Open _azure-iot-samples-python_ folder in VS Code and navigate to **azure-iot-samples-python/iot-hub/Quickstarts/simulated-device/SimulatedDeviceSync.py**.
* Replace the value of variable, `CONNECTION_STRING`, with the primary connection string copied from [IoT Hub Setup](setup-azure-iot-hub.md) process in `SimulatedDeviceSync.py`.

<pre class="language-python" data-overflow="wrap"><code class="lang-python"># Copyright (c) Microsoft. All rights reserved.
# Licensed under the MIT license. See LICENSE file in the project root for full license information.
import os
import random
import time
from azure.iot.device import IoTHubDeviceClient, Message

# The device connection authenticates your device to your IoT hub. The connection string for 
# a device should never be stored in code. For the sake of simplicity we're using an environment 
# variable here. If you created the environment variable with the IDE running, stop and restart 
# the IDE to pick up the environment variable.
#
# You can use the Azure CLI to find the connection string:
# az iot hub device-identity show-connection-string --hub-name {YourIoTHubName} --device-id MyNodeDevice --output table

<strong>#REPLACE os.getenv("IOTHUB_DEVICE_CONNECTION_STRING") with primary connection string copied from IoT Hub setup process.
</strong>CONNECTION_STRING = os.getenv("IOTHUB_DEVICE_CONNECTION_STRING")

# Define the JSON message to send to IoT Hub.
TEMPERATURE = 20.0
HUMIDITY = 60
MSG_TXT = '{{"temperature": {temperature},"humidity": {humidity}}}'


def run_telemetry_sample(client):
    # This sample will send temperature telemetry every second
    print("IoT Hub device sending periodic messages")

    client.connect()

    while True:
        # Build the message with simulated telemetry values.
        temperature = TEMPERATURE + (random.random() * 15)
        humidity = HUMIDITY + (random.random() * 20)
        msg_txt_formatted = MSG_TXT.format(temperature=temperature, humidity=humidity)
        message = Message(msg_txt_formatted)

        # Add a custom application property to the message.
        # An IoT hub can filter on these properties without access to the message body.
        if temperature > 30:
            message.custom_properties["temperatureAlert"] = "true"
        else:
            message.custom_properties["temperatureAlert"] = "false"

        # Send the message.
        print("Sending message: {}".format(message))
        client.send_message(message)
        print("Message successfully sent")
        time.sleep(10)


def main():
    print("IoT Hub Quickstart #1 - Simulated device")
    print("Press Ctrl-C to exit")

    # Instantiate the client. Use the same instance of the client for the duration of
    # your application
    client = IoTHubDeviceClient.create_from_connection_string(CONNECTION_STRING)

    # Run Sample
    try:
        run_telemetry_sample(client)
    except KeyboardInterrupt:
        print("IoTHubClient sample stopped by user")
    finally:
        # Upon application exit, shut down the client
        print("Shutting down IoTHubClient")
        client.shutdown()

if __name__ == '__main__':
    main()
</code></pre>

* Run&#x20;
* You will see the following output in the terminal.

![](../../.gitbook/assets/vncviewer\_EdhWaA1agd.png)

You can monitor [Monitor D2C (device-to-cloud) messages in VS code](monitor-d2c-messages-in-vs-code.md). A sample output is shown below.

![](../../.gitbook/assets/Code\_XyGoFDuwlg.png)
