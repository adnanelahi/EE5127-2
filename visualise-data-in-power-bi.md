# Visualise data in Power BI

![End-to-end diagram](https://docs.microsoft.com/en-us/azure/iot-hub/media/iot-hub-get-started-e2e-diagram/4.png)

> Before you start this tutorial, make sure you’ve completed Setup your device. By Setup your device, you set up your IoT device and IoT hub, and deploy a sample application to run on your device. The application sends collected sensor data to your IoT hub.

## What you learn <a href="#what-you-learn" id="what-you-learn"></a>

You learn how to visualize real-time sensor data that your Azure IoT hub receives by Power BI. If you want to try visualize the data in your IoT hub with Web Apps, please see [Use Azure Web Apps to visualize real-time sensor data from Azure IoT Hub](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-live-data-visualization-in-web-apps).

## What you do <a href="#what-you-do" id="what-you-do"></a>

* Create, configure and run a Stream Analytics job for data transfer from your IoT hub to your Power BI account.
* Create and publish a Power BI report to visualize the data.

## What you need <a href="#what-you-need" id="what-you-need"></a>

* Tutorial [Setup your device](https://adnan-elahi.gitbook.io/ee5122/send-telemetry-data-using-raspberry-pi-device) completed which covers the following requirements:
  * An active Azure subscription.
  * An Azure IoT hub under your subscription.
  * A client application that sends messages to your Azure IoT hub.
* A Power BI account. ([Try Power BI for free](https://powerbi.microsoft.com/))

## Create, configure, and run a Stream Analytics job <a href="#create-configure-and-run-a-stream-analytics-job" id="create-configure-and-run-a-stream-analytics-job"></a>

### Create a Stream Analytics job <a href="#create-a-stream-analytics-job" id="create-a-stream-analytics-job"></a>

1. In the Azure portal, click New > Internet of Things > Stream Analytics job.
2.  Enter the following information for the job.

    **Job name**: The name of the job. The name must be globally unique.

    **Resource group**: Use the same resource group that your IoT hub uses.

    **Location**: Use the same location as your resource group.

    **Pin to dashboard**: Check this option for easy access to your IoT hub from the dashboard.
3. Click **Create**.
4. Select **Create** and you should see a _Deployment in progress..._ notification displayed in the top right of your browser window.
5. Check the **Pin to dashboard** box to place your job on your dashboard when the option is available.

### Add an input to the Stream Analytics job <a href="#add-an-input-to-the-stream-analytics-job" id="add-an-input-to-the-stream-analytics-job"></a>

1. Navigate to your Stream Analytics job.
2. Under **Job Topology**, click **Inputs**.
3.  In the **Inputs** pane, click **Add**, and then enter the following information:

    **Input alias**: The unique alias for the input.

    **Source**: Select **IoT hub**.

    **Consumer group**: Select the consumer group you just created.
4. Click **Create**.

### Add an output to the Stream Analytics job <a href="#add-an-output-to-the-stream-analytics-job" id="add-an-output-to-the-stream-analytics-job"></a>

1. Under **Job Topology**, click **Outputs**.
2.  In the **Outputs** pane, click **Add**, and then enter the following information:

    **Output alias**: The unique alias for the output.

    **Sink**: Select **Power BI**.
3. Click **Authorize**, and then sign into your Power BI account.
4.  Once authorized, enter the following information:

    **Group Workspace**: Select your target group workspace.

    **Dataset Name**: Enter a dataset name.

    **Table Name**: Enter a table name.
5. Click **Create**.

### Configure the query of the Stream Analytics job <a href="#configure-the-query-of-the-stream-analytics-job" id="configure-the-query-of-the-stream-analytics-job"></a>

1. Under **Job Topology**, click **Query**.
2. Replace `[YourInputAlias]` with the input alias of the job.
3. Replace `[YourOutputAlias]` with the output alias of the job.
4. Click **Save**.

### Run the Stream Analytics job <a href="#run-the-stream-analytics-job" id="run-the-stream-analytics-job"></a>

In the Stream Analytics job, click **Start** > **Now** > **Start**. Once the job successfully starts, the job status changes from **Stopped** to **Running**.

## Create and publish a Power BI report to visualize the data <a href="#create-and-publish-a-power-bi-report-to-visualize-the-data" id="create-and-publish-a-power-bi-report-to-visualize-the-data"></a>

1. Ensure the sample application is running on your device. If not, you can refer to the tutorials under [Setup your device](https://adnan-elahi.gitbook.io/ee5122/send-telemetry-data-using-raspberry-pi-device).
2. Sign in to your [Power BI](https://powerbi.microsoft.com/en-us/) account.
3. Go to the group workspace that you set when you created the output for the Stream Analytics job.
4.  Click **Datasets**.

    You should see the listed dataset that you specified when you created the output for the Stream Analytics job.
5. Under your workspace, click your dataset to create a visualisation.
6. Create a line chart to show real-time temperature over time.
   1. On the report creation page, add a line chart.
   2. On the **Fields** pane, expand the table that you specified when you created the output for the Stream Analytics job.
   3. Drag **EventEnqueuedUtcTime** to **Axis** on the **Visualizations** pane.
   4.  Drag **temperature** to **Values**.

       Now a line chart is created. The x-axis of chart displays date and time in the UTC time zone. The y-axis displays temperature from the sensor.
7.  Create another line chart to show real-time humidity over time. To do this, follow the same steps above and place **EventEnqueuedUtcTime** on the x-axis and **humidity** on the y-axis.


8. Click **Save** to save the report.

Microsoft also offers the [Power BI mobile apps](https://powerbi.microsoft.com/en-us/documentation/powerbi-power-bi-apps-for-mobile-devices/) for viewing and interacting with your Power BI dashboards and reports on your mobile device.
