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
