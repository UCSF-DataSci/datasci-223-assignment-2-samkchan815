# Cohort Analysis Write-Up

## Goal
The goal of this analysis was to examine patient cohorts according to different ranges of BMI, and identifying key health indicators such as glucose levelsa and age within each group.


## Approach
To analyze this dataset, we first read in a large patient dataset from a .csv file and converted it to Parquet to allow for faster querying. Next, we out patients who had BMI values less than 10 or greater than 60. With the rest of the patients, we then sorted them into groups according to their BMI (ranging 10 to 60) and gave them appropriate labels: Underweight, Normal, Overweight, and Obese. Finally, we aggregated the data to find the average glucose level, the patient count, and average age in each BMI group.


## Insights and Patterns
According to our output, we can see that as the BMI range goes from underweight to obese, the average glucose level increases as well. Those with underweight BMI range has an average glucose of 95.20 while the obese BMI group has an avaerage glucose of 126.03. In addition, this dataset has a lot more patients in the overweight and obese groups, which can be seen in the patient counts for each group.

## Why Polars?
Polars was used because it is more efficient and faster when handling larger datasets. Using lazy query to analyze the dataset (```scan_parquet()```) helps build an optimized query plan to reduce computation time and memory. In addition, using the ```pipe() ```command helps create a clearer pipeline of what is happening when processing the data. The ```pl.when().then()``` command is used to efficiently categorize our data into the appropriate BMI groups. 