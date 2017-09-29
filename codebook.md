
Download ad unzipping the data into the workign directory from link below 
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

File with R code "run_analysis.R" perform the following:

Merging the training and the test sets to create one data set.
    Reading trainings tables
    Reading testing tables
    Reading feature vector
    Reading activitylabels
    Assigning column names
    Merging all data in one set
Extracting only the measurements on the mean and standard deviation for each measurement
    Reading column names
    Create vector for defining ID, mean and standard deviation
    Making nessesary subset from setAllInOne
Creating a second, independent tidy data set with the average of each variable for each activity and each subject
    Making second tidy data set
    Writing second tidy data set in txt file

Variables:
x_train, y_train, x_test, y_test, subject_train and subject_test contain the data from the downloaded files.
x_data, y_data and subject_data merge the previous datasets for analysis.
> dim(secTidySet)
[1] 180  82
> class(secTidySet)
[1] "data.frame"
> colnames(secTidySet)
 [1] "subjectId"                       "activityId"                      "tBodyAcc-mean()-X"              
 [4] "tBodyAcc-mean()-Y"               "tBodyAcc-mean()-Z"               "tBodyAcc-std()-X"               
 [7] "tBodyAcc-std()-Y"                "tBodyAcc-std()-Z"                "tGravityAcc-mean()-X"           
[10] "tGravityAcc-mean()-Y"            "tGravityAcc-mean()-Z"            "tGravityAcc-std()-X"            
[13] "tGravityAcc-std()-Y"             "tGravityAcc-std()-Z"             "tBodyAccJerk-mean()-X"          
[16] "tBodyAccJerk-mean()-Y"           "tBodyAccJerk-mean()-Z"           "tBodyAccJerk-std()-X"           
[19] "tBodyAccJerk-std()-Y"            "tBodyAccJerk-std()-Z"            "tBodyGyro-mean()-X"             
[22] "tBodyGyro-mean()-Y"              "tBodyGyro-mean()-Z"              "tBodyGyro-std()-X"              
[25] "tBodyGyro-std()-Y"               "tBodyGyro-std()-Z"               "tBodyGyroJerk-mean()-X"         
[28] "tBodyGyroJerk-mean()-Y"          "tBodyGyroJerk-mean()-Z"          "tBodyGyroJerk-std()-X"          
[31] "tBodyGyroJerk-std()-Y"           "tBodyGyroJerk-std()-Z"           "tBodyAccMag-mean()"             
[34] "tBodyAccMag-std()"               "tGravityAccMag-mean()"           "tGravityAccMag-std()"           
[37] "tBodyAccJerkMag-mean()"          "tBodyAccJerkMag-std()"           "tBodyGyroMag-mean()"            
[40] "tBodyGyroMag-std()"              "tBodyGyroJerkMag-mean()"         "tBodyGyroJerkMag-std()"         
[43] "fBodyAcc-mean()-X"               "fBodyAcc-mean()-Y"               "fBodyAcc-mean()-Z"              
[46] "fBodyAcc-std()-X"                "fBodyAcc-std()-Y"                "fBodyAcc-std()-Z"               
[49] "fBodyAcc-meanFreq()-X"           "fBodyAcc-meanFreq()-Y"           "fBodyAcc-meanFreq()-Z"          
[52] "fBodyAccJerk-mean()-X"           "fBodyAccJerk-mean()-Y"           "fBodyAccJerk-mean()-Z"          
[55] "fBodyAccJerk-std()-X"            "fBodyAccJerk-std()-Y"            "fBodyAccJerk-std()-Z"           
[58] "fBodyAccJerk-meanFreq()-X"       "fBodyAccJerk-meanFreq()-Y"       "fBodyAccJerk-meanFreq()-Z"      
[61] "fBodyGyro-mean()-X"              "fBodyGyro-mean()-Y"              "fBodyGyro-mean()-Z"             
[64] "fBodyGyro-std()-X"               "fBodyGyro-std()-Y"               "fBodyGyro-std()-Z"              
[67] "fBodyGyro-meanFreq()-X"          "fBodyGyro-meanFreq()-Y"          "fBodyGyro-meanFreq()-Z"         
[70] "fBodyAccMag-mean()"              "fBodyAccMag-std()"               "fBodyAccMag-meanFreq()"         
[73] "fBodyBodyAccJerkMag-mean()"      "fBodyBodyAccJerkMag-std()"       "fBodyBodyAccJerkMag-meanFreq()" 
[76] "fBodyBodyGyroMag-mean()"         "fBodyBodyGyroMag-std()"          "fBodyBodyGyroMag-meanFreq()"    
[79] "fBodyBodyGyroJerkMag-mean()"     "fBodyBodyGyroJerkMag-std()"      "fBodyBodyGyroJerkMag-meanFreq()"
[82] "activityType"                   
> rownames(secTidySet)
  [1] "1"   "31"  "61"  "91"  "121" "151" "2"   "32"  "62"  "92"  "122" "152" "3"   "33"  "63"  "93"  "123" "153" "4"   "34" 
 [21] "64"  "94"  "124" "154" "5"   "35"  "65"  "95"  "125" "155" "6"   "36"  "66"  "96"  "126" "156" "7"   "37"  "67"  "97" 
 [41] "127" "157" "8"   "38"  "68"  "98"  "128" "158" "9"   "39"  "69"  "99"  "129" "159" "10"  "40"  "70"  "100" "130" "160"
 [61] "11"  "41"  "71"  "101" "131" "161" "12"  "42"  "72"  "102" "132" "162" "13"  "43"  "73"  "103" "133" "163" "14"  "44" 
 [81] "74"  "104" "134" "164" "15"  "45"  "75"  "105" "135" "165" "16"  "46"  "76"  "106" "136" "166" "17"  "47"  "77"  "107"
[101] "137" "167" "18"  "48"  "78"  "108" "138" "168" "19"  "49"  "79"  "109" "139" "169" "20"  "50"  "80"  "110" "140" "170"
[121] "21"  "51"  "81"  "111" "141" "171" "22"  "52"  "82"  "112" "142" "172" "23"  "53"  "83"  "113" "143" "173" "24"  "54" 
[141] "84"  "114" "144" "174" "25"  "55"  "85"  "115" "145" "175" "26"  "56"  "86"  "116" "146" "176" "27"  "57"  "87"  "117"
[161] "147" "177" "28"  "58"  "88"  "118" "148" "178" "29"  "59"  "89"  "119" "149" "179" "30"  "60"  "90"  "120" "150" "180"
> 
