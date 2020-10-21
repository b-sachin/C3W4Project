The run_analysis.R script performs the data preparation and then followed by the 5 steps required as described in the course project’s definition.
<h3> 1.	Download the dataset</h3>
<ul>
  <li>Dataset downloaded and extracted in the folder called UCI HAR Dataset</li>
</ul>

<h3> 2.	Assign each data to variables</h3>
<ul>
  <li>train_subject <- UCI HAR Dataset/train/subject_train.txt : 7352 rows, 1 column
contains train data of 21/30 volunteer subjects being observed</li>
  <li>train <- UCI HAR Dataset/train/X_train.txt : 7352 rows, 561 columns
contains recorded features train data</li>
  <li>train_activity <- UCI HAR Dataset/train/Y_train.txt : 7352 rows, 1 columns
contains train data of activities’code labels</li>
  <li>test_subject <- UCI HAR Dataset/test/subject_test.txt : 2947 rows, 1 column
contains test data of 9/30 volunteer test subjects being observed</li>
  <li>test <- UCI HAR Dataset/test/X_test.txt : 2947 rows, 561 columns
contains recorded features test data</li>
  <li>test_activity <- UCI HAR Dataset/test/Y_test.txt : 2947 rows, 1 columns
contains test data of activities’code labels</li>
  <li>features_raw <- UCI HAR Dataset/features.txt : 561 rows, 2 columns
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.</li>
  <li>activity_labels <- UCI HAR Dataset/activity_labels.txt : 6 rows, 2 columns
List of activities performed when the corresponding measurements were taken and its codes (labels)</li>
</ul>

<h3> 3.	Merges the training and the test sets to create one data set</h3>
<ul>
  <li>train (7352 rows, 563 column) is created by merging train_subject, train_activity and train using cbind() function</li>
  <li>test (2947 rows, 563 column) is created by merging</li>
  <li>test_subject, test_activity and test using cbind() function</li>
  <li>all_data (10299 rows, 561 columns) is created by merging train and test using rbind() function</li>
</ul>

<h3> 4.	Extracts only the measurements on the mean and standard deviation for each measurement</h3>
<ul>
  <li>req_data (10299 rows, 81 columns) is created by first, applying grep() on feature_raw, to collect measurements on the mean and standard deviation (std) for each measurement and then applying it to all_data to extract req_data.</li>
  <li>Added column names to all columns of the req_data as “subject”,”activity” and feature name respectively.</li>
</ul>


<h3> 5.	Uses descriptive activity names to name the activities in the data set</h3>
<ul>
  <li>Entire numbers in activity column of the req_data replaced with corresponding activity taken from second column of the activity_labels variable.</li>
</ul>

<h3> 6.	Appropriately labels the data set with descriptive variable names</h3>
<ul>
  <li>activity column in req_data renamed into activity_labels</li>
  <li>All Acc in column’s name replaced by Accelerometer</li>
  <li>All Gyro in column’s name replaced by Gyroscope</li>
  <li>All Mag in column’s name replaced by Magnitude</li>
  <li>All start with character f in column’s name replaced by FrequencyDomain</li>
  <li>All start with character t in column’s name replaced by TimeDomain</li>
</ul>

<h3> 7.	From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject</h3>
<ul>
    <li>mean_data (180 rows, 81 columns) is created by reshaping req_data. Firstly, melting req_data along with “subject and activity as id variables and the melt_data is casted to take mean for each subject and activity group.</li>
    <li>Export mean_data into tidy_data.txt file.</li>
</ul>
