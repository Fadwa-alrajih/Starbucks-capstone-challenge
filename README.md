Starbucks Capstone Challenge
Project in Data Scientist Nanodegree of Udacity

Table of Contents
Installation
Project Motivation
File Descriptions
Summary of Results
Experience:

Project Motivation
It is the Starbuck's Capstone Challenge of the Data Scientist Nanodegree in Udacity. We get the dataset from the program that creates the data simulates how people make purchasing decisions and how those decisions are influenced by promotional offers. We want to make a recommendation engine that recommends Starbucks which offer should be sent to a particular customer.

We are interested to answer the following two questions:

Which offer should be sent to a particular customer to let the customer buy more?
Which demographic groups respond best to which offer type?
File Descriptions
The notebook available here showcases work related to the above questions.

This data set is a simplified version of the real Starbucks app because the underlying simulator only has one product whereas Starbucks actually sells dozens of products.

The data is contained in three files:

portfolio.json - containing offer ids and meta data about each offer (duration, type, etc.)
profile.json - demographic data for each customer
transcript.json - records for transactions, offers received, offers viewed, and offers completed
Here is the schema and explanation of each variable in the files:

portfolio.json

id (string) - offer id
offer_type (string) - the type of offer ie BOGO, discount, informational
difficulty (int) - the minimum required to spend to complete an offer
reward (int) - the reward is given for completing an offer
duration (int) - time for the offer to be open, in days
channels (list of strings)
profile.json

age (int) - age of the customer
became_member_on (int) - the date when customer created an app account
gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
id (str) - customer id
income (float) - customer's income
transcript.json

event (str) - record description (ie transaction, offer received, offer viewed, etc.)
person (str) - customer id
time (int) - time in hours since the start of the test. The data begins at time t=0
value - (dict of strings) - either an offer id or transaction amount depending on the record

Summary of Results:

I used the above datasets of the Starbucks to check if the offers provided were only viewed or they did complete them, that is,
they really used the offer to make a purchase .

I fully went thorugh the datasets to understand them and see how to use them to check for the above analysis..
I used th ETL process i learnt in SQl to clean the datasets for duplicates, null values and got them ready for analysis.

I created  latent features to improve the datasets,as follows.
I created a new colum age_category from age columm and converted the values to numerical ,
like teen-1, young-2,adult-3 and old-4.

For income_group , I segregated into three numericall values , average: 1, above-average: 2, high: 3, from column-income

For the member-cat, derived from became_memeber_on, i made numerical values, like new: 1, regular: 2, loyal: 3

The gender category has three values- Male, Female and others.

There are 2175 missing values. Male - 8484, Female-6129 and other - 212.

The attractive offer is BOGO-first-for all age groups,  next is Disount offers. 
Last is -informational offers.

Mostly ,  customers with more than 90,000 income range are females and between 30,000 and 60,000 are mostly males.

For Females, offers completed: 14890, 74.87% of total offers viewed. offers viewed numbers: 19889.
For Males, offer completed: 14791, 58.25% of total offers viewed.offer viewed numbers : 25394.

We can also see that both Male and Female customers are spending almost equal time and 
they take about 16 to 17 days to complete the offer. 

we can see that the maximum of number of customers Stabrbucks got was in 2017 and the percentatge of that year was 40%
The number of customers in 2017 was 30938.

we can see that Female customers viewed 75% and Male , 58%. We can definitely say that Female customers are more convinced and 
more attracted by promotions.The main findings of the code can be found at the post available here.

Based on the transcript records, we build an user-item-matrix that represents how users responded to the offers they received. 
We then split the records into the training set and the test set and trained our SVD algorithm to predict how a user responses to a particular offer.
We achieved the lowest mean square error around 0.003823 with 15 latent features with the training set and around 0.009175 with 10 latent features with the testing set. 
After that, we created a recommendation engine that recommends Starbucks which offer should be sent to a particular user.

In the later section, we found out which demographic groups respond best to which offer type. 
Female respond much better than men, in both BOGO and discount. 
Men react slightly better to discount than BOGO. 
We also found that it is better to promote the offer via social media.
Among the ten offers, sending buy 10 dollars get 2 dollars off within 10 days offer via email, web, mobile and social makes Starbucks gain more. It is the best offer so far!

Experience:

For this project, I could use my ETL , SQL and Python skills and it was really challenging.
I would thank Udacity and Starbucks for having given me, such a good opportunity .

The meidum link is here https://medium.com/@fadwa.alrajih88/starbucks-capstone-challenge-4aae24f3534b
