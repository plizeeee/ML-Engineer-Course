*NOTE:* This file is a template that you can use to create the README for your project. The *TODO* comments below will highlight the information you should be sure to include.


# ML Ops with Azure project

*TODO:* This project demonstrates how I performed ML Ops on a test dataset using Azure.
 The project demonstrates my knowledge of how I deployed a model, enabled logging to track its performance, documented the model, consumed the model endpoint in python and automated the pipeline


## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/Architectural_Diagram.png)
![alt text](https://github.com/plizeeee/ML-Engineer-Course/tree/master/Module_2_ML_Ops/sample_screenshots/benchmark_endpoint_1.PNG)
The architecture diagram above shows the flow of operations for this project. 
- First we register a dataset about a marketing campaign on if clients will subscribe to term deposits.
- Second we create a compute cluster to be able to models using automl
- Third we train models to predict whether or not clients will subscribe to term deposits using automl
- forth we deploy the best performing model from automl using Azure ML Studio
- Fifth we enable application insights so that we can log the model in case there are performance issues
- Sixth we document the model API endpoint using swagger documentation so we know the format that we need to serve data to the endpoint
- Seventh we test the API endpoint using some test data and see what we get as outputs
- Eigth we benchmark the dataset to see the response time/failure rate 
- Finally we create a pipeline to be able to do the above steps and train the automl model, retrieve the best
one and call the entire pipeline using an API endpoint.

## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screenshots required to demonstrate key steps. 
- Register a dataset about a marketing campaign on if clients will subscribe to term deposits:
To register the dataset I simply downloaded this dataset and added it to the registered datasets in Azure
ML Studio. The registered dataset can be seen in the screenshot below
![alt text](https://github.com/plizeeee/ML-Engineer-Course/tree/master/Module_2_ML_Ops/sample_screenshots/Registered_dataset.PNG)
- Second we create a compute cluster to be able to models using automl
- Third we train models to predict whether or not clients will subscribe to term deposits using automl
- forth we deploy the best performing model from automl using Azure ML Studio
- Fifth we enable application insights so that we can log the model in case there are performance issues
- Sixth we document the model API endpoint using swagger documentation so we know the format that we need to serve data to the endpoint
- Seventh we test the API endpoint using some test data and see what we get as outputs
- Eigth we benchmark the dataset to see the response time/failure rate 
- Finally we create a pipeline to be able to do the above steps and train the automl model, retrieve the best
one and call the entire pipeline using an API endpoint.


## Screen Recording
https://www.youtube.com/watch?v=nF-ZcDXk7iA&ab_channel=PatrickSavoie

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
