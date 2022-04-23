# Module 16  Amazon_Vine_Analysis
#### by Terra Lasho 
### Overview of the Analysis: For this project, I have been asked to perform an analysis on the Amazon reviews written by members of the Amazon Vine program for a specific product. This program allows manufacturers and publishers to obtain reviews for their products.  I will have access to ~50 datasets, each specific to a certain product.  I will pick one, and with the help of PySpark, I will perform the ETL process (extract the data, transform[to an AWS RDS instance], and load the data [into pgAdmin]). After this is completed, I will interrogate the reviews using PySpark to determine if there is any bias in the reviews from members in the Vine program (vs. non-members).
## Results
### Deliverable 1: Perform ETL on Amazon Product Reviews
-	For Deliverable 1, I extracted an Amazon review dataset as a DataFrame:
![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot1.png)

![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot5.png)

-	I next created a new database with Amazon RDS:

![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot2.png)

-	I next linked this database to pgAdmin:

![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot3.png)

-	I next ran a new query to create four tables (using a provided challenge_schema.sql) in pgAdmin 

![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot4.png)

-	Next, see the attached Google Colab Notebook (Amazon_Reviews_ETL), where I created specific DataFrames with extracted information corresponding to the tables created in pgAdmin.  Finally, I wrote these DataFrames into each table in pgAdmin using .write.jdbc (see Amazon_Reviews_ETL).

### Deliverable 2: Perform ETL on Amazon Product Reviews
-	For Deliverable 2, I used PySpark and created a new Google Colab Notebook (see Vine_Analysis.ipynb). With this, I first extracted the same dataset as in Deliverable 1, then proceeded to filter this data so that I could answer several specific questions listed below.
-	I first created a dataframe filtered to the total review votes above or equal to 20:

![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot6.png)
-	I next filtered this dataset to create a DataFrame that includes ‘helpful votes ratio’ above or equal to 50%:
![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot7.png)
-	I next filtered this dataset to create a DataFrame that includes a Vine Review:
![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot8.png)
-	I next filtered this dataset to create a DataFrame that does not include a Vine Review:
![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot9.png)

### -How many Vine reviews and non-Vine reviews were there?
-	There was a total of 22 Vine reviews, and 26,987 non-Vine Reviews.
![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot10.png)
![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot11.png)
### -How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?
-	There were 13 Vine 5-star reviews, and 14,475 non-Vine Reviews.
![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot12.png)
![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot13.png)
### -What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?
-	5 star reviews represented 59.1% of Vine reviews, whereas 53.6% of reviews were 5 star in the non-Vine reviews.
![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot14.png)
![](https://github.com/Beetleee/Amazon_Vine_Analysis/blob/main/Resources/Plot15.png)

## Summary
### 59.1% of the reviews in the Vine program were 5 stars reviews whereas the percentage in the non-Vine reviews is 53.6%. There represents only a slight positive bias to Vine member reviews.   We could additionally use statistics to analyze any significant differences between the groups… (mean, median and mode).
