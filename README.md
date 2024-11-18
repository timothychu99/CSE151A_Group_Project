# CSE151A_Group_Project

How will you preprocess your data? You should only explain (do not perform pre-processing as that is in MS3) this in your README.md file and link your Jupyter notebook to it. All code and  Jupyter notebooks have be uploaded to your repo.

How will we preprocess our data:
* We will drop the subject column from our data as it contains nothing of value: the only information it provides is the information regarding the participant performing the physical activity
* normalize the data through min-max normalization
* random sample our data to contain 4,000 entries instead of the full > 1.2 million entries for visualizing the data since generating a pairplot was taking too long to run
* We have identified that around 800,000 to 900,000 of the samples were the participants standing still and we intend on either dropping or sampling to an appropriate size of individuals standing still

Columns:
1. Subject - The identifier for the subject performing the action in the data
2. alx - The acceleration in the X direction of the sensor while the subject is performing motions
3. aly - The acceleration in the Y direction of the sensor while the subject is performing motions
4. alz - The acceleration in the Z direction of the sensor while the subject is performing motions
5. arx - The rate of change of the accelerations in the X direction while the subject is performing motions
6. ary - The rate of change of the accelerations in the Y direction while the subject is performing motions 
7. arz - The rate of change of the accelerations in the Z direction while the subject is performing motions 
8. glx - The gyroscrope data of the X location while the subject is performing motions
9. gly - The gyroscrope data of the Y location while the subject is performing motions
10. glz - The gyroscrope data of the Z location while the subject is performing motions
11. grx - The rate of change of the gyroscope data in the X direction while the subject is performing motions
12. gry - The rate of change of the gyroscope data in the Y direction while the subject is performing motions
13. grz - The rate of change of the gyroscope data in the Z direction while the subject is performing motions
14. Activity - The class of what activityu the subject is performing

What we checked:
* We checked if the categories for the activities needed to be encoded and they were already numerically encoded so no work needs to be done here
* We checked if there were any null or invalid entries within our dataset. Ultimately, we did not find any and thus do not need to remove any values in the upcoming preprocessing milestone

-- Milestone 3 --
Preprocessing:
* We dropped the subject column.
* We used min-max scaling to scale all the data besides the Activity.

There was no need to encode our data since our data was already in floats and ints.
We used feature expansion to create a magnitude of acceleration using all the acceleration values we had to improve correlation of Activities to the rest of the data.

* We trained our first model using logistic regression to predict an Activity based on acceleration and coordinate data.

* We made a classification report to measure training vs testing error for each Activity's logistic regression prediction model

Where does your model fit in the fitting graph?
Our model fit early in the fitting graph because as we measured iteration count on the logisitic regrssion models, we see that both the training and testing errors doesn't improve much after around iteration 30-100 which is very early in a logistic regression model. This shows our data is low complexity.

What are the next models you are thinking of and why?
We are thinking of SVMs because we can categorically sort the Activities on a graph to show correlation between acceleration and coordinates to a certain Activity.

Link to Jupyter Notebook Fitting Graph and Logistic Regression Models:
[jupyter notebook link](https://github.com/timothychu99/CSE151A_Group_Project/blob/Milestone3/preprocessing.ipynb)

Conclusion
The conclusion of our 1st model is that it performs below our expectations in terms of predicting the correct Activity based on acceleration and coordinate sensory data. We can improve this model by labeling the data better by using a very good model called Support Vector Machine. Support Vector Machine will categorize our data better than using logistic regression because it could categorize multiple activities on a singular graph. This will help us compare Activities with more accuracy.


