# My Data Cleaning Process #


The <b>run_analysis.R</b> script performs the data cleaning as described in project's definiton.

#### 1. Download the dataset :-
* The dataset is downloaded and extracted in a folder called <b>UCI HAR Dataset</b>.


#### 2. Assign each data to variables :-
* <b>features</b> <- <i>features.txt</i> : 561 rows, 2 columns. The features selected for this database come from the accelerator and gyroscope 3-axial raw   signals tAcc-XYZ and tGyro-XYZ.

* <b>activities</b> <- <i>activity_labels.txt</i> : 6rows, 2 columns. List of activities performed when the corresponding measurements were taken and its codes.

* <b>subj_test</b> <- <i>test/subject_test.txt</i> : 2947 rows, 1 column. It contains test data of 9/30 volunteer test subjects being observed.

* <b>x_test</b> <- <i>test/X_test.txt</i> : 2947 rows, 561 columns. It contains recorded features test data.

* <b>y_test</b> <- <i>test/y_test.txt</i> : 2947 rows, 1 column. It contains test data of activities$code labels.

* <b>subj_train</b> <- <i>test/subject_train.txt</i> : 7352 rows, 1 column. It contains data of 21/30 volunteers subjects being observed.

* <b>x_train</b> <- <i>test/X_train.txt</i> : 7352 rows, 561 columns. It contains recorded features of train data.

* <b>y_train</b> <- <i>test/y_train.txt</i> : 7352 rows, 1 column. it contains data of activities$code labels.


#### 3. Merges the training and the test datasets to create new data set :-
* <b>x_merged</b> (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function.

* <b>y_merged</b> (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function.

* <b>subject</b> (10299 rows, 1 column) is created by merging subj_train and subj_test using rbind() function.

* <b>merged_data</b> (10299 rows, 563 columns) is created by merging subject, x_merged, y_merged using cbind() function.


#### 4. Extracts only the measurements on the mean and standatd deviation for each measurement :-
* <b>tidy_data</b> (10299 rows, 88 columns) is created by subsetting merged_data, selecting onlu columns : subject, code and the measurements mean and standard deviation (std) for each measurement.


#### 5. Uses descriptive activity names to name the activities in the data set :-
* Entire numbers in code column of the tidy_data replaced with corresponding activity taken from second column of the activity variable.


#### 6. Appropriately labels the data set with descriptive variable names :-
* code column in tidy_data renamed into <b>activity</b>.

* All Acc in column's name replaced by <b>Accelerometor</b>.

* All Gyro in column's name replaced by <b>Gyroscope</b>.

* All BodyBody in column's name replaced by <b>Body</b>.

* All Mag in column's name replaced by <b>Magnitude</b>.

* All column names that starts with <i>f</i> are replaced by <b>Frequency</b>.

* All column names that starts with <i>t<i> are replaced by <b>Time</b>.


#### 7. Creating a second independent tidy data set with average of each variable for each activity and each subject :-
* <b>final_data</b> (180 rows, 88 columns) is created by summarizing tidy_data and taking the means of each variable for each activity and each subject, and then grouping by subject na dactivity.

* Exporting final_data into <b>FinalData.txt</b> file.


