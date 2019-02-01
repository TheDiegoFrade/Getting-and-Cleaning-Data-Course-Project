# Getting-and-Cleaning-Data-Course-Project

First after downloading the data set we will apply the read.table function to read the data
And we place it in our working directory

We can see that they have common 561 that will be used as xTrain colnames
The only problem is that for xTrain is columns and for features it is rows 
we will need transpose
Colnames for xTrain with the transpose 
There is an activity label and subject label
Merge into one table with rbind() function
The names of the xTest columns will be in one row between the merge so we will erase that row
Obtain the Standard deviation and Mean with grep() function 
grep() will match "mean()" that is included in the names of the completeTable
Use of descriptive activity names for the columns in the data set
We clean the Data Set labels to be tidy, using the function gsub()

Finally we create the tidy data set


