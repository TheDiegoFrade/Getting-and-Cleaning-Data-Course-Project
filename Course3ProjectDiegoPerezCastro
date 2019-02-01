#First after downloading the data set and placing it in our working directory 
#we will apply the read.table function to create tables of the train,test subject,features data for X and Y
getwd()
yTest <- read.table("./UCI HAR Dataset/test/y_test.txt")
xTest <- read.table("./UCI HAR Dataset/test/x_test.txt")
subjectTest <- read.table("./UCI HAR Dataset/test/subject_test.txt")
yTrain <- read.table("./UCI HAR Dataset/train/y_train.txt")
xTrain <- read.table("./UCI HAR Dataset/train/x_train.txt")
subjectTrain <- read.table("./UCI HAR Dataset/train/subject_train.txt")
features <- read.table("./UCI HAR Dataset/features.txt")


#We can see that they have common 561 that will be used as xTrain colnames
#The only problem is that for xTrain is columns and for features it is rows 
#we will need transpose
dim(features)
dim(xTrain)
dim(xTest)

#colnames for xTrain with the transpose 
colnames(xTrain) <- t(features[2])
colnames(xTest) <- t(features[2])

#There is an activity label and subject label
xTrain$activity <- yTrain[,1]
xTrain$subject <- subjectTrain[,1]
xTest$activity <- yTest[,1]
xTest$subject <- subjectTest[,1]

#Merge into one table
completeTable <- rbind(xTrain,xTest)

#The names of the xTest columns will be in one row between the merge so we will erase that row
duplicated(colnames(completeTable)) #Some TRUE values
completeTable <- completeTable[, !duplicated(colnames(completeTable))]
duplicated(colnames(completeTable)) # WIthout TRUE values

completeTable#Mean and standart deviation for each measurment 
#grep will match "mean()" that is included in the names of the completeTable
#fixed should be matched and value returns the integer
meanMeasurements <- grep("mean()", names(completeTable), value= FALSE, fixed = TRUE)
meanMeasurements <- completeTable[meanMeasurements]

#Standard deviation
stdMeasurements <- grep("std()", names(completeTable), value = FALSE)
stdMeasurements <- completeTable[stdMeasurements]

#USE DESCRIPTIVE ACTIVITY NAMES TO NAME THE ACTIVITIES IN THE DATASET
completeTable$activity <- as.character(completeTable$activity)
completeTable$activity[completeTable$activity == 1] <- "Walking"
completeTable$activity[completeTable$activity == 2] <- "Walking Upstairs"
completeTable$activity[completeTable$activity == 3] <- "Walking Downstairs"
completeTable$activity[completeTable$activity == 4] <- "Sitting"
completeTable$activity[completeTable$activity == 5] <- "Standing"
completeTable$activity[completeTable$activity == 6] <- "Laying"
completeTable$activity <- as.factor(completeTable$activity)
completeTable

#APPORPIATELY LABELS THE DATASET WITH DESCRIPTIVE VARIABLE NAMES
names(completeTable) <- gsub("Acc","Accelerator",names(completeTable))
names(completeTable) <- gsub("Mag","Magnitude",names(completeTable))
names(completeTable) <- gsub("Gyro","Gyroscope",names(completeTable))
names(completeTable) <- gsub("^t","time",names(completeTable))
names(completeTable) <- gsub("^f","frequency",names(completeTable))
completeTable <- completeTable[,c(478:479,1:477)]
names(completeTable)

#CREATE A TIDY DATASET
completeTable.dt <- data.table(completeTable) 
tidyData <- completeTable.dt[,lapply(.SD,mean), by= 'activity,subject']
write.table(tidyData, file = "Tidy.txt", row.names = FALSE)
