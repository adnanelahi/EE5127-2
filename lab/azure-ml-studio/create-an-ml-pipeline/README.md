# Create an ML Pipeline

## Prerequisites

1. [Create Resource Group](../create-resource-group.md)
2. [Create an ML Workspace](../create-ml-workspace.md)
3. [Create a Storage Account](../create-storage-account.md)
4. [Create a Datastore](../create-datastore.md)
5. [Create Datasets](../create-dataset.md)

## Creating an ML Pipeline&#x20;

1. Select Pipeline in left pane of Azure ML Studio and click on "Create a new pipeline using classic prebuilt components".

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/90b6dd5c-a658-46cd-91fe-d04d352c146c/File.jpeg?tl\_px=0,132\&br\_px=746,552\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=132,139)

2. Creating a pipeline will create a blank canvas for connecting various components of ML. Click "ph\_and\_hr\_dataset" or another dataset that you have uploaded and drag it to the blank canvas. Note that the "Data" tab below will show all available datasets that were uploaded and the "Components" tab will display all ML components that are available for use in the ML pipeline.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/ed13dbb4-f4d7-457a-8ad9-e9412981e0d7/File.jpeg?tl\_px=0,193\&br\_px=746,613\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=72,152)

3. Before proceeding further, set up a compute instance. Follow the tutorial on "[Create Compute Instance](create-compute-instance.md)"
4. Right click on the dataset block and click "Preview data".

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/a50b4ce9-76a3-4d51-9263-5412d4f9c68a/File.jpeg?tl\_px=188,193\&br\_px=934,613\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,252)

4. Preview will show not only a preview of the data but it allows some visualisations of the data as well.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/37cc2376-20ce-4b5d-8f84-f44add03345e/File.jpeg?tl\_px=4,0\&br\_px=750,420\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,52)

5. Click on the Profile tab as shown in the image below.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/2d7d9ec7-476f-43ab-a772-a06ad3f1383f/File.jpeg?tl\_px=125,21\&br\_px=871,441\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,139)

6. The profile option shows the histogram of all features in the data.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/6e3fb9df-f6d2-40c1-999c-ea84345a8cab/File.jpeg?tl\_px=273,193\&br\_px=1019,613\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=494,153)

7. Click on any one of the feature row and it will display the Boxplot of that particular feature.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/49c6e220-66a0-4db2-b497-8740e96ca600/File.jpeg?tl\_px=273,191\&br\_px=1019,611\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=520,139)

8. Click on the next feature and observe the boxplot visualisation.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/9daceb74-0459-4b35-a096-3e6311946e25/File.jpeg?tl\_px=273,184\&br\_px=1019,604\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=523,139)

9. Select the components and connect them together as shown in the image below.&#x20;

<figure><img src="../../../.gitbook/assets/msedge_IWeTsCxLwn (1).png" alt=""><figcaption></figcaption></figure>

10. Double click the "Linear Regression" component and select the hyperparameters of the Linear Regression algorithms. Use the Solution method "Gradient descent" instead of "Ordinary Least Squares". Other parameters can be left at default values for this experiment.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/d771b63a-13d5-4829-b5d2-0251941a0501/File.jpeg?tl\_px=273,0\&br\_px=1019,420\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=436,87)

11. Double click the "Split Data" component and change "Fraction of rows in the first output dataset" field to 0.8.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/83160adf-be6d-4028-b168-d473b8d1d490/File.jpeg?tl\_px=57,111\&br\_px=803,531\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,139)

12. Set the "Random seed" value to 1.&#x20;

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/2139cd5b-7d3d-4e54-81e1-64599bee6acb/File.jpeg?tl\_px=273,0\&br\_px=1019,420\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=449,84)

13. Next, double click "Train Model" and click on "Edit column".

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-08/26a83090-bd1f-4620-bcdc-8d7b3e65845a/ascreenshot.jpeg?tl\_px=273,14\&br\_px=1019,434\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=486,139)

14. Click the "Enter column name" field and enter the name of the outcome column e.g. pH for the pH dataset.&#x20;

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-08/0e00b216-500c-4e28-9d27-8445468762b7/ascreenshot.jpeg?tl\_px=273,0\&br\_px=1019,420\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=280,116)

15. Type "pH" and click "Save".

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-08/63d0171d-bb89-43fa-856f-f6862a559de9/ascreenshot.jpeg?tl\_px=273,0\&br\_px=1019,420\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=442,83)

16. Click "Submit"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-08/424be325-9585-462b-9107-e6dfcce5ada5/ascreenshot.jpeg?tl\_px=273,0\&br\_px=1019,420\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=493,48)

17. After clicking "Submit" in the previous step, a pop-up will appear asking to create a new "Experiment" or select "Existing Experiment". Click "Create new"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-08/c673a518-c09e-4e88-96d1-6d14737e5c7c/ascreenshot.jpeg?tl\_px=69,0\&br\_px=815,420\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,108)

18. Click the "Enter new experiment name" field and type "predicting-ph-from-hr"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-08/346d1711-f3a3-40e4-8bf0-74da3777fc26/ascreenshot.jpeg?tl\_px=0,193\&br\_px=746,613\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,243)

19. Click "Submit"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-08/ef9131a4-e16e-4d53-bf16-504c8dbea23c/ascreenshot.jpeg?tl\_px=224,193\&br\_px=970,613\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,238)

20. Once the job has been submitted. Select "Pipelines" in the left pane of the Azure ML Studio and select the submitted pipeline under the "Pipeline jobs" tab.&#x20;
21. Right click "Scored dataset" and select "Preview data"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-08/414736b9-fee6-4d56-98d3-0da1914c9936/ascreenshot.jpeg?tl\_px=273,193\&br\_px=1019,613\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=269,219)

22. Observe the actual and predicted values side-by-side.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-08/a4742bc6-819b-4356-ac57-f2d53a386558/ascreenshot.jpeg?tl\_px=273,154\&br\_px=1019,574\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=320,139)

23. Right click on the "Evaluate Model" component and click on  "Evaluation results" in "Preview data" option.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-08/667b3b3a-fd68-496f-be6c-901ecc7ebd5f/ascreenshot.jpeg?tl\_px=273,183\&br\_px=1019,603\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=336,139)

24. Observe the error metrics.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-08/50e31ed1-0183-42ce-bb26-cf568b3887d6/ascreenshot.jpeg?tl\_px=273,193\&br\_px=1019,613\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=512,139)
