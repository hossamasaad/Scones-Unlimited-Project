# Scones-Unlimited-Project
Stores code and results for the "Build ML Workflow For Scones Unlimited" project in the Udacity AWS MLE Nanodegree

## Deploy ML Workflow with AWS
The project aims to deploy a functioning ML workflow for image classification using AWS.
Specifically, the project involved:
* Building an image classification model that can tell bicycles apart from motorcycles.
* Deploying the trained model to an endpoint.
* Using AWS Lambda Functions to build services to serialize the data, perform inference, and filter out weak inferences.
* Using AWS Step Functions to create an ML workflow to stich the above services together into an event-driven application.

## Dataset
The CIFAR dataaset is open source and generously hosted by the University of Toronto at: https://www.cs.toronto.edu/~kriz/cifar-100-python.tar.gz

## ML-Workflow Sample

Main three lambda functions:

* The Serialize Target Image Data takes the address of an image hosted in S3, then serializes and returns a JSON object.
* The image classification takes the JSON object returned from 1 and passes it to an end point and collectd the result as a JSON Object.
* The Filtering Low-Confidence Inferences takes the inference data from 2 and filters only the images that meet the defined threshold.

## Results
1. The image classification model had a test accuracy of 0.82.
2. The Final Step Function: <br>
![image](https://user-images.githubusercontent.com/40635600/193429285-0a3ce3f4-0812-4c43-a59c-889a1667dab9.png)
3. The Step Function indicates success when the prediction probability exceeds the acceptance threshold:
![image](https://user-images.githubusercontent.com/40635600/193429163-63458e67-34bf-4eaa-ad25-c86864969478.png)
4. Otherwise a Red completion status :
![image](https://user-images.githubusercontent.com/40635600/193429145-11cfdeab-f58c-4656-b711-1d485da5697b.png)

