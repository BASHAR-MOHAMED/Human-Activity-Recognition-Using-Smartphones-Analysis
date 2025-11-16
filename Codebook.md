# Codebook: Human Activity Recognition Using Smartphones Tidy Data

## Dataset Description
This dataset is derived from the "Human Activity Recognition Using Smartphones" dataset. It contains averaged measurements for each subject and activity.

## Study Design
The original experiments were carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities while wearing a smartphone on the waist.

## Variables

### Identifier Variables
- `subject`: Integer (1-30) identifying the volunteer
- `activity`: Factor with 6 levels describing the activity performed
  - walking
  - walking_upstairs
  - walking_downstairs
  - sitting
  - standing
  - laying

### Measurement Variables
All measurement variables are numeric and represent the average of mean and standard deviation measurements for each subject-activity combination. Units are normalized and bounded within [-1,1].

#### Variable Naming Convention:
- Prefixes:
  - `time`: Time domain signals
  - `frequency`: Frequency domain signals
- Sensors:
  - `Accelerometer`: Accelerometer measurements
  - `Gyroscope`: Gyroscope measurements
- Statistics:
  - `Mean`: Mean value
  - `Std`: Standard deviation
- Components:
  - `X`, `Y`, `Z`: 3-axial signals
  - `Magnitude`: Magnitude of signals

#### Complete Variable List:
- timeBodyAccelerometerMeanX
- timeBodyAccelerometerMeanY
- timeBodyAccelerometerMeanZ
- timeBodyAccelerometerStdX
- timeBodyAccelerometerStdY
- timeBodyAccelerometerStdZ
- timeGravityAccelerometerMeanX
- timeGravityAccelerometerMeanY
- timeGravityAccelerometerMeanZ
- timeGravityAccelerometerStdX
- timeGravityAccelerometerStdY
- timeGravityAccelerometerStdZ
- timeBodyAccelerometerJerkMeanX
- timeBodyAccelerometerJerkMeanY
- timeBodyAccelerometerJerkMeanZ
- timeBodyAccelerometerJerkStdX
- timeBodyAccelerometerJerkStdY
- timeBodyAccelerometerJerkStdZ
- timeBodyGyroscopeMeanX
- timeBodyGyroscopeMeanY
- timeBodyGyroscopeMeanZ
- timeBodyGyroscopeStdX
- timeBodyGyroscopeStdY
- timeBodyGyroscopeStdZ
- timeBodyGyroscopeJerkMeanX
- timeBodyGyroscopeJerkMeanY
- timeBodyGyroscopeJerkMeanZ
- timeBodyGyroscopeJerkStdX
- timeBodyGyroscopeJerkStdY
- timeBodyGyroscopeJerkStdZ
- timeBodyAccelerometerMagnitudeMean
- timeBodyAccelerometerMagnitudeStd
- timeGravityAccelerometerMagnitudeMean
- timeGravityAccelerometerMagnitudeStd
- timeBodyAccelerometerJerkMagnitudeMean
- timeBodyAccelerometerJerkMagnitudeStd
- timeBodyGyroscopeMagnitudeMean
- timeBodyGyroscopeMagnitudeStd
- timeBodyGyroscopeJerkMagnitudeMean
- timeBodyGyroscopeJerkMagnitudeStd
- frequencyBodyAccelerometerMeanX
- frequencyBodyAccelerometerMeanY
- frequencyBodyAccelerometerMeanZ
- frequencyBodyAccelerometerStdX
- frequencyBodyAccelerometerStdY
- frequencyBodyAccelerometerStdZ
- frequencyBodyAccelerometerJerkMeanX
- frequencyBodyAccelerometerJerkMeanY
- frequencyBodyAccelerometerJerkMeanZ
- frequencyBodyAccelerometerJerkStdX
- frequencyBodyAccelerometerJerkStdY
- frequencyBodyAccelerometerJerkStdZ
- frequencyBodyGyroscopeMeanX
- frequencyBodyGyroscopeMeanY
- frequencyBodyGyroscopeMeanZ
- frequencyBodyGyroscopeStdX
- frequencyBodyGyroscopeStdY
- frequencyBodyGyroscopeStdZ
- frequencyBodyAccelerometerMagnitudeMean
- frequencyBodyAccelerometerMagnitudeStd
- frequencyBodyAccelerometerJerkMagnitudeMean
- frequencyBodyAccelerometerJerkMagnitudeStd
- frequencyBodyGyroscopeMagnitudeMean
- frequencyBodyGyroscopeMagnitudeStd
- frequencyBodyGyroscopeJerkMagnitudeMean
- frequencyBodyGyroscopeJerkMagnitudeStd

## Transformations Performed

1. **Merging**: Combined training and test sets
2. **Extraction**: Selected only mean and standard deviation measurements
3. **Activity Labels**: Replaced numeric codes with descriptive names
4. **Variable Names**: Applied descriptive naming convention
5. **Averaging**: Created second dataset with averages for each subject-activity combination

## Dataset Dimensions
- Final tidy dataset: 180 observations × 68 variables
- 30 subjects × 6 activities = 180 combinations
