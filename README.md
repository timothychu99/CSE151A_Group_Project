# CSE151A_Group_Project

## Milestone 2

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
14. Activity - The class of what activity the subject is performing

What we checked:
* We checked if the categories for the activities needed to be encoded and they were already numerically encoded so no work needs to be done here
* We checked if there were any null or invalid entries within our dataset. Ultimately, we did not find any and thus do not need to remove any values in the upcoming preprocessing milestone

## Milestone 3
Preprocessing:
* We dropped the subject column.
* We took 10,000 random samples of each activity to ensure an equal number of observaions for each.
* We used min-max scaling to scale all the input data.
* There was no need to encode our data since our data was already in floats and ints. We encoded the output class `Activity` for each of our Logistic regression models.
* We used feature expansion to create a magnitude of acceleration for each hand (left and right) using the x, y, and z acceleration values, with the goal of improving correlation of Activities to the rest of the data. 

We trained our first model using logistic regression to predict an Activity based on acceleration and gyroscope data.
* For each activity model, we encoded the output as 1 for the activity and 0 for the other activities. 

* We made a classification report to measure training vs testing error for each Activity's logistic regression prediction model

The example ground truth is the Activity type of the observation. For each model i this is encoded as `not Activity i = 0` and `Activity i = 1`. We expect our test accuracy to be lower than training accuracy, since the model is trained on the training data. 

Where does your model fit in the fitting graph?  
Our model fit early in the fitting graph because as we measured iteration count on the logisitic regrssion models, we see that both the training and testing errors doesn't improve much after around iteration 30-100 which is very early in a logistic regression model. This shows our data is low complexity.

What are the next models you are thinking of and why?  
We are thinking of SVMs because we can categorically sort the Activities on a graph to show correlation between acceleration and gyroscope data to a certain Activity. We can also use one model to classify all the activities, rather than a separate model for each activity.

Link to Jupyter Notebook Fitting Graph and Logistic Regression Models:
[jupyter notebook link](https://github.com/timothychu99/CSE151A_Group_Project/blob/Milestone3/Milestone3_Logistic_Regression.ipynb)

Conclusion  
The conclusion of our 1st model is that it performs better than random and for some activities performs very well in terms of predicting the correct Activity based on acceleration and gyroscope sensory data. However, for Activity 0 it did not perform as well. For several of the activities the training accuracy is much higher than the test accuracy, which can be an indication of overfitting. We can improve this model by labeling the data better and using a very good model called Support Vector Machine. Support Vector Machine will categorize our data better than using logistic regression because it could categorize multiple activities on a singular graph. This will help us compare Activities with more accuracy.

## Milestone 4
Based on feedback from Milestone 3, we changed our first model from Logistic Regression, where we made individual classifiers, to K-Nearest Neighbors to make it easier to find an overall accuracy and allow us to compare the results to our second model, SVM. The KNN model had an overall train accuracy of 0.93 and test accuracy of 0.61 after fine-tuning k to 19. Given the large difference in accuracies, this could indicate overfitting in our model. We then moved on to the second model, SVM.

1: Train your second model. Make sure you use a different model than in MS3, and you must fine-tune your model to get an accurate comparison.
Our second model is SVM, we redone our previous model to be KNN instead of the Logistic Regression.

2: Evaluate your model and compare training vs. test error
We have done this for both SVM and KNN test and train accuracies.
In order to convert this to training and test error, we will compute the following equations:
* testing error = 1 - testing accuracy
* training error = 1 - training accuracy
for the best (Linear) SVM model measured in terms of lowest testing error:
* training accuracy = 0.7314529914529915
* testing accuracy = 0.7476923076923077
* training error = 0.2685
* testing error = 0.2523
for the best (k = 19) KNN model measured in terms of lowest testing error:
* training accuracy = 0.9257606837606838
* testing accuracy = 0.6079230769230769
* training error = 0.07423
* testing error = 0.3921

3: Answer the questions: Where does your model fit in the fitting graph? and What are the next models you are thinking of and why?
The KNN model fits in the fitting graph in regards to k being the model complexity with higher k values being higher model complexity to be close to the ideal range. This is because when testing with increasing k values, we saw that it plateaus at a testing error of around 0.39. For proof, please check the KNN_accuracy_results.txt

The SVM model fits in the fitting graph in regards to the model complexity with a higher polynomial SVM being higher model complexity to be at the ideal range. From the classification reports, with increasing polynomials, it fully plateaued at testing accuracy of 0.72 for all polynomials greater or equal to 2. This is equal to a testing error of 0.28. For the Linear SVM model, the testing accuracy was a 0.74 which is equivalent to a testing error of 0.26, which is the lowest error we see from testing the SVM models. For proof, please check SVM_accuracy_results.txt

4: Update your README.md to include your new work and updates you have all added. Make sure to upload all code and notebooks. Provide links in your README.md
DONE

5: Conclusion section: What is the conclusion of your 2nd model? What can be done to possibly improve it? Note: The conclusion section should be it's own independent section. i.e. Methods: will have models 1 and 2 methods, Conclusion: will have models 1 and 2 results and discussion. 
The conclusion for our SVM model (our 2nd model) is that it is pretty good. It predcted with a whooping 74% accuracy!!! We can't improve it that much. The error rate has plateaued out in terms of the SVM for all higher polynomial degrees at a lower accuracy. The only way we can improve the model is to find another model like K-means or RBF.

6: Provide predictions of correct and FP and FN from your test dataset.
In terms of FP and FN, we have multiple classes and our y_test data is in terms of which activity is predicted. As a result, we are unable to perform FP and FN. For the predictions of correct on our test dataset, we are able to do compute it.

Correct = accuracy * length of test_dataset

Predictions of correct for Linear SVM model:
SVM test set size = 0.1 * 13000 = 1300
Correct = 0.7476923076923077 * 1300 = 972

Predictions of correct for (k=19) KNN model:
KNN test set size = 0.1 * 130000 = 13000
Correct = 0.6079230769230769 * 13000 = 7903


