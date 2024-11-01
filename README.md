# CSE151A_Group_Project

How will you preprocess your data? You should only explain (do not perform pre-processing as that is in MS3) this in your README.md file and link your Jupyter notebook to it. All code and  Jupyter notebooks have be uploaded to your repo.

How will we preprocess our data:
* drop the subject column because it contains 
* normalize the data through min-max normalization
* random sample our data to contain 4000 entries instead of the full > 1.2 million entries

What we checked:
* if there were any null values in the dataset, which was none. As a result, we do not have to remove any null values.
* there were no outliers to be found from the describe function's min and max and also from the pairplot not showing any outliers