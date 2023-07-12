# IBM Applied Data Science Capstone Project


## Executive summary
In this capstone project, we will use machine learning classification methods to
predict whether the SpaceX Falcon 9 first stage will successfully land.
• The main steps in this project include:
• Data collection, wrangling, and formatting
• Exploratory data analysis
• Interactive data visualization
• Machine learning prediction

Our graphs illustrate that several aspects of rocket launches are related to the success or failure of the launches.It is also found that the decision tree is the best machine learning technique for predicting whether the Falcon 9 first stage will successfully land.

## Introduction
In this capstone, we will predict if the Falcon 9 first stage will successfully land. SpaceX advertises Falcon 9 rocket launches on its website for 62 million dollars; other companies charge up to 165 million dollars apiece; much of the savings is due to SpaceX's ability to reuse the first stage. As a result, if we can predict whether the first stage will land, we can estimate the cost of a launch. This data can be used if another company wishes to compete with SpaceX for a rocket launch.

The majority of failed landings are planned. SpaceX will occasionally perform a controlled landing in the water.

The fundamental issue we are attempting to answer is whether, for a given set of Falcon 9 rocket launch features such as payload mass, orbit type, launch site, and so on, the first stage of the rocket will successfully land.

## Methodology
The overall methodology includes:
1. Data collection, wrangling, and formatting, using:
  - SpaceX API
  - Web scraping
2. Exploratory data analysis (EDA), using:
  - Pandas and NumPy 
  - SQL
3. Data visualization, using:
  - Matplotlib and Seaborn
  - Folium
  - Dash
4. Machine learning prediction, using
  - Logistic regression
  - Support vector machine (SVM)
  - Decision tree
  - K-nearest neighbors (KNN)


## Data collection using SpaceX API
<a href="https://github.com/gebeyaw/IBM-Applied-Data-Science-Capstone-Project/blob/main/1_Data%20Collection%20API.ipynb" target="_blank">1_Data Collection API.ipynb</a>

Libraries or modules used: requests, pandas, numpy, datetime

- The API used is <a href="https://api.spacexdata.com/v4/rockets/" target="_blank">here</a>.
- The API provides data about many types of rocket launches done by SpaceX, the data is therefore filtered to include only Falcon 9 launches.
- The API is accessed using requests.get().
- The json result is converted to a dataframe using the json_normalize() function from pandas.
- Every missing value in the data is replaced the mean the column that the missing value belongs to. 
- We end up with 90 rows or instances and 17 columns or features. 

## Data Collection with Web Scraping
<a href="https://github.com/gebeyaw/IBM-Applied-Data-Science-Capstone-Project/blob/main/2_Data%20Collection%20with%20Web%20Scraping.ipynb" target="_blank">2_Data Collection with Web Scraping.ipynb</a>

Libraries or modules used: sys, requests, BeautifulSoup from bs4, re, unicodedata, pandas

- The data is scraped from  <a href="https://en.wikipedia.org/w/index.php?title=List_of_Falcon_9_and_Falcon_Heavy_launches&oldid=1027686922" target="_blank">List of Falcon 9 and Falcon Heavy launches</a>.
- The website contains only the data about Falcon 9 launches.
- First, the Falcon9 Launch Wiki page is requested from the url and a BeautifulSoup object is created from response of requests.get().
- Next, all column/variable names are extracted from the HTML table header by using the find_all() function from BeautifulSoup.
- A dataframe is then created with the extracted column names and entries filled with launch records extracted from table rows.
- We end up with 121 rows or instances and 11 columns or features. 

## EDA with Pandas and Numpy
<a href="https://github.com/gebeyaw/IBM-Applied-Data-Science-Capstone-Project/blob/main/3_EDA.ipynb">3_EDA.ipynb</a>

Libraries or modules used: pandas, numpy

Functions from the Pandas and NumPy libraries such as value_counts() are used to derive basic information about the data collected, which includes:
- The number of launches on each launch site
- The number of occurrence of each orbit
- The number and occurrence of each mission outcome

## EDA with SQL
<a href="https://github.com/gebeyaw/IBM-Applied-Data-Science-Capstone-Project/blob/main/4_EDA%20with%20SQL.ipynb" target="_blank">4_EDA with SQL.ipynb</a>

Framework used: IBM DB2

Libraries or modules used: ibm_db

The data is queried using SQL to answer several questions about the data such as:
- The names of the unique launch sites in the space mission
- The total payload mass carried by boosters launched by NASA (CRS)
- The average payload mass carried by booster version F9 v1.1

The SQL statements or functions used include SELECT, DISTINCT, AS, FROM, WHERE, LIMIT, LIKE, SUM(), AVG(), MIN(), BETWEEN, COUNT(), and YEAR().

## Data Visualization using Matplotlib and Seaborn
<a href="https://github.com/gebeyaw/IBM-Applied-Data-Science-Capstone-Project/blob/main/5_EDA%20Visualization.ipynb" target="_blank">5_EDA Visualization.ipynb</a>

Libraries or modules used: pandas, numpy, matplotlib.pyplot, seaborn

Functions from the Matplotlib and Seaborn libraries are used to visualize the data through scatterplots, bar charts, and line charts. The plots and charts are used to understand more about the relationships between several features, such as:
- The relationship between flight number and launch site
- The relationship between payload mass and launch site
- The relationship between success rate and orbit type

Examples of functions from seaborn that are used here are scatterplot(), barplot(), catplot(), and lineplot().

<br>
Example: A scatterplot showing the relationship between flight number and launch site
<p align="center">
<img width="604" alt="Picture 1" src="https://user-images.githubusercontent.com/46462603/152728660-a3b5dc76-2e52-4c66-b058-3e37361b7055.png">
</p>
<br>

## Data Visualization using Folium
<a href="https://github.com/gebeyaw/IBM-Applied-Data-Science-Capstone-Project/blob/main/6_Interactive%20Visual%20Analytics%20with%20Folium%20lab.ipynb" target="_blank">6_Interactive Visual Analytics with Folium lab.ipynb</a>

Libraries or modules used: folium, wget, pandas, math

Functions from the Folium libraries are used to visualize the data through interactive maps. The Folium library is used to:
- Mark all launch sites on a map
- Mark the succeeded launches and failed launches for each site on the map
- Mark the distances between a launch site to its proximities such as the nearest city, railway, or highway

These are done using functions from folium such as add_child() and folium plugins which include MarkerCluster, MousePosition, and DivIcon.

<br>
Example: A folium map showing the succeeded launches and failed launches for a specific launch site. If we zoom in on one of the launch site, we can see green and red tags. Each green tag represents a successful launch while each red tag represents a failed launch.
<p align="center">
<img width="670" alt="Picture 2" src="https://user-images.githubusercontent.com/46462603/152728830-e7a4d921-706e-4040-af27-b4b27361f8c1.png">
</p>
<br>

## Data Visualization using Dash
<a href="https://github.com/gebeyaw/IBM-Applied-Data-Science-Capstone-Project/blob/main/7_spacex_dash_app.py" target="_blank">7_spacex_dash_app.py</a>

Libraries or modules used: pandas, dash, dash_html_components, dash_core_components, Input and Output from dash.dependencies, plotly.express

Functions from Dash are used to generate an interactive site where we can toggle the input using a dropdown menu and a range slider.
Using a pie chart and a scatterplot, the interactive site shows:
- The total success launches from each launch site
- The correlation between payload mass and mission outcome (success or failure) for each launch site

The application is launched on a terminal on the IBM Skills Network website.

<br>
The picture below shows a pie chart when launch site CCAFS LC-40 is chosen in the dropdown menu on the website. 0 represents failed launches while 1 represents successful launches. We can see that 73.1% of launches done at CCAFS LC-40 are failed launches.
<p align="center">
<img width="692" alt="Picture 3" src="https://user-images.githubusercontent.com/46462603/152729002-f731499b-aab8-46a1-b1c3-583c24ae909e.png">
</p>
<br>
<br>
The picture below shows a scatterplot when the payload mass range is set to be from 2000kg to 8000kg. Class 0 represents failed launches while class 1 represents successful launches. 
<p align="center">
<img width="748" alt="Picture 4" src="https://user-images.githubusercontent.com/46462603/152729009-c2cdaba4-674c-4103-b540-e77ad3544a99.png">
</p>
<br>

## Machine Learning Prediction
<a href="https://github.com/gebeyaw/IBM-Applied-Data-Science-Capstone-Project/blob/main/8_Machine%20Learning%20Prediction.ipynb" target="_blank">8_Machine Learning Prediction.ipynb</a>

Libraries or modules used: pandas, numpy, matplotlib.pyplot, seaborn, sklearn

Functions from the Scikit-learn library are used to create our machine learning models. The machine learning prediction phase include the following steps:
1. Standardizing the data using the preprocessing.StandardScaler() function from sklearn
2. Splitting the data into training and test data using the train_test_split function from sklearn.model_selection
3. Creating machine learning models, which include:
  - Logistic regression using LogisticRegression from sklearn.linear_model
  - Support vector machine (SVM) using SVC from sklearn.svm
  - Decision tree using DecisionTreeClassifier from sklearn.tree
  - K nearest neighbors (KNN) using KNeighborsClassifier from sklearn.neighbors
4. Fit the models on the training set 
5. Find the best combination of hyperparameters for each model using GridSearchCV from sklearn.model_selection
6. Evaluate the models based on their accuracy scores and confusion matrix using the score() function and confusion_matrix from sklearn.metrics

When we compare the results of all four models, we can observe that they all have the same accuracy score and confusion matrix when tested on the test set. As a result, their best GridSearchCV ratings are utilized to rank them instead. The models are rated in the following order based on their GridSearchCV best scores,with the first being the best and the last being the worst:
- Decision tree (GridSearchCV best score: 0.8892857142857142) 
- K nearest neighbors, KNN (GridSearchCV best score: 0.8482142857142858)
- Support vector machine, SVM (GridSearchCV best score: 0.8482142857142856)
- Logistic regression (GridSearchCV best score: 0.8464285714285713)

<br>
The picture below shows the confusion matrix when the Decision Tree model is tested on the test data.
<p align="center">
<img width="368" alt="Picture 5" src="https://user-images.githubusercontent.com/46462603/152729182-f031ab89-9805-4701-a112-3baad406e127.png">
</p>
<br>

## Discussion
We can see from the data visualization section that some features may have an  association with the mission outcome in a variety of ways. For example, with heavy payloads, the successful or positive landing rate is higher in orbit types such as Polar, LEO, and ISS. However, for GTO, we can't tell the difference because both positive and negative landing rates (missed missions) are present.

As a result, each characteristic may have an effect on the final mission outcome. It is difficult to determine how each of these features affects the mission outcome. However, we can apply machine learning algorithms to learn the pattern of previous data and predict whether or not a mission would be successful based on the supplied features.

## Conclusion
In this capstone, we try to predict whether or not the first stage of a specific Falcon 9 launch will land in order to calculate the cost of the launch. Each feature of a Falcon 9 launch, such as payload mass or orbit type, may have an impact on the mission's result. 

Several machine learning techniques are employed to study the patterns in 
previous Falcon 9 launch data in order to create prediction models that can be used to predict the outcome of a Falcon 9 launch.

Among the four machine learning algorithms used, the predictive model built by the decision tree method performed the best


