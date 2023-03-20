*NOTE:* This file is a template that you can use to create the README for your project. The *TODO* comments below will highlight the information you should be sure to include.


# ML Ops with Azure project

*TODO:* This project demonstrates how I performed ML Ops on a test dataset using Azure.
 The project demonstrates my knowledge of how I deployed a model, enabled logging to track its performance, documented the model, consumed the model endpoint in python and automated the pipeline


## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/Architectural_Diagram.png)

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
- **Register a dataset about a marketing campaign on if clients will subscribe to term deposits:**
To register the dataset I simply downloaded this dataset and added it to the registered datasets in the Azure
ML Studio GUI. The registered dataset can be seen in the screenshot below
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/Registered_dataset.PNG)
- **Create a compute cluster to be able to models using automl:
To create a compute cluster I simply created one in the Azure ML Studio UI with the following configuration: 
I selected "Standard DS12_V2" for the VM size and set the minimum number of nodes to 1. No screenshot was required here, so I jumped to the following step after
- **Train models with automl:**
Next I trained the models using autoML using the Azure ML Studio UI. The model was trained as a classification task, with a timout time of 20 minutes. The successfully trained model can be found below
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/trained_auto_ml_model.PNG)
A screenshot of the best performing model is shown below, which is a voting ensemble:
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/best_model_1.PNG)
- **Deploy the best performing model from automl using Azure ML Studio**
next the best model (the voting ensemble) was deployed using the Azure ML Studio UI, and was deployed using Azure Container Instance and with Authentication enabled (so I will need a key to authenticate to use the model)
- **Enable application insights:**
Next I enabled app insights to so that we can log the model in case there are performance issues. Below is
a screeshot of the API endpoint showing the app insights was enabed:
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/application_insights_running.PNG)

I also ran Python code to show output logs of App insights using "logs.py". The output in the command prompt is seen in the 2 images below:
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/application_insights_output.PNG)
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/application_insights_running_2.PNG)
- **Document the model API using swagger:**
Next I documented the model API endpoint using swagger documentation so we know the format that we need to serve data to the endpoint. This was done
by downloading a configuration file from azure (config.json), and changing the ports to the correct ones to work with the VM (I used port 9000 instead of 8080).
Once the setup was complete I ran swagger.sh in Git Bash and servy.py in the command line and used the local host to see the output. Below is the documentation of the
endpoint generated by swagger. Note that it clearly highlights the inputs required by the model, which can be used if other people want to use the model.

First I show that I'm using the correct local host in the search bar and the authorized scheme (only https is available)
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/swagger_documentation_1.PNG)

Next I show a get method to show if the API is working as expected (should return Healthy if it's working properly) 
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/swagger_documentation_health_metric.PNG)

Next I show the post method, which is how we can format the request with input data to get an output from the model(for instance the columns we need to provide include "age", "job", "education", ect
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/swagger_documentation_post_method.PNG)

Next I show a screenshot that summarizes the inputs and outputs of the endpoint
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/swagger_documentation_other_documentation.PNG)

- **Test API endpoint using some test data and see what we get as outputs:** Next I tested the model endpoint by sending data to the API. I did this through sending 2 test datapoints to the model
using "endpoint.py". I needed to add a scoring_URI and key to the python script, and changed the input requirements to include an extra dictionnary key called "inputs" which was a required parameter from the model from the swagger documentation (otherwise the API would return an error).
The output from serve.py from the two requests is as follows:
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/endpoint_results.PNG)

From the above screenshot we see that the 2 examples we sent to the API the response we got was ['No','No'] meaning the model predicted based on the datapoints we provided that these hypothetical clients
are predicted not to subscribe to a term deposit. It is clear our endpoint is working! :)

- **Benchmark the dataset to see the response time/failure rate:**
Next, I benchmarked the dataset to see key statistics of the model performance after being deployed. To do this I ran benchmark.sh in git bash and added my key and URI to the command for it to work.
I got the following output from the 10 runs:
![alt text](https://github.com/plizeeee/ML-Engineer-Course/blob/master/Module_2_ML_Ops/sample_screenshots/benchmark_endpoint_2.PNG)
Note this shows that the average response time of the model is 122ms, which is very good (well-within Azure's timeout time of 60 seconds). Note that 
I forgot to include a screenshot of the failure rate (none of the 10 runs failed), but since this component of the project was optional it should be okay.


- **Create pipeline to be able to do the above steps and train the automl model, retrieve the best**
one and call the entire pipeline using an API endpoint.


## Screen Recording
https://www.youtube.com/watch?v=nF-ZcDXk7iA&ab_channel=PatrickSavoie

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
