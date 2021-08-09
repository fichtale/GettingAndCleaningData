CodeBook


The run_analysis.R script performs data preparation (cleaning) and is followed by the five required steps, as described in the course project’s instructions.

Download the dataset:
Dataset downloaded and extracted under the folder called UCI HAR Dataset.

Assign each data to variables:

features <- features.txt : 561 rows, 2 columns
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.

activities <- activity_labels.txt : 6 rows, 2 columns
List of activities performed when the corresponding measurements were taken and their labels.

subject_test <- test/subject_test.txt : 2947 rows, 1 column
Contains testing data of 9/30 volunteer test subjects being observed.

x_test <- test/X_test.txt : 2947 rows, 561 columns
Contains recorded features testing data.

y_test <- test/y_test.txt : 2947 rows, 1 columns
Contains testing data of activities’code labels.

subject_train <- test/subject_train.txt : 7352 rows, 1 column
Contains training data of 21/30 volunteer subjects being observed.

x_train <- test/X_train.txt : 7352 rows, 561 columns
Contains recorded features training data.

y_train <- test/y_train.txt : 7352 rows, 1 columns
Contains training data of activities’code labels.

Merges the training and the test sets to create one data set:

X (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function
Y (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function
Subject (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function
Merged_Data (10299 rows, 563 column) is created by merging Subject, Y and X using cbind() function

Extracts only the measurements on the mean and standard deviation for each measurement:

TidyData (10299 rows, 88 columns) is created by subsetting Merged_Data, and selecting ONLY the following columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

Uses descriptive activity names to name the activities in the data set:

All numbers in code column of the TidyData were replaced with the corresponding activity taken from second column of the activities variable.

Appropriately labels the data set with descriptive variable names:
Code column in TidyData was renamed to activities.
All Acc in column’s name were replaced by Accelerometer
All Gyro in column’s name were replaced by Gyroscope
All BodyBody in column’s name were replaced by Body
All Mag in column’s name were replaced by Magnitude
All f characters in column’s name were replaced with Frequency
All t characters in column’s name replaced with Time

From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject:

FinalData (180 rows, 88 columns) was created by sumarizing TidyData taking the means of each variable for each activity and each subject, after being grouped by subject and activity.
Exported FinalData into FinalData.txt file.
