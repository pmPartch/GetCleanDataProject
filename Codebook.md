# Codebook for Project

Data Science class *Getting and Cleaning Data*

## data transformations

Units of [standard gravity](http://en.wikipedia.org/wiki/Standard_gravity) and angular velocity (radians/sec). The meaurements were made for body accleration, rate of change of acceleration (Jerk), and angular acceleration

Of the sampled data (see list below), only the first two items were reatained (1. mean() and 2. std()). The raw data was filtered to remove all but the columns that measured mean and standard deviation.

1. mean(): Mean value
1. std(): Standard deviation
1. mad(): Median absolute deviation 
1. max(): Largest value in array
1. min(): Smallest value in array
1. sma(): Signal magnitude area
1. energy(): Energy measure. Sum of the squares divided by the number of values. 
1. iqr(): Interquartile range 
1. entropy(): Signal entropy
1. arCoeff(): Autorregresion coefficients with Burg order equal to 4
1. correlation(): correlation coefficient between two signals
1. maxInds(): index of the frequency component with largest magnitude
1. meanFreq(): Weighted average of the frequency components to obtain a mean frequency
1. skewness(): skewness of the frequency domain signal 
1. kurtosis(): kurtosis of the frequency domain signal 
1. bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT of each window.
1. angle(): Angle between to vectors.

## Processing of raw data to derive the tidy data set

The following processing was performed:

1. uncompress the raw data from [UCI HAR Dataset](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)
1. load the activity labels (with associated activity id's)
1. load the feature labels (with associated feature column numbers)
1. load the test data
    1. subject data contining the subject ID per record
    1. the raw recorded data for each feature
    1. the activity performed for each record and replace the activity id with its corresponding label
1. load the training data
    1. subject data contining the subject ID per record
    1. the raw recorded data for each feature
    1. the activity performed for each record and replace the activity id with its corresponding label
1. Verify there is no missing data
1. merge the test data, training data, then finally merge both sets together
1. assign labels to each column where the subject id is named SubjectID, the activity column is named Activity and the feature columns are labeld via the features table (to be explanded in a step below)
1. collapse the rows by forming a mean of the measured feature data for a given subject ID and specific activity
1. remove columns that cannot be used (see section below 'removed columns from the raw data sets due to naming mistakes')
1. expand the feature names to a more human readable form (see section 'Column name changes')


## multiple sample taken for a given subject and activity

Each subject (of 30) were all measured multiple times for each acvitity (WALKING, WALKING\_UPSTAIRS, WALKING\_DOWNSTAIRS, SITTING, STANDING, LAYING)

## removed columns from the raw data sets due to naming mistakes

The reason why these were removed were the lack of the X/Y/Z axis indicators. Also, some of these names were mistyped (BodyBody substrings)

- "tBodyAccMag-mean()"
- "tBodyAccMag-std()"
- "tGravityAccMag-mean()"
- "tGravityAccMag-std()"
- "tBodyAccJerkMag-mean()"
- "tBodyAccJerkMag-std()"
- "tBodyGyroMag-mean()"
- "tBodyGyroMag-std()"
- "tBodyGyroJerkMag-mean()"
- "tBodyGyroJerkMag-std()"
- "fBodyAccMag-mean()"
- "fBodyAccMag-std()"
- "fBodyBodyAccJerkMag-mean()"
- "fBodyBodyAccJerkMag-std()"
- "fBodyBodyGyroMag-mean()"
- "fBodyBodyGyroMag-std()"
- "fBodyBodyGyroJerkMag-mean()"
- "fBodyBodyGyroJerkMag-std()" 

## Column name changes

The feature names were expanded and [CamelCase or Pascal case](http://en.wikipedia.org/wiki/CamelCase). I also decided to separate the workds with '.' since I found it more readable (but unfortunatly makes the names long). The following name transformations were made:

- 't' was changed to 'Time'
- 'f' was changed to 'Frequency'
- 'Acc' was changed to 'Acceleration'
- 'mean()' was changed to 'Mean'
- 'std()' was changed to 'StdDev'
- the names were separated by '.'
- finally, a trailing 'Mean was added

and example would be 'fBodyAccJerk-mean()-Z' changes to 'Frequency.Body.Acceleration.Jerk.Mean.Z Mean'

### Processing Environment

The data was processed using the following enviroment (dump using sessionInfo())

R version 3.1.2 (2014-10-31)
Platform: x86_64-w64-mingw32/x64 (64-bit)

locale:
[1] LC_COLLATE=English_United States.1252  LC_CTYPE=English_United States.1252    LC_MONETARY=English_United States.1252
[4] LC_NUMERIC=C                           LC_TIME=English_United States.1252    

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
[1] reshape2_1.4.1

loaded via a namespace (and not attached):
[1] plyr_1.8.1    Rcpp_0.11.3   stringr_0.6.2 tools_3.1.2  
