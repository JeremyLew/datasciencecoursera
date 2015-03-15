
#Code Book

This code book describes:

* Information about the raw data set
* Key variables of the data set
* Data cleaning operations done to clean the data

 
## Data Set Information:

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

A video of the experiment including an example of the 6 recorded activities with one of the participants can be seen in the following link: https://www.youtube.com/watch?v=XOEN9W05_4A

**Citation**:
Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. A Public Domain Dataset for Human Activity Recognition Using Smartphones. 21th European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning, ESANN 2013. Bruges, Belgium 24-26 April 2013.

1. Smartlab - Non-Linear Complex Systems Laboratory
DITEN - Universit� degli Studi di Genova, Genoa (I-16145), Italy. 
2. CETpD - Technical Research Centre for Dependency Care and Autonomous Living
Universitat Polit�cnica de Catalunya (BarcelonaTech). Vilanova i la Geltr� (08800), Spain
activityrecognition '@' smartlab.ws

## Data Set Structure

|         Features      |         Subject             |           Activity                |
|-----------------------|-----------------------------|-----------------------------------|
|X_train.txt            |subject_train.txt            |y_train.txt                        |
|X_test.txt             |subject_test.txt             |y_test.txt                         |


## Key Variables

|       Key variables   |                           Description                       |
|-----------------------|-----------------------------------------------------------------|
|Subject                |ID from 1-30 denoting the person who took part in the experiment |
|Activity               |6 activities performed by the subject in file *activity_labels.txt*| 
|Features               |Measurements (mean,standard deviation,max,min etc.) of signals (tBodyAcc-XYZ, tGravityAcc-XYZ, tBodyAccJerk-XYZ etc). More information can be found in *features_info.txt*                                                                       |


## Data Cleaning Operations

#### 1. Merge the features, subject and activity tables into one data set ```data```

```r
str(data)
```

```
## 'data.frame':	10299 obs. of  563 variables:
##  $ tBodyAcc-mean()-X                   : num  0.257 0.286 0.275 0.27 0.275 ...
##  $ tBodyAcc-mean()-Y                   : num  -0.0233 -0.0132 -0.0261 -0.0326 -0.0278 ...
##  $ tBodyAcc-mean()-Z                   : num  -0.0147 -0.1191 -0.1182 -0.1175 -0.1295 ...
##  $ tBodyAcc-std()-X                    : num  -0.938 -0.975 -0.994 -0.995 -0.994 ...
##  $ tBodyAcc-std()-Y                    : num  -0.92 -0.967 -0.97 -0.973 -0.967 ...
##  $ tBodyAcc-std()-Z                    : num  -0.668 -0.945 -0.963 -0.967 -0.978 ...
##  $ tBodyAcc-mad()-X                    : num  -0.953 -0.987 -0.994 -0.995 -0.994 ...
##  $ tBodyAcc-mad()-Y                    : num  -0.925 -0.968 -0.971 -0.974 -0.966 ...
##  $ tBodyAcc-mad()-Z                    : num  -0.674 -0.946 -0.963 -0.969 -0.977 ...
##  $ tBodyAcc-max()-X                    : num  -0.894 -0.894 -0.939 -0.939 -0.939 ...
##  $ tBodyAcc-max()-Y                    : num  -0.555 -0.555 -0.569 -0.569 -0.561 ...
##  $ tBodyAcc-max()-Z                    : num  -0.466 -0.806 -0.799 -0.799 -0.826 ...
##  $ tBodyAcc-min()-X                    : num  0.717 0.768 0.848 0.848 0.849 ...
##  $ tBodyAcc-min()-Y                    : num  0.636 0.684 0.668 0.668 0.671 ...
##  $ tBodyAcc-min()-Z                    : num  0.789 0.797 0.822 0.822 0.83 ...
##  $ tBodyAcc-sma()                      : num  -0.878 -0.969 -0.977 -0.974 -0.975 ...
##  $ tBodyAcc-energy()-X                 : num  -0.998 -1 -1 -1 -1 ...
##  $ tBodyAcc-energy()-Y                 : num  -0.998 -1 -1 -0.999 -0.999 ...
##  $ tBodyAcc-energy()-Z                 : num  -0.934 -0.998 -0.999 -0.999 -0.999 ...
##  $ tBodyAcc-iqr()-X                    : num  -0.976 -0.994 -0.993 -0.995 -0.993 ...
##  $ tBodyAcc-iqr()-Y                    : num  -0.95 -0.974 -0.974 -0.979 -0.967 ...
##  $ tBodyAcc-iqr()-Z                    : num  -0.83 -0.951 -0.965 -0.97 -0.976 ...
##  $ tBodyAcc-entropy()-X                : num  -0.168 -0.302 -0.618 -0.75 -0.591 ...
##  $ tBodyAcc-entropy()-Y                : num  -0.379 -0.348 -0.695 -0.899 -0.74 ...
##  $ tBodyAcc-entropy()-Z                : num  0.246 -0.405 -0.537 -0.554 -0.799 ...
##  $ tBodyAcc-arCoeff()-X,1              : num  0.521 0.507 0.242 0.175 0.116 ...
##  $ tBodyAcc-arCoeff()-X,2              : num  -0.4878 -0.1565 -0.115 -0.0513 -0.0289 ...
##  $ tBodyAcc-arCoeff()-X,3              : num  0.4823 0.0407 0.0327 0.0342 -0.0328 ...
##  $ tBodyAcc-arCoeff()-X,4              : num  -0.0455 0.273 0.1924 0.1536 0.2943 ...
##  $ tBodyAcc-arCoeff()-Y,1              : num  0.21196 0.19757 -0.01194 0.03077 0.00063 ...
##  $ tBodyAcc-arCoeff()-Y,2              : num  -0.1349 -0.1946 -0.0634 -0.1293 -0.0453 ...
##  $ tBodyAcc-arCoeff()-Y,3              : num  0.131 0.411 0.471 0.446 0.168 ...
##  $ tBodyAcc-arCoeff()-Y,4              : num  -0.0142 -0.3405 -0.5074 -0.4195 -0.0682 ...
##  $ tBodyAcc-arCoeff()-Z,1              : num  -0.106 0.0776 0.1885 0.2715 0.0744 ...
##  $ tBodyAcc-arCoeff()-Z,2              : num  0.0735 -0.084 -0.2316 -0.2258 0.0271 ...
##  $ tBodyAcc-arCoeff()-Z,3              : num  -0.1715 0.0353 0.6321 0.4164 -0.1459 ...
##  $ tBodyAcc-arCoeff()-Z,4              : num  0.0401 -0.0101 -0.5507 -0.2864 -0.0502 ...
##  $ tBodyAcc-correlation()-X,Y          : num  0.077 -0.105 0.3057 -0.0638 0.2352 ...
##  $ tBodyAcc-correlation()-X,Z          : num  -0.491 -0.429 -0.324 -0.167 0.29 ...
##  $ tBodyAcc-correlation()-Y,Z          : num  -0.709 0.399 0.28 0.545 0.458 ...
##  $ tGravityAcc-mean()-X                : num  0.936 0.927 0.93 0.929 0.927 ...
##  $ tGravityAcc-mean()-Y                : num  -0.283 -0.289 -0.288 -0.293 -0.303 ...
##  $ tGravityAcc-mean()-Z                : num  0.115 0.153 0.146 0.143 0.138 ...
##  $ tGravityAcc-std()-X                 : num  -0.925 -0.989 -0.996 -0.993 -0.996 ...
##  $ tGravityAcc-std()-Y                 : num  -0.937 -0.984 -0.988 -0.97 -0.971 ...
##  $ tGravityAcc-std()-Z                 : num  -0.564 -0.965 -0.982 -0.992 -0.968 ...
##  $ tGravityAcc-mad()-X                 : num  -0.93 -0.989 -0.996 -0.993 -0.996 ...
##  $ tGravityAcc-mad()-Y                 : num  -0.938 -0.983 -0.989 -0.971 -0.971 ...
##  $ tGravityAcc-mad()-Z                 : num  -0.606 -0.965 -0.98 -0.993 -0.969 ...
##  $ tGravityAcc-max()-X                 : num  0.906 0.856 0.856 0.856 0.854 ...
##  $ tGravityAcc-max()-Y                 : num  -0.279 -0.305 -0.305 -0.305 -0.313 ...
##  $ tGravityAcc-max()-Z                 : num  0.153 0.153 0.139 0.136 0.134 ...
##  $ tGravityAcc-min()-X                 : num  0.944 0.944 0.949 0.947 0.946 ...
##  $ tGravityAcc-min()-Y                 : num  -0.262 -0.262 -0.262 -0.273 -0.279 ...
##  $ tGravityAcc-min()-Z                 : num  -0.0762 0.149 0.145 0.1421 0.1309 ...
##  $ tGravityAcc-sma()                   : num  -0.0178 0.0577 0.0406 0.0461 0.0554 ...
##  $ tGravityAcc-energy()-X              : num  0.829 0.806 0.812 0.809 0.804 ...
##  $ tGravityAcc-energy()-Y              : num  -0.865 -0.858 -0.86 -0.854 -0.843 ...
##  $ tGravityAcc-energy()-Z              : num  -0.968 -0.957 -0.961 -0.963 -0.965 ...
##  $ tGravityAcc-iqr()-X                 : num  -0.95 -0.988 -0.996 -0.992 -0.996 ...
##  $ tGravityAcc-iqr()-Y                 : num  -0.946 -0.982 -0.99 -0.973 -0.972 ...
##  $ tGravityAcc-iqr()-Z                 : num  -0.76 -0.971 -0.979 -0.996 -0.969 ...
##  $ tGravityAcc-entropy()-X             : num  -0.425 -0.729 -0.823 -0.823 -0.83 ...
##  $ tGravityAcc-entropy()-Y             : num  -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 ...
##  $ tGravityAcc-entropy()-Z             : num  0.219 -0.465 -0.53 -0.7 -0.302 ...
##  $ tGravityAcc-arCoeff()-X,1           : num  -0.43 -0.51 -0.295 -0.343 -0.482 ...
##  $ tGravityAcc-arCoeff()-X,2           : num  0.431 0.525 0.305 0.359 0.539 ...
##  $ tGravityAcc-arCoeff()-X,3           : num  -0.432 -0.54 -0.315 -0.375 -0.596 ...
##  $ tGravityAcc-arCoeff()-X,4           : num  0.433 0.554 0.326 0.392 0.655 ...
##  $ tGravityAcc-arCoeff()-Y,1           : num  -0.795 -0.746 -0.232 -0.233 -0.493 ...
##  $ tGravityAcc-arCoeff()-Y,2           : num  0.781 0.733 0.169 0.176 0.463 ...
##  $ tGravityAcc-arCoeff()-Y,3           : num  -0.78 -0.737 -0.155 -0.169 -0.465 ...
##  $ tGravityAcc-arCoeff()-Y,4           : num  0.785 0.749 0.164 0.185 0.483 ...
##  $ tGravityAcc-arCoeff()-Z,1           : num  -0.984 -0.845 -0.429 -0.297 -0.536 ...
##  $ tGravityAcc-arCoeff()-Z,2           : num  0.987 0.869 0.44 0.304 0.544 ...
##  $ tGravityAcc-arCoeff()-Z,3           : num  -0.989 -0.893 -0.451 -0.311 -0.553 ...
##  $ tGravityAcc-arCoeff()-Z,4           : num  0.988 0.913 0.458 0.315 0.559 ...
##  $ tGravityAcc-correlation()-X,Y       : num  0.981 0.945 0.548 0.986 0.998 ...
##  $ tGravityAcc-correlation()-X,Z       : num  -0.996 -0.911 -0.335 0.653 0.916 ...
##  $ tGravityAcc-correlation()-Y,Z       : num  -0.96 -0.739 0.59 0.747 0.929 ...
##  $ tBodyAccJerk-mean()-X               : num  0.072 0.0702 0.0694 0.0749 0.0784 ...
##  $ tBodyAccJerk-mean()-Y               : num  0.04575 -0.01788 -0.00491 0.03227 0.02228 ...
##  $ tBodyAccJerk-mean()-Z               : num  -0.10604 -0.00172 -0.01367 0.01214 0.00275 ...
##  $ tBodyAccJerk-std()-X                : num  -0.907 -0.949 -0.991 -0.991 -0.992 ...
##  $ tBodyAccJerk-std()-Y                : num  -0.938 -0.973 -0.971 -0.973 -0.979 ...
##  $ tBodyAccJerk-std()-Z                : num  -0.936 -0.978 -0.973 -0.976 -0.987 ...
##  $ tBodyAccJerk-mad()-X                : num  -0.916 -0.969 -0.991 -0.99 -0.991 ...
##  $ tBodyAccJerk-mad()-Y                : num  -0.937 -0.974 -0.973 -0.973 -0.977 ...
##  $ tBodyAccJerk-mad()-Z                : num  -0.949 -0.979 -0.975 -0.978 -0.985 ...
##  $ tBodyAccJerk-max()-X                : num  -0.903 -0.915 -0.992 -0.992 -0.994 ...
##  $ tBodyAccJerk-max()-Y                : num  -0.95 -0.981 -0.975 -0.975 -0.986 ...
##  $ tBodyAccJerk-max()-Z                : num  -0.891 -0.978 -0.962 -0.962 -0.986 ...
##  $ tBodyAccJerk-min()-X                : num  0.898 0.898 0.994 0.994 0.994 ...
##  $ tBodyAccJerk-min()-Y                : num  0.95 0.968 0.976 0.976 0.98 ...
##  $ tBodyAccJerk-min()-Z                : num  0.946 0.966 0.966 0.97 0.985 ...
##  $ tBodyAccJerk-sma()                  : num  -0.931 -0.974 -0.982 -0.983 -0.987 ...
##  $ tBodyAccJerk-energy()-X             : num  -0.995 -0.998 -1 -1 -1 ...
##  $ tBodyAccJerk-energy()-Y             : num  -0.997 -0.999 -0.999 -0.999 -1 ...
##  $ tBodyAccJerk-energy()-Z             : num  -0.997 -0.999 -0.999 -0.999 -1 ...
##   [list output truncated]
```


