# Deploy an ML Model

### Deploy a real-time endpoint <a href="#deploy-a-real-time-endpoint" id="deploy-a-real-time-endpoint"></a>

There are multiple ways to deploy a model in Azure Machine Learning. One of the simplest ways is to use the designer to automate the deployment process. Use the following steps to deploy a model as a real-time endpoint:

1. Run your completed training pipeline at least once.
2. After the job completes, at the top of the canvas, select **Create inference pipeline** > **Real-time inference pipeline**.
3.

    <figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

    The designer converts the training pipeline into a real-time inference pipeline. A similar conversion also occurs in Studio (classic).

    In the designer, the conversion step also registers the trained model to your Azure Machine Learning workspace.
4. Your new pipeline looks like this.

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

5. Select **Submit** to run the real-time inference pipeline, and verify that it runs successfully.
6. After you verify the inference pipeline, select **Deploy**.

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

7. Enter a name for your endpoint and a compute type.
8. In the dialog box that appears, you can select from any existing Azure Kubernetes Service (AKS) Compute clusters to deploy your model to. If you don't have an AKS cluster, use the following steps to create one.
9. Select **Compute** in the left navigation to go to the **Compute** page.
10. On the navigation ribbon, select **Kubernetes Clusters** > + **New > AksCompute**

<figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

11. Select the Region and specifications for the compute instance.

<figure><img src="../../.gitbook/assets/Screenshot 2024-03-22 013624.png" alt=""><figcaption></figcaption></figure>

12. Click **Create**.

<figure><img src="../../.gitbook/assets/Screenshot 2024-03-22 013704.png" alt=""><figcaption></figcaption></figure>

13. After completing the above steps, go back to the inference pipeline and complete the Deploy dialogue box as shown in Step 6. Creation of the endpoint may take a while. The endpoint will be **Transitioning** while it is being created. Wait until the **Deployment state** of the endpoint changes from **Transitioning** to **Healthy**.

#### Test the real-time endpoint <a href="#test-the-real-time-endpoint" id="test-the-real-time-endpoint"></a>

After deployment completes, you can see more details and test your endpoint:

1. Go to the **Endpoints** tab.
2. Select your endpoint.
3. Select the Details tab and copy the Swagger URI, which looks like as below: [`http://XX.XXX.XX.XXX/api/v1/service/ENDPOINT/swagger.json`](http://20.162.73.242/api/v1/service/occupancymodel-ep1245/swagger.json)
4. Paste the URI from the above step in the browser to see the contents of `swagger.json`. The contents of `swagger.json` describe the REST API endpoints of the deployed model or web service. It defines how a client can interact with the deployed model. Copy these contents.
5. Download and install [Postman app](https://www.postman.com/downloads/). This app will allow you to test deployed model by sending sample inputs to the model and receive results from the model.
6. Open the Postman app and click on Import. Paste the contents of swagger.json from Step 4 into the text box.
7.

    <figure><img src="../../.gitbook/assets/Screenshot 2025-03-21 153012.png" alt=""><figcaption></figcaption></figure>
8. The above step should import the endpoint into the Postman app workspace. Select the model name and set the variable initial and current value of `baseURL` under the `Variables` tab to the REST endpoint URL of the endpoint. You can obtain this from the **Consume** tab of the endpoint in Machine Learning Studio. Note that baseURL should be set to only the IP address part of the REST endpoint.&#x20;
9. Next, select "**Run ML Service**" in the Postman app. You will need to expand all folder hierarchies in the left-side navigation panel to locate the "**Run ML Service**" option. Once selected, navigate to the **Authorisation** tab and select **Bearer Token** from the **Type** dropdown
10. Paste the **Primary Key** obtained from the Azure ML endpoint's Consume tab into the **Token** field.
11. Click on the **Body** tab. Select raw and ensure the format is set to JSON.
12. Enter the sample input data for your model and click the **Send** button. Postman will send the request to the Azure ML model endpoint. If the request is successful, you should receive a **200 OK** response with a JSON response body containing the model's predictions.

