# FastAPI Iris Classification API

This repository contains the source code for building a FastAPI-based API for working with the Iris flower dataset.

## Installing Libraries

```bash
pip install -r requirements.txt
```

### First launching
We run our main.py

![Project Logo](img/image1.png)

It's normal because we have put nothing in the root  endpoint.

We will redirect the root endpoint of your API to the automatic swagger documentation by adding this line in our script

```python
responses.RedirectResponse(url='/docs')
```
And now we're redirected to the swagger

![Project Logo](img/image2.png)

### First call to the API

Now we will make the first call to our API.
We wlll request on the hello route using the swagger directly

Our request will take "Frank" as parameter

![Project Logo](img/image3.png)

Et voilà le travail !! 😄

## Our dataset
The Iris dataset is a famous dataset in the field of machine learning and statistics. It is often used as a beginner's dataset for practicing classification algorithms.

### Downloading 
We create a a route in api/routes/data to download and save the contents of our dataset in the src/data folder

![Project Logo](img/image4.jpeg)

### Loading
We add an endpoint */load-iris* to load the iris dataset file as a dataframe and return it as a json.

![Project Logo](img/image5.png)

### Processing
After download and load the dataset, here comes the step of processing 
in this step , the only thing we are going to do is

- Remove the column *species*
- Standardize the numerical features

Dataset before 

![Project Logo](img/image6.png)

Dataset after

![Project Logo](img/image7.png)

### Split dataset
Then we want split our dataset into two parts , one for training and one for test (which will represents 20% of the data)

The dataset

![Project Logo](img/image8.png)

The dataset splitted

![Project Logo](img/image9.png)

### Training
We train the training set

![Project Logo](img/image10.png)

### Prediction
Now it's time for the prediction

![Project Logo](img/image11.png)

## Firestore
Here come the interisting part :!!!


### Creation of  the Firestore collection
Let's create our firestore dabase on GCP 

![Project Logo](img/image12.png)

Then we create our collection called *parameters* , inside we create a document with the same name with two fields
- n_estimators
- criterion

![Project Logo](img/image13.png)


### Retrieve parameters from Firestore

We can get this parameters through the */get-parameters*

![Project Logo](img/image14.png)

### Update and add Firestore parameters

#### Update

![Project Logo](img/image15.png)

![Project Logo](img/image16.png)

We can get the paramters freshly updated 

![Project Logo](img/image17.png)


#### Add