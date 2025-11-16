# run_analysis.R
# Human Activity Recognition Using Smartphones Dataset Analysis
# This script performs the following steps:
# 1. Merges the training and the test sets to create one data set.
# 2. Extracts only the measurements on the mean and standard deviation for each measurement.
# 3. Uses descriptive activity names to name the activities in the data set.
# 4. Appropriately labels the data set with descriptive variable names.
# 5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

# Load required packages
if (!require(dplyr)) install.packages("dplyr")
if (!require(tidyr)) install.packages("tidyr")
library(dplyr)
library(tidyr)

# Set working directory (adjust path as needed)
# setwd("your/project/directory")

# Download and extract data
if (!file.exists("UCI HAR Dataset")) {
    fileUrl <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
    download.file(fileUrl, destfile = "UCI_HAR_Dataset.zip", method = "curl")
    unzip("UCI_HAR_Dataset.zip")
}

# Step 1: Read all data files
# Read feature names and activity labels
features <- read.table("UCI HAR Dataset/features.txt", col.names = c("index", "feature_name"))
activity_labels <- read.table("UCI HAR Dataset/activity_labels.txt", col.names = c("code", "activity"))

# Read training data
x_train <- read.table("UCI HAR Dataset/train/X_train.txt")
y_train <- read.table("UCI HAR Dataset/train/y_train.txt", col.names = "activity")
subject_train <- read.table("UCI HAR Dataset/train/subject_train.txt", col.names = "subject")

# Read test data
x_test <- read.table("UCI HAR Dataset/test/X_test.txt")
y_test <- read.table("UCI HAR Dataset/test/y_test.txt", col.names = "activity")
subject_test <- read.table("UCI HAR Dataset/test/subject_test.txt", col.names = "subject")

# Step 2: Merge training and test sets
# Combine subject, activity, and features for each set
train_data <- cbind(subject_train, y_train, x_train)
test_data <- cbind(subject_test, y_test, x_test)

# Merge vertically
merged_data <- rbind(train_data, test_data)

# Step 3: Extract only mean and standard deviation measurements
# Create complete variable names vector
variable_names <- c("subject", "activity", as.character(features$feature_name))

# Identify columns containing mean() or std()
mean_std_columns <- grep("subject|activity|mean\\(\\)|std\\(\\)", variable_names)

# Extract only required columns
extracted_data <- merged_data[, mean_std_columns]

# Step 4: Use descriptive activity names
extracted_data$activity <- factor(extracted_data$activity, 
                                  levels = activity_labels$code, 
                                  labels = tolower(activity_labels$activity))

# Step 5: Label with descriptive variable names
# Get current names
current_names <- names(extracted_data)

# Apply descriptive naming
new_names <- current_names
new_names <- gsub("^t", "time", new_names)
new_names <- gsub("^f", "frequency", new_names)
new_names <- gsub("Acc", "Accelerometer", new_names)
new_names <- gsub("Gyro", "Gyroscope", new_names)
new_names <- gsub("Mag", "Magnitude", new_names)
new_names <- gsub("BodyBody", "Body", new_names)
new_names <- gsub("-mean\\(\\)", "Mean", new_names)
new_names <- gsub("-std\\(\\)", "Std", new_names)
new_names <- gsub("-", "", new_names)

# Apply new names
names(extracted_data) <- new_names

# Step 6: Create independent tidy data set with averages
tidy_data <- extracted_data %>%
    group_by(subject, activity) %>%
    summarise(across(everything(), list(mean = mean), .names = "{.col}"), 
              .groups = "drop")

# Save the tidy data set
write.table(tidy_data, "tidy_data.txt", row.names = FALSE)

# Output summary
cat("Analysis completed successfully!\n")
cat("Original merged data dimensions:", dim(merged_data), "\n")
cat("Extracted data dimensions:", dim(extracted_data), "\n")
cat("Final tidy data dimensions:", dim(tidy_data), "\n")
cat("File saved: tidy_data.txt\n")

# Display sample of final data
cat("\nSample of final tidy data:\n")
print(head(tidy_data, 3))
