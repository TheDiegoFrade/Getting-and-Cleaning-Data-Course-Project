# Getting-and-Cleaning-Data-Course-Project

1.First after downloading the data set we will apply the read.table function to read the data
2. we place it in our working directory

3.We can see that they have common 561 that will be used as xTrain colnames
The only problem is that for xTrain is columns and for features it is rows 
4. we will need transpose
5. Colnames for xTrain with the transpose 
6. There is an activity label and subject label
7. Merge into one table with rbind() function
8. The names of the xTest columns will be in one row between the merge so we will erase that row
9. Obtain the Standard deviation and Mean with grep() function 
10. grep() will match "mean()" that is included in the names of the completeTable
11. Use of descriptive activity names for the columns in the data set
12. We clean the Data Set labels to be tidy, using the function gsub()

13. Finally we create the tidy data set


