# Monitor D2C Messages in Azure IoT Explorer

The Azure IoT explorer is a graphical tool for interacting with devices connected to your IoT hub. After installing the tool on your local machine, you can use it to connect to a hub. You can use the tool to view the telemetry the devices are sending, work with device properties, and invoke commands.

### Install Azure IoT Explorer

Go to [Azure IoT explorer releases](https://github.com/Azure/azure-iot-explorer/releases) and expand the list of assets for the most recent release. Download and install the most recent version of the application. The installation package configures a way for you to launch the application on your platform. For example, in Windows you can launch the application from the Start menu.

### Connect to your hub

The first time you run Azure IoT explorer, you're prompted for your IoT hub's connection string. After you add the connection string, select Save/**Connect**. You can use the tool's settings to switch to another IoT hub by updating the connection string.

### View devices

After saving the connection string select `View devies in this hub.` .&#x20;

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

It displays the Devices list page that lists the device identitites registered with your IoT hub. You can select any entry in the list to see more information.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

On the **Devices** list page you can:

* Select **New** to register a new device with your hub. Then enter a device ID. Use the default settings to automatically generate authentication keys and enable the connection to your hub.
* Select a device and then select **Delete** to delete a device identity. Review the device details before you complete this action to be sure you're deleting the right device identity.

### Interact with a device

On the **Devices** list page, select a value in the **Device ID** column to view the detail page for the registered device.&#x20;

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

If a device is connected and actively sending data, you can view the telemetry on the **Telemetry** tab.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