#### 2. Create ```data_subset```, which is a subset of ```data``` containing only mean and standard deviation measurements. Modify the column names and ```data_subset$activity``` to make them more descriptive.

```r
str(data_subset)
```

```
## 'data.frame':	10299 obs. of  68 variables:
##  $ timeBodyAccelerometer-mean()-X                : num  0.257 0.286 0.275 0.27 0.275 ...
##  $ timeBodyAccelerometer-mean()-Y                : num  -0.0233 -0.0132 -0.0261 -0.0326 -0.0278 ...
##  $ timeBodyAccelerometer-mean()-Z                : num  -0.0147 -0.1191 -0.1182 -0.1175 -0.1295 ...
##  $ timeBodyAccelerometer-std()-X                 : num  -0.938 -0.975 -0.994 -0.995 -0.994 ...
##  $ timeBodyAccelerometer-std()-Y                 : num  -0.92 -0.967 -0.97 -0.973 -0.967 ...
##  $ timeBodyAccelerometer-std()-Z                 : num  -0.668 -0.945 -0.963 -0.967 -0.978 ...
##  $ timeGravityAccelerometer-mean()-X             : num  0.936 0.927 0.93 0.929 0.927 ...
##  $ timeGravityAccelerometer-mean()-Y             : num  -0.283 -0.289 -0.288 -0.293 -0.303 ...
##  $ timeGravityAccelerometer-mean()-Z             : num  0.115 0.153 0.146 0.143 0.138 ...
##  $ timeGravityAccelerometer-std()-X              : num  -0.925 -0.989 -0.996 -0.993 -0.996 ...
##  $ timeGravityAccelerometer-std()-Y              : num  -0.937 -0.984 -0.988 -0.97 -0.971 ...
##  $ timeGravityAccelerometer-std()-Z              : num  -0.564 -0.965 -0.982 -0.992 -0.968 ...
##  $ timeBodyAccelerometerJerk-mean()-X            : num  0.072 0.0702 0.0694 0.0749 0.0784 ...
##  $ timeBodyAccelerometerJerk-mean()-Y            : num  0.04575 -0.01788 -0.00491 0.03227 0.02228 ...
##  $ timeBodyAccelerometerJerk-mean()-Z            : num  -0.10604 -0.00172 -0.01367 0.01214 0.00275 ...
##  $ timeBodyAccelerometerJerk-std()-X             : num  -0.907 -0.949 -0.991 -0.991 -0.992 ...
##  $ timeBodyAccelerometerJerk-std()-Y             : num  -0.938 -0.973 -0.971 -0.973 -0.979 ...
##  $ timeBodyAccelerometerJerk-std()-Z             : num  -0.936 -0.978 -0.973 -0.976 -0.987 ...
##  $ timeBodyGyroscope-mean()-X                    : num  0.11998 -0.00155 -0.04821 -0.05664 -0.05999 ...
##  $ timeBodyGyroscope-mean()-Y                    : num  -0.0918 -0.1873 -0.1663 -0.126 -0.0847 ...
##  $ timeBodyGyroscope-mean()-Z                    : num  0.1896 0.1807 0.1542 0.1183 0.0787 ...
##  $ timeBodyGyroscope-std()-X                     : num  -0.883 -0.926 -0.973 -0.968 -0.975 ...
##  $ timeBodyGyroscope-std()-Y                     : num  -0.816 -0.93 -0.979 -0.975 -0.978 ...
##  $ timeBodyGyroscope-std()-Z                     : num  -0.941 -0.968 -0.976 -0.963 -0.968 ...
##  $ timeBodyGyroscopeJerk-mean()-X                : num  -0.2049 -0.1387 -0.0978 -0.1022 -0.0918 ...
##  $ timeBodyGyroscopeJerk-mean()-Y                : num  -0.1745 -0.0258 -0.0342 -0.0447 -0.029 ...
##  $ timeBodyGyroscopeJerk-mean()-Z                : num  -0.0934 -0.0714 -0.06 -0.0534 -0.0612 ...
##  $ timeBodyGyroscopeJerk-std()-X                 : num  -0.901 -0.962 -0.984 -0.984 -0.988 ...
##  $ timeBodyGyroscopeJerk-std()-Y                 : num  -0.911 -0.956 -0.988 -0.99 -0.992 ...
##  $ timeBodyGyroscopeJerk-std()-Z                 : num  -0.939 -0.981 -0.976 -0.981 -0.982 ...
##  $ timeBodyAccelerometerMagnitude-mean()         : num  -0.867 -0.969 -0.976 -0.974 -0.976 ...
##  $ timeBodyAccelerometerMagnitude-std()          : num  -0.705 -0.954 -0.979 -0.977 -0.977 ...
##  $ timeGravityAccelerometerMagnitude-mean()      : num  -0.867 -0.969 -0.976 -0.974 -0.976 ...
##  $ timeGravityAccelerometerMagnitude-std()       : num  -0.705 -0.954 -0.979 -0.977 -0.977 ...
##  $ timeBodyAccelerometerJerkMagnitude-mean()     : num  -0.93 -0.974 -0.982 -0.983 -0.987 ...
##  $ timeBodyAccelerometerJerkMagnitude-std()      : num  -0.896 -0.941 -0.971 -0.975 -0.989 ...
##  $ timeBodyGyroscopeMagnitude-mean()             : num  -0.796 -0.898 -0.939 -0.947 -0.957 ...
##  $ timeBodyGyroscopeMagnitude-std()              : num  -0.762 -0.911 -0.972 -0.97 -0.969 ...
##  $ timeBodyGyroscopeJerkMagnitude-mean()         : num  -0.925 -0.973 -0.987 -0.989 -0.99 ...
##  $ timeBodyGyroscopeJerkMagnitude-std()          : num  -0.894 -0.944 -0.984 -0.986 -0.99 ...
##  $ frequencyBodyAccelerometer-mean()-X           : num  -0.919 -0.961 -0.992 -0.993 -0.992 ...
##  $ frequencyBodyAccelerometer-mean()-Y           : num  -0.918 -0.964 -0.965 -0.968 -0.969 ...
##  $ frequencyBodyAccelerometer-mean()-Z           : num  -0.789 -0.957 -0.967 -0.967 -0.98 ...
##  $ frequencyBodyAccelerometer-std()-X            : num  -0.948 -0.984 -0.995 -0.996 -0.995 ...
##  $ frequencyBodyAccelerometer-std()-Y            : num  -0.925 -0.97 -0.974 -0.977 -0.967 ...
##  $ frequencyBodyAccelerometer-std()-Z            : num  -0.636 -0.942 -0.962 -0.969 -0.978 ...
##  $ frequencyBodyAccelerometerJerk-mean()-X       : num  -0.9 -0.944 -0.991 -0.991 -0.991 ...
##  $ frequencyBodyAccelerometerJerk-mean()-Y       : num  -0.937 -0.969 -0.973 -0.972 -0.98 ...
##  $ frequencyBodyAccelerometerJerk-mean()-Z       : num  -0.924 -0.973 -0.972 -0.97 -0.983 ...
##  $ frequencyBodyAccelerometerJerk-std()-X        : num  -0.924 -0.962 -0.992 -0.992 -0.994 ...
##  $ frequencyBodyAccelerometerJerk-std()-Y        : num  -0.943 -0.98 -0.971 -0.975 -0.979 ...
##  $ frequencyBodyAccelerometerJerk-std()-Z        : num  -0.948 -0.981 -0.972 -0.981 -0.989 ...
##  $ frequencyBodyGyroscope-mean()-X               : num  -0.824 -0.923 -0.973 -0.972 -0.976 ...
##  $ frequencyBodyGyroscope-mean()-Y               : num  -0.808 -0.926 -0.981 -0.981 -0.98 ...
##  $ frequencyBodyGyroscope-mean()-Z               : num  -0.918 -0.968 -0.972 -0.967 -0.969 ...
##  $ frequencyBodyGyroscope-std()-X                : num  -0.903 -0.927 -0.973 -0.967 -0.974 ...
##  $ frequencyBodyGyroscope-std()-Y                : num  -0.823 -0.932 -0.977 -0.972 -0.977 ...
##  $ frequencyBodyGyroscope-std()-Z                : num  -0.956 -0.97 -0.979 -0.965 -0.97 ...
##  $ frequencyBodyAccelerometerMagnitude-mean()    : num  -0.791 -0.954 -0.976 -0.973 -0.978 ...
##  $ frequencyBodyAccelerometerMagnitude-std()     : num  -0.711 -0.96 -0.984 -0.982 -0.979 ...
##  $ frequencyBodyAccelerometerJerkMagnitude-mean(): num  -0.895 -0.945 -0.971 -0.972 -0.987 ...
##  $ frequencyBodyAccelerometerJerkMagnitude-std() : num  -0.896 -0.934 -0.97 -0.978 -0.99 ...
##  $ frequencyBodyGyroscopeMagnitude-mean()        : num  -0.771 -0.924 -0.975 -0.976 -0.977 ...
##  $ frequencyBodyGyroscopeMagnitude-std()         : num  -0.797 -0.917 -0.974 -0.971 -0.97 ...
##  $ frequencyBodyGyroscopeJerkMagnitude-mean()    : num  -0.89 -0.952 -0.986 -0.986 -0.99 ...
##  $ frequencyBodyGyroscopeJerkMagnitude-std()     : num  -0.907 -0.938 -0.983 -0.986 -0.991 ...
##  $ subject                                       : int  1 1 1 1 1 1 1 1 1 1 ...
##  $ activity                                      : Factor w/ 6 levels "LAYING","SITTING",..: 3 3 3 3 3 3 3 3 3 3 ...
```

#### 3. Create an independent tidy data set which displays the average of each measurement for each ```subject``` and ```activity```.

```r
str(data_tidy)
```

```
## Classes 'grouped_df', 'tbl_df', 'tbl' and 'data.frame':	180 obs. of  68 variables:
##  $ subject                                       : int  1 1 1 1 1 1 2 2 2 2 ...
##  $ activity                                      : Factor w/ 6 levels "LAYING","SITTING",..: 1 2 3 4 5 6 1 2 3 4 ...
##  $ timeBodyAccelerometer-mean()-X                : num  0.281 0.276 0.278 0.276 0.278 ...
##  $ timeBodyAccelerometer-mean()-Y                : num  -0.0182 -0.0131 -0.0173 -0.0186 -0.0227 ...
##  $ timeBodyAccelerometer-mean()-Z                : num  -0.107 -0.11 -0.104 -0.106 -0.117 ...
##  $ timeBodyAccelerometer-std()-X                 : num  -0.9741 -0.9867 -0.9851 -0.4236 0.0464 ...
##  $ timeBodyAccelerometer-std()-Y                 : num  -0.9803 -0.949 -0.9361 -0.0781 0.2629 ...
##  $ timeBodyAccelerometer-std()-Z                 : num  -0.984 -0.959 -0.931 -0.425 -0.103 ...
##  $ timeGravityAccelerometer-mean()-X             : num  -0.51 0.927 0.915 0.913 0.862 ...
##  $ timeGravityAccelerometer-mean()-Y             : num  0.7525 -0.0246 -0.2702 -0.3466 -0.3258 ...
##  $ timeGravityAccelerometer-mean()-Z             : num  0.6468 0.1947 0.1537 0.0847 -0.0439 ...
##  $ timeGravityAccelerometer-std()-X              : num  -0.959 -0.981 -0.985 -0.973 -0.94 ...
##  $ timeGravityAccelerometer-std()-Y              : num  -0.988 -0.958 -0.963 -0.972 -0.94 ...
##  $ timeGravityAccelerometer-std()-Z              : num  -0.984 -0.956 -0.93 -0.972 -0.931 ...
##  $ timeBodyAccelerometerJerk-mean()-X            : num  0.0826 0.0737 0.0745 0.0618 0.11 ...
##  $ timeBodyAccelerometerJerk-mean()-Y            : num  0.01225 0.00843 0.00741 0.01825 -0.00328 ...
##  $ timeBodyAccelerometerJerk-mean()-Z            : num  -0.0018 0.00441 -0.01405 0.0079 -0.02094 ...
##  $ timeBodyAccelerometerJerk-std()-X             : num  -0.986 -0.986 -0.978 -0.278 0.147 ...
##  $ timeBodyAccelerometerJerk-std()-Y             : num  -0.9832 -0.9744 -0.9629 -0.0166 0.1268 ...
##  $ timeBodyAccelerometerJerk-std()-Z             : num  -0.988 -0.987 -0.98 -0.586 -0.34 ...
##  $ timeBodyGyroscope-mean()-X                    : num  -0.0185 -0.0481 -0.0257 -0.053 -0.1159 ...
##  $ timeBodyGyroscope-mean()-Y                    : num  -0.1118 -0.06705 -0.08077 -0.04824 -0.00482 ...
##  $ timeBodyGyroscope-mean()-Z                    : num  0.1449 0.0553 0.0887 0.0828 0.0972 ...
##  $ timeBodyGyroscope-std()-X                     : num  -0.988 -0.984 -0.948 -0.562 -0.321 ...
##  $ timeBodyGyroscope-std()-Y                     : num  -0.982 -0.977 -0.965 -0.538 -0.416 ...
##  $ timeBodyGyroscope-std()-Z                     : num  -0.96 -0.957 -0.951 -0.481 -0.279 ...
##  $ timeBodyGyroscopeJerk-mean()-X                : num  -0.102 -0.0923 -0.106 -0.0819 -0.0581 ...
##  $ timeBodyGyroscopeJerk-mean()-Y                : num  -0.0359 -0.0411 -0.0426 -0.0538 -0.0421 ...
##  $ timeBodyGyroscopeJerk-mean()-Z                : num  -0.0702 -0.0423 -0.0553 -0.0515 -0.071 ...
##  $ timeBodyGyroscopeJerk-std()-X                 : num  -0.993 -0.988 -0.97 -0.39 -0.244 ...
##  $ timeBodyGyroscopeJerk-std()-Y                 : num  -0.99 -0.991 -0.981 -0.634 -0.469 ...
##  $ timeBodyGyroscopeJerk-std()-Z                 : num  -0.988 -0.985 -0.971 -0.435 -0.218 ...
##  $ timeBodyAccelerometerMagnitude-mean()         : num  -0.977 -0.967 -0.95 -0.29 0.09 ...
##  $ timeBodyAccelerometerMagnitude-std()          : num  -0.973 -0.953 -0.941 -0.423 0.216 ...
##  $ timeGravityAccelerometerMagnitude-mean()      : num  -0.977 -0.967 -0.95 -0.29 0.09 ...
##  $ timeGravityAccelerometerMagnitude-std()       : num  -0.973 -0.953 -0.941 -0.423 0.216 ...
##  $ timeBodyAccelerometerJerkMagnitude-mean()     : num  -0.98774 -0.985 -0.97574 -0.28142 0.00566 ...
##  $ timeBodyAccelerometerJerkMagnitude-std()      : num  -0.986 -0.983 -0.972 -0.164 0.23 ...
##  $ timeBodyGyroscopeMagnitude-mean()             : num  -0.95 -0.943 -0.942 -0.447 -0.162 ...
##  $ timeBodyGyroscopeMagnitude-std()              : num  -0.961 -0.958 -0.93 -0.553 -0.275 ...
##  $ timeBodyGyroscopeJerkMagnitude-mean()         : num  -0.992 -0.99 -0.979 -0.548 -0.411 ...
##  $ timeBodyGyroscopeJerkMagnitude-std()          : num  -0.99 -0.989 -0.974 -0.558 -0.343 ...
##  $ frequencyBodyAccelerometer-mean()-X           : num  -0.977 -0.986 -0.981 -0.346 0.113 ...
##  $ frequencyBodyAccelerometer-mean()-Y           : num  -0.9798 -0.9558 -0.9436 -0.0219 0.2783 ...
##  $ frequencyBodyAccelerometer-mean()-Z           : num  -0.984 -0.97 -0.951 -0.454 -0.131 ...
##  $ frequencyBodyAccelerometer-std()-X            : num  -0.9732 -0.9873 -0.9871 -0.4577 0.0161 ...
##  $ frequencyBodyAccelerometer-std()-Y            : num  -0.981 -0.948 -0.936 -0.169 0.172 ...
##  $ frequencyBodyAccelerometer-std()-Z            : num  -0.985 -0.956 -0.925 -0.455 -0.162 ...
##  $ frequencyBodyAccelerometerJerk-mean()-X       : num  -0.986 -0.986 -0.978 -0.305 0.138 ...
##  $ frequencyBodyAccelerometerJerk-mean()-Y       : num  -0.9828 -0.9738 -0.9625 -0.0788 0.0962 ...
##  $ frequencyBodyAccelerometerJerk-mean()-Z       : num  -0.986 -0.985 -0.976 -0.555 -0.271 ...
##  $ frequencyBodyAccelerometerJerk-std()-X        : num  -0.987 -0.988 -0.981 -0.314 0.05 ...
##  $ frequencyBodyAccelerometerJerk-std()-Y        : num  -0.985 -0.9771 -0.9663 -0.0153 0.0808 ...
##  $ frequencyBodyAccelerometerJerk-std()-Z        : num  -0.989 -0.988 -0.982 -0.616 -0.408 ...
##  $ frequencyBodyGyroscope-mean()-X               : num  -0.986 -0.98 -0.943 -0.43 -0.146 ...
##  $ frequencyBodyGyroscope-mean()-Y               : num  -0.983 -0.981 -0.968 -0.555 -0.362 ...
##  $ frequencyBodyGyroscope-mean()-Z               : num  -0.9627 -0.9575 -0.9495 -0.3967 -0.0875 ...
##  $ frequencyBodyGyroscope-std()-X                : num  -0.989 -0.985 -0.95 -0.604 -0.379 ...
##  $ frequencyBodyGyroscope-std()-Y                : num  -0.982 -0.975 -0.964 -0.533 -0.459 ...
##  $ frequencyBodyGyroscope-std()-Z                : num  -0.963 -0.961 -0.956 -0.56 -0.423 ...
##  $ frequencyBodyAccelerometerMagnitude-mean()    : num  -0.975 -0.962 -0.952 -0.324 0.293 ...
##  $ frequencyBodyAccelerometerMagnitude-std()     : num  -0.9751 -0.9553 -0.944 -0.5771 -0.0215 ...
##  $ frequencyBodyAccelerometerJerkMagnitude-mean(): num  -0.985 -0.982 -0.972 -0.169 0.222 ...
##  $ frequencyBodyAccelerometerJerkMagnitude-std() : num  -0.985 -0.982 -0.971 -0.164 0.227 ...
##  $ frequencyBodyGyroscopeMagnitude-mean()        : num  -0.972 -0.97 -0.945 -0.531 -0.321 ...
##  $ frequencyBodyGyroscopeMagnitude-std()         : num  -0.961 -0.958 -0.932 -0.652 -0.373 ...
##  $ frequencyBodyGyroscopeJerkMagnitude-mean()    : num  -0.99 -0.989 -0.975 -0.583 -0.38 ...
##  $ frequencyBodyGyroscopeJerkMagnitude-std()     : num  -0.989 -0.989 -0.975 -0.558 -0.344 ...
##  - attr(*, "vars")=List of 1
##   ..$ : symbol subject
##  - attr(*, "drop")= logi TRUE
```

