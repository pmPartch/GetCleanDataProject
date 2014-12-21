GetCleanDataProject
===================

Project for the Get and Clean Data Course

The following files are available:

- **Codebook.md** a description of the data and transforms from raw input data to the tidy output table  
NOTE: the original codebook.txt has been added as an appendix
- **run_analysis.R** the script that will download, unzip, and create the tidy table.  
To generate the Tidy data set, Run this script and it will
    1. verify that the raw data files are in the current working directory (if not, the script will attempt to download the zip and uncompress it to the current working directory)
    1. merge the data together in to a single data frame
    1. filter out the unwanted columns
    1. replace the activity id's with their labels
    1. melt and then cast the data frame to merge the duplicate activity samples into a single row using mean()
    1. rename the variable by expanding their labels
    1. write the new tidy data frame to the current working directory with the name 'Tidy UCI HAR Dataset.txt'

- **load_and_view_table.R** a small utility script that can load the tidy table  
This script will expect the 'Tidy UCI HAR Dataset.txt' to be in the current working directory and will load it and call View()


