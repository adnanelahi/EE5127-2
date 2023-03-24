# Integrate ML Model with IoT Hub

### Add a machine learning model to stream analytics job <a href="#add-a-machine-learning-model-to-your-job" id="add-a-machine-learning-model-to-your-job"></a>

You can add Azure Machine Learning functions to your Stream Analytics job directly from the Azure portal

#### Azure portal <a href="#azure-portal" id="azure-portal"></a>

1. Navigate to your Stream Analytics job in the Azure portal, and select **Functions** under **Job topology**. Then, select **Azure Machine Learning Service** from the **+ Add** dropdown menu.
2. Fill in the **Azure Machine Learning Service function** form with the following property values:

The following table describes each property of Azure Machine Learning Service functions in Stream Analytics.

| Property                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Function alias                            | Enter a name to invoke the function in your query.                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Subscription                              | Your Azure subscription.                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Azure Machine Learning workspace          | The Azure Machine Learning workspace you used to deploy your model as a web service.                                                                                                                                                                                                                                                                                                                                                                                                                |
| Endpoint                                  | The web service hosting your model.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Function signature                        | The signature of your web service inferred from the API's schema specification. If your signature fails to load, check that you have provided sample input and output in your scoring script to automatically generate the schema.                                                                                                                                                                                                                                                                  |
| Number of parallel requests per partition | <p>This is an advanced configuration to optimize high-scale throughput. This number represents the concurrent requests sent from each partition of your job to the web service. Jobs with six streaming units (SU) and lower have one partition. Jobs with 12 SUs have two partitions, 18 SUs have three partitions and so on.</p><p>For example, if your job has two partitions and you set this parameter to four, there will be eight concurrent requests from your job to your web service.</p> |
| Max batch count                           | This is an advanced configuration for optimizing high-scale throughput. This number represents the maximum number of events be batched together in a single request sent to your web service.                                                                                                                                                                                                                                                                                                       |

### Calling machine learning endpoint from your query <a href="#calling-machine-learning-endpoint-from-your-query" id="calling-machine-learning-endpoint-from-your-query"></a>

When your Stream Analytics query invokes an Azure Machine Learning UDF, the job creates a JSON serialized request to the web service. The request is based on a model-specific schema that Stream Analytics infers from the endpoint's swagger.

The following Stream Analytics query is an example of how to invoke an Azure Machine Learning UDF:

```
SELECT udf.score(<model-specific-data-structure>)
INTO output
FROM input
WHERE <model-specific-data-structure> is not null
```

More specific query is given below:

```
WITH Ip AS
(
SELECT 
    "isRain",
    "temperature",
    "humidity"
FROM
[iothubinput]
)
SELECT udf.weathermodel(Ip)
INTO
    [iothubbloboutput]
FROM
    Ip
```

If your input data sent to the ML UDF is inconsistent with the schema that is expected, the endpoint will return a response with error code 400, which will cause your Stream Analytics job to go to a failed state. It's recommended that you enable resource logs for your job, which will enable you to easily debug and troubleshoot such problems. Therefore, it's strongly recommended that you:
