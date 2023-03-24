# Deploy an ML Model

### Deploy a real-time endpoint <a href="#deploy-a-real-time-endpoint" id="deploy-a-real-time-endpoint"></a>

There are multiple ways to deploy a model in Azure Machine Learning. One of the simplest ways is to use the designer to automate the deployment process. Use the following steps to deploy a model as a real-time endpoint:

1. Run your completed training pipeline at least once.
2.  After the job completes, at the top of the canvas, select **Create inference pipeline** > **Real-time inference pipeline**.

    The designer converts the training pipeline into a real-time inference pipeline. A similar conversion also occurs in Studio (classic).

    In the designer, the conversion step also registers the trained model to your Azure Machine Learning workspace.
3. Select **Submit** to run the real-time inference pipeline, and verify that it runs successfully.
4. After you verify the inference pipeline, select **Deploy**.
5.  Enter a name for your endpoint and a compute type.

    The following table describes your deployment compute options in the designer:

    | Compute target                 | Used for               | Description                                                                      | Creation                                                        |
    | ------------------------------ | ---------------------- | -------------------------------------------------------------------------------- | --------------------------------------------------------------- |
    | Azure Kubernetes Service (AKS) | Real-time inference    | Large-scale, production deployments. Fast response time and service autoscaling. | User-created. For more information, see Create compute targets. |
    | Azure Container Instances      | Testing or development | Small-scale, CPU-based workloads that require less than 48 GB of RAM.            | Automatically created by Azure Machine Learning.                |

#### Test the real-time endpoint <a href="#test-the-real-time-endpoint" id="test-the-real-time-endpoint"></a>

After deployment completes, you can see more details and test your endpoint:

1. Go to the **Endpoints** tab.
2. Select your endpoint.
3. Select the **Test** tab.
