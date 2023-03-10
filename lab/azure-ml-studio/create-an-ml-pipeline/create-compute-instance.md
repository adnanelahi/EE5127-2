---
description: >-
  This page describes the steps required to create a compute instance for
  training and evaluating machine learning algorithms in Azure Machine Learning
  Studio.
---

# Create Compute Instance

A compute instance will provide the necessary computing resources for machine learning training and testing. While there is also an option to create a compute cluster, a low-end compute instance will be created in this tutorial.

1. Click "Settings" in top right of the "Designer"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/ec542dfb-6da3-4c17-b1fb-7baf24736bc7/File.jpeg?tl\_px=273,0\&br\_px=1019,420\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=502,90)

2. Select the compute type. There are several options available but select "Compute instance" for this experiment.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/f8f5074f-4edc-43dc-ba91-abf09f098618/File.jpeg?tl\_px=273,111\&br\_px=1019,531\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=499,139)

3. Click "Compute instance"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/cd23cb28-fcab-43a2-bcce-c240721da58f/File.jpeg?tl\_px=125,148\&br\_px=871,568\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,139)

4. Click "Create Azure ML compute instance"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/b507b775-a0ba-4d9a-a2b1-917b27b4777e/File.jpeg?tl\_px=189,117\&br\_px=935,537\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,139)

5. &#x20;Enter Compute name as "mlcomputeinstance"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/47d8655a-f9c8-48d9-82cb-b64c8d6443e6/File.jpeg?tl\_px=0,141\&br\_px=746,561\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=102,139)

6. Choose "Select from all options" to see more compute options.&#x20;

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/8a5ca13e-764f-442a-aea4-284ab1ef3741/File.jpeg?tl\_px=241,39\&br\_px=987,459\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,139)

7. Click on "Cost" to order all compute options by cost.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/348dd793-5eb2-446e-a286-923fed9d849f/File.jpeg?tl\_px=241,39\&br\_px=987,459\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,139)

8. Select a suitable compute instance.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/4902a89c-d38e-4109-9e06-0517625009f3/File.jpeg?tl\_px=0,193\&br\_px=746,613\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=54,196)

9. Click "Create".

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/c2aa21a9-3b27-49cf-8632-a35e0e7813ce/File.jpeg?tl\_px=0,193\&br\_px=746,613\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=72,271)

10 Select the created compute instance "STANDARD\_DS1\_V2" in the pipeline once the instance is ready.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-03-09/f396521b-0daa-420e-a354-33faa340b0be/File.jpeg?tl\_px=79,129\&br\_px=825,549\&sharp=0.8\&width=560\&wat\_scale=50\&wat=1\&wat\_opacity=0.7\&wat\_gravity=northwest\&wat\_url=https://colony-labs-public.s3.us-east-2.amazonaws.com/images/watermarks/watermark\_default.png\&wat\_pad=262,139)

11. Continue with [Create an ML Pipeline](./).
