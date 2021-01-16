# Amazon_Vine_Analysis

## Overview of the analysis
The Amazon vine program is a service that allows manufacturers and publishers to receive reviews for the products. The purpose of this analysis is to analyze the reviews written by the member of this paid program. Companies pay a small fee to Amazon and provide products to Amazon Vine members, who are required to publish a review. 

Access to approximately 50 datasets were given for this project in which reviews for Outdoor gear was selected. Through the use of PySpark, an analysis performed the ETL process. This extracted the dataset, transformed the data, connected to an AWS (Amazon Web Services) RDS instance, and loaded the transformed data into pdAdmin. The next thing was to use PySpark to determine if there is any bias toward favorable reviews from Vine member in the dataset. 

## Results
Prior to analyzing the data to see if there was bias, the large dataset was extracted into four DataFrames. Each dataset had the same columns as seen here: 

![](https://github.com/holleyvoegtle/Amazon_Vine_Analysis/blob/main/images/data%20columns.png)



From there queries were performed on these DataFrames to extract the needed information. The four DataFrames were: customer_table, products_table, review_id_table, and vine_table. The table we go on to further analyze is the vine_table and the result in pgAdmin can be seen here: 

![](https://github.com/holleyvoegtle/Amazon_Vine_Analysis/blob/main/images/vine_table%20in%20pgAdmin.png)



Using PySpark, we took the information from the vine table and ran the analyses to determine if there is bias. The first DataFrame filtered the data try taking the total vote counts that is equal to or greater than 20 that are helpful. Then a new DataFrame was created where the number of helpful votes is divided by total votes is equal to or greater than 50%. Then two new DataFrames were created from here with reviews created from paid reviewers and then unpaid reviewers as seen below. 

![](https://github.com/holleyvoegtle/Amazon_Vine_Analysis/blob/main/images/paid%20and%20unpaid%20DF.png)  



Final results:


### How many Vine reviews and non-Vine reviews were there?
Paid: 107
Unpaid: 39,869

### How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?
Paid: 56
Unpaid: 21,005

### What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?
Paid: 52.3%
Unpaid: 52.7%

## Summary 

Based on the analysis, I would conclude there is no bias with paid and unpaid members for reviews. The only caveat is the sample number for paid reviewers in significantly smaller than unpaid.  But this also illustrates that getting paid for reviews or given the product for free, does not alter the results. An additioinal analysis that could be performed to see if other reviews have bias is to do this same anaysis on two other product review datasets. 
