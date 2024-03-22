# Deploy an ML Model

### Deploy a real-time endpoint <a href="#deploy-a-real-time-endpoint" id="deploy-a-real-time-endpoint"></a>

There are multiple ways to deploy a model in Azure Machine Learning. One of the simplest ways is to use the designer to automate the deployment process. Use the following steps to deploy a model as a real-time endpoint:

1. Run your completed training pipeline at least once.
2. After the job completes, at the top of the canvas, select **Create inference pipeline** > **Real-time inference pipeline**.
3.

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

    The designer converts the training pipeline into a real-time inference pipeline. A similar conversion also occurs in Studio (classic).

    In the designer, the conversion step also registers the trained model to your Azure Machine Learning workspace.
4. Your new pipeline looks like this.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

5. Select **Submit** to run the real-time inference pipeline, and verify that it runs successfully.
6. After you verify the inference pipeline, select **Deploy**.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

7. Enter a name for your endpoint and a compute type.
8. In the dialog box that appears, you can select from any existing Azure Kubernetes Service (AKS) Compute clusters to deploy your model to. If you don't have an AKS cluster, use the following steps to create one.
9. Select **Compute** in the left navigation to go to the **Compute** page.
10. On the navigation ribbon, select **Kubernetes Clusters** > + **New**

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

11. Select the Region and specifications for the compute instance.

<figure><img src="../../.gitbook/assets/Screenshot 2024-03-22 013624.png" alt=""><figcaption></figcaption></figure>

12. Click **Create**.

<figure><img src="../../.gitbook/assets/Screenshot 2024-03-22 013704.png" alt=""><figcaption></figcaption></figure>

13. After completing the above steps, go back to the inference pipeline and complete the Deploy dialogue box as shown in Step 6. Creation of the endpoint may take a while. The endpoint will be **Transitioning** while it is being created.&#x20;

#### Test the real-time endpoint <a href="#test-the-real-time-endpoint" id="test-the-real-time-endpoint"></a>

After deployment completes, you can see more details and test your endpoint:

1. Go to the **Endpoints** tab.
2. Select your endpoint.
3. Select the **Test** tab.
