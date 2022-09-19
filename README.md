# Amazon_Vine_Analysis
## Big Data analysis using Google Colab, Pyspark, Postgresv / pgAdmin, AWS RDS, Pandas and SQL

![Amazon_Vine_Program_a](https://user-images.githubusercontent.com/103727169/190926381-076cb5a4-ed2a-4448-b699-bf256d950328.jpg)

## Overview

The purpose of this project is to analyze Amazon reviews written by members of the paid Amazon Vine program, a service that allows manufacturers and publishers to receive reviews of their products and determine if there are any biases between Vine members and Non-Vine member's reviews.

Companies that will pay a fee to Amazon and may provide free products to Vine members who are then required to publish a review. In order to determine if there is any bias towards favorable reviews from Vine members vs. non-members, we need to identify the percentage of 5 star ratings to total rating. As part of this exercise, we were asked to choose from 50 datasets to extract, transform and load into a dataframe in order to complete our analysis. Throughout this analysis, we use:

&#x1F539; PySpark to extract the dataset, transform the data, connect to AWS RDS instance and load the transformed data into pgAdmin.

&#x1F538; Google Colaboratory to import PySpark libraries and connect to Postgres in order to create SQL tables and export the results.

Of the 50 datasets, I chose to analyze reviews that were made by users in the "Apparel" category.

Dataset used for this analysis can be found
[Click Here](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Apparel_v1_00.tsv.gz)


## Results

The dataset had over 3 million reviews recorded. In order to focus on reviews that would be considered more likely to be helpful, we needed to filter the dataset by:

&#x1F539; Count of Total Votes equal or greater than 20.

&#x1F538; Percent of Helpful Votes to Total Votes equal or greater than 50%.

![percent_votes_df](https://user-images.githubusercontent.com/103727169/190926915-bfb440cb-74a9-4eac-ae80-10a483a7902d.png)

The results reduced the total number of reviews from 3M to 45.3K. This allowed us to answer the following questions:

&#x1F539; **How many Vine reviews and non-Vine reviews were there?**

**Vine members** made up only .07% (33) of the reviews whereas the remaining 99.88 % were **Non-Vine members** (45246).

![review5star](https://user-images.githubusercontent.com/103727169/190927094-70152654-6391-4deb-9ade-2ac1424f6fa9.png)

![paid_vine_program](https://user-images.githubusercontent.com/103727169/190927369-f31b0988-8bad-4ea3-b003-79c2b1154d3d.png)

![non_paid_vine_program](https://user-images.githubusercontent.com/103727169/190927378-cef74a01-ea1d-4e1a-89e9-99f717c5eca2.png)


&#x1F539; How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?
* **Vine members** gave 15 out of 33 reviews a 5 star rating.
* **Non-Vine members** gave 23639 out of 45246 reviews a 5 star rating.

&#x1F539; What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?
* 45% of the reviews for **Vine members** were rated 5 Stars.
* 52.25% of the reviews for **Non-Vine members** were rated 5 Stars.

## Summary

Based on the results, **Vine members** did not show bias when rating their products considering that the number of 5-star ratings was about 10% less than **Non-Vine members** (45% vs. 52.25%). With this, we can assume that Vine customers are more critical when submitting their review. However, in order to support this assumption further, we should include all of the data rather than filtering it to a percentage of helpful vs. total votes as we did for this analysis. Reviewing the data as is would give us more information and allow us to further support our assumption as shown below.


![review_vine_df](https://user-images.githubusercontent.com/103727169/190927841-0210a60f-3276-4cde-bd50-55049c19fe89.png)

In addition, running the same analysis using datasets from different product categories can provide us with the whole picture of whether reviews made by **Vine members are bias.**