```r
#Display the first 6 rows of the tidy data set
head(data_tidy,6)
```

```
## Source: local data frame [6 x 68]
## Groups: subject
## 
##   subject           activity timeBodyAccelerometer-mean()-X
## 1       1             LAYING                      0.2813734
## 2       1            SITTING                      0.2759908
## 3       1           STANDING                      0.2776850
## 4       1            WALKING                      0.2764266
## 5       1 WALKING_DOWNSTAIRS                      0.2776153
## 6       1   WALKING_UPSTAIRS                      0.2471648
## Variables not shown: timeBodyAccelerometer-mean()-Y (dbl),
##   timeBodyAccelerometer-mean()-Z (dbl), timeBodyAccelerometer-std()-X
##   (dbl), timeBodyAccelerometer-std()-Y (dbl),
##   timeBodyAccelerometer-std()-Z (dbl), timeGravityAccelerometer-mean()-X
##   (dbl), timeGravityAccelerometer-mean()-Y (dbl),
##   timeGravityAccelerometer-mean()-Z (dbl),
##   timeGravityAccelerometer-std()-X (dbl), timeGravityAccelerometer-std()-Y
##   (dbl), timeGravityAccelerometer-std()-Z (dbl),
##   timeBodyAccelerometerJerk-mean()-X (dbl),
##   timeBodyAccelerometerJerk-mean()-Y (dbl),
##   timeBodyAccelerometerJerk-mean()-Z (dbl),
##   timeBodyAccelerometerJerk-std()-X (dbl),
##   timeBodyAccelerometerJerk-std()-Y (dbl),
##   timeBodyAccelerometerJerk-std()-Z (dbl), timeBodyGyroscope-mean()-X
##   (dbl), timeBodyGyroscope-mean()-Y (dbl), timeBodyGyroscope-mean()-Z
##   (dbl), timeBodyGyroscope-std()-X (dbl), timeBodyGyroscope-std()-Y (dbl),
##   timeBodyGyroscope-std()-Z (dbl), timeBodyGyroscopeJerk-mean()-X (dbl),
##   timeBodyGyroscopeJerk-mean()-Y (dbl), timeBodyGyroscopeJerk-mean()-Z
##   (dbl), timeBodyGyroscopeJerk-std()-X (dbl),
##   timeBodyGyroscopeJerk-std()-Y (dbl), timeBodyGyroscopeJerk-std()-Z
##   (dbl), timeBodyAccelerometerMagnitude-mean() (dbl),
##   timeBodyAccelerometerMagnitude-std() (dbl),
##   timeGravityAccelerometerMagnitude-mean() (dbl),
##   timeGravityAccelerometerMagnitude-std() (dbl),
##   timeBodyAccelerometerJerkMagnitude-mean() (dbl),
##   timeBodyAccelerometerJerkMagnitude-std() (dbl),
##   timeBodyGyroscopeMagnitude-mean() (dbl),
##   timeBodyGyroscopeMagnitude-std() (dbl),
##   timeBodyGyroscopeJerkMagnitude-mean() (dbl),
##   timeBodyGyroscopeJerkMagnitude-std() (dbl),
##   frequencyBodyAccelerometer-mean()-X (dbl),
##   frequencyBodyAccelerometer-mean()-Y (dbl),
##   frequencyBodyAccelerometer-mean()-Z (dbl),
##   frequencyBodyAccelerometer-std()-X (dbl),
##   frequencyBodyAccelerometer-std()-Y (dbl),
##   frequencyBodyAccelerometer-std()-Z (dbl),
##   frequencyBodyAccelerometerJerk-mean()-X (dbl),
##   frequencyBodyAccelerometerJerk-mean()-Y (dbl),
##   frequencyBodyAccelerometerJerk-mean()-Z (dbl),
##   frequencyBodyAccelerometerJerk-std()-X (dbl),
##   frequencyBodyAccelerometerJerk-std()-Y (dbl),
##   frequencyBodyAccelerometerJerk-std()-Z (dbl),
##   frequencyBodyGyroscope-mean()-X (dbl), frequencyBodyGyroscope-mean()-Y
##   (dbl), frequencyBodyGyroscope-mean()-Z (dbl),
##   frequencyBodyGyroscope-std()-X (dbl), frequencyBodyGyroscope-std()-Y
##   (dbl), frequencyBodyGyroscope-std()-Z (dbl),
##   frequencyBodyAccelerometerMagnitude-mean() (dbl),
##   frequencyBodyAccelerometerMagnitude-std() (dbl),
##   frequencyBodyAccelerometerJerkMagnitude-mean() (dbl),
##   frequencyBodyAccelerometerJerkMagnitude-std() (dbl),
##   frequencyBodyGyroscopeMagnitude-mean() (dbl),
##   frequencyBodyGyroscopeMagnitude-std() (dbl),
##   frequencyBodyGyroscopeJerkMagnitude-mean() (dbl),
##   frequencyBodyGyroscopeJerkMagnitude-std() (dbl)
```
