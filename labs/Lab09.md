## Lab 9 : Working with Models

Data scientists often develop models using a variety of Python/R open source packages. The challenge lies in actually exposing those models to stakeholders who can test the model.  The data science team also needs a reliable way to retain history of the models they build and ensure that they can rebuild a specific version if needed

 This lab will give you practice packaging a trained model into an immutable artifact and deploying models as REST APIs.

 

1. Open Workbench and start a **Python 3** session using the 2 vCPU/ 4 GiB RAM engine.

2. Open the file **7_fit.py** and run it. You will see the code created a model called “petalWidthModel.pkl”:

3. Before we deploy thismodel, let’s test it in the workbench. Open file **8_predict.py** and run it. Then, to confirm that the predict() function works as expected, run this line of code by copying and pasting into
   the workbench prompt, see below screenshot: `predict({"petal_length": 19})`

   You should see the output like this:

Now let’s deploy the add function to a REST endpoint.

1. Stop your Python 3 Session used in step 3 above.
2. Go to the project overview page and select **Models->New Model** from the left hand bar.
3. Enter a name, description, select the python file **8_predict.py**, the **predict** function, and Example Input as per below screenshot: 

1. Click on the model you just added and go to its **Build and Monitoring** pages to watch the build process until it completes.
2. Once the model has been built and **deployed**, go back to the model **Overview** page and use the **Test Model** widget to make sure the model works as expected.

You can test using Shell, Python, and R to see the various ways the model can be accessed using a rest a REST interface: 

Each model in Cloudera Data Science Workbench has a unique access key associated with it. This access key serves two purposes: 1) it is a unique identifier for the model, and 2) it serves as an authentication token that allows you to make calls to the model.

1. Note the access key used in the test examples. You would need this access key to use the Model from a REST API. Click on the Setting tab in your Model to see your key and the option for Regenerating a new Model Access Key.
2. Now try on  your own to see if you can figure out how to use the model from your environment.

Stop your Model deployment when finished with this lab.

### End of Lab 9

------

[Back to Main](https://github.com/rajatrakesh/cdswlabs)