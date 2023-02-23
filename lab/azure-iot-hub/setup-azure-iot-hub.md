# Setup Azure IoT Hub

## Create an IoT hub <a href="#create-an-iot-hub" id="create-an-iot-hub"></a>

This section describes how to create an IoT hub using the [Azure portal](https://portal.azure.com/).

1. Sign in to the [Azure portal](https://portal.azure.com/).
2. From the Azure homepage, select the **+ Create a resource** button, and then enter _IoT Hub_ in the **Search the Marketplace** field.

<figure><img src="../../.gitbook/assets/cal63kCZoh.png" alt=""><figcaption><p>Select IoT Hub from the Microsoft Azure Marketplace</p></figcaption></figure>

3. Select **IoT Hub** from the search results, and then select **Create**.
   * On the **Basics** tab, complete the fields as follows:
   * **Subscription**: Select the subscription to use for your hub.
   * **Resource Group**: Select a resource group or create a new one. To create a new one, select **Create new** and fill in the name you want to use. To use an existing resource group, select that resource group. For more information, see [Manage Azure Resource Manager resource groups](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal).
   * **Region**: Select the region in which you want your hub to be located. Select the location closest to you (e.g. UK West). Some features, such as [IoT Hub device streams](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-device-streams-overview), are only available in specific regions. For these limited features, you must select one of the supported regions.
   * **IoT Hub Name**: Enter a name for your hub. This name must be globally unique.
   * **Pricing and scale tier**: Your selected tier. You can choose from several tiers, depending on how many features you want and how many messages you send through your solution per day. The free tier is intended for testing and evaluation. It allows 500 devices to be connected to the hub and up to 8,000 messages per day. Each Azure subscription can create one IoT hub in the free tier.

_Important : Because the IoT hub will be publicly discoverable as a DNS endpoint, be sure to avoid entering any sensitive or personally identifiable information when you name it._&#x20;

![Create an IoT hub.](../../.gitbook/assets/iot-hub-creation.png)

6. Select **Next: Networking** to continue creating your hub.
   * Choose the endpoints that can connect to your IoT Hub. You can select the default setting **Public access**.
7. Select **Next: Management** to continue creating your hub.
   * You can accept the default settings here. If desired, you can modify any of the following fields:
   * **Scale** > **Device-to-cloud partitions**: This property relates the device-to-cloud messages to the number of simultaneous readers of the messages. Most hubs need only four partitions.
8. Select Next: Add-ons to continue to the next screen. You can accept default settings here.
9.  Select **Next: Tags** to continue to the next screen.

    Tags are name/value pairs. You can assign the same tag to multiple resources and resource groups to categorize resources and consolidate billing. For more information, see [Use tags to organize your Azure resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources).
10. Select **Next: Review + create** to review your choices.&#x20;
11. Select **Create** to create your new hub. Creating the hub takes a few minutes.

## Register a device <a href="#register-a-device" id="register-a-device"></a>

* In the [Azure portal](https://portal.azure.com/), open your IoT hub. This should be available under **Resource**.
* Click **Devices** under **Device Management**.

![Add an IoT device in Azure IoT hub.](../../.gitbook/assets/add-iot-device-in-iothub.png)

*   In the Devices pane, click **Add** to add a device to your IoT hub.

    **Device ID**: The ID of the new device. Device IDs are case sensitive.

    **Authentication Type**: Select **Symmetric Key**.

    **Auto Generate Keys**: Check this field.

    **Connect device to IoT Hub**: Click **Enable**.
* Click **Save**.
* After the device is created, open the device in the **Device Explorer** pane.
* Make a note of the primary key of the connection string.

![](../../.gitbook/assets/7\_get-device-connection-string-in-device-explorer-portal.png)

* Make a note of the device connection string, which looks like:
*   `HostName={YourIoTHubName}.azure-devices.net;DeviceId=MyPythonDevice;SharedAccessKey={YourSharedAccessKey}`

    You'll use this value later in the next step.

