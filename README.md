# Lending Club Case Study


## Table of Contents
* [Problem Statement](#problem-statement)
* [Data Understanding](#data-understanding)
* [Data Cleaning](#data-cleaning)
* [Data Analysis](#data-analysis)
* [Recommendations](#recommendations)
* [Acknowledgements](#acknowledgements)

## Problem Statement
It is important for a Lending Club to identify which group of customers might default, meaning they might be charged off and don't return the money, based on their application. If this identification is not performed correctly, it can lead to loss of business in two ways:
- If the application of the customers who fully pay their loan, is mistakenly rejected, then this will lead to the loss of business.
- If the application of the defaulters are approved, and then later they are charged off and don't return the money back, then this will also lead to loss of business.

In this project the dataset, containing the history of customers of a Lending Club is given, with the information about whether each customer has been charged off or fully paid back the loan.

The objective is to identify the groups of customers who are most likely to default, and advise this to the business.

## Data Understanding
- The dataset of the Lending Club was imported.
- The columns with more than 50% of NaN (null) values were removed, and hence the number of columns dropped to 54 from 111.
- The following columns were also removed:
    - Customer behaviour: since these are used at the time of revieweing the loan application and before approving the application. However, now that all the applications of the customers are approved, these columns are irrelevant to this study
    - the geographic location of the applicant
    - columns that have: (i) only one unique value; (ii) IDs; (iii) only 0 or NaN; (iv) ‘sub_grade’, due to no need for further granularity; (v) URL, description, loan title and employment title since these have no impact on the loan_status.
- The rows that have ‘Current’ value in loan_status column were removed from the dataframe, since it is unknown whether they will be charged off (default) or not.

## Data Cleaning
- The columns 'emp_length' and 'pub_rec_bankruptcies’ are both categorical and still have null values. For these columns, the most frequent element in the column is replaced with the NaN values. (the number of rows (data entries) that are affected are less than 4.50% of the entire rows. Hence, this doesn't significantly impact the analysis.)
- Sanity check performed to ensure: 
        funded_amnt_inv <= funded_amnt <= loan_amnt
- Preparing columns for data analysis
    - The ‘loan_status’ with the entries of 'Fully Paid', 'Charged Off’ were transformed to ‘0’ and ‘1’, respectively, in a new column called ‘charged_off?’.
    - The ‘%’ at the end of the elements in interest rate were removed.
    - All the columns were categorised into bins in order to analyse the data in manageable number of categories rather than in numeric values or in higher number of categories.

In this way, the data were prepared for the next step, i.e. data analysis.

## Data Analysis
- The new categorised columns were gathered into a new dataframe, however, this new dataframe has several duplicates due to the new categories. Hence, the duplicates were removed and the number of entries (rows) reduced to 34848 from 38577.
- For every column of this dataframe, two plots were produced:
    - frequency count plots of categories of ‘charged_off?’ over the new categories of the column
    - percentage frequency count plots of the above plot: in order to observed the share (percentage) of defaulters of every new category of the column.

#### Impact of 'int_rate_cat' on 'charged_off?'
<img src="/images/int_rate_cat.png" width = 800>
As can be seen, the <strong>interest rate of more than 20%</strong> can potentially be considered as one of the drivers of the customer being charged off, since the percentage of the defaulters in this category of interest rate is much higher than the same percentage in the rest of the categories.

#### Impact of 'pub_rec_bankruptcies_cat' on 'charged_off?'
<img src="/images/pub_rec_bankruptcies_cat.png" width = 800>
The customers with <strong>2 public records of bankruptcies</strong> are very probable to default.

#### Impact of ‘purpose' on 'charged_off?'
<img src="/images/purpose.png" width = 800>
The <strong>loan purpose of 'small business'</strong> can also be considered as another driver for the customer to default.

#### Impact of ‘grade' on 'charged_off?'
<img src="/images/grade.png" width = 800>
As can be seen, customers with <strong>LC assigned loan grade of 'G'</strong> is very probable to default due to the much higher percentage of defaulters in this category.

#### Impact of ‘term' on 'charged_off?'
<img src="/images/term.png" width = 800>
The loans with <strong>60 months return term</strong> is very probable to be charged off. Hence, this category of loan term can be considered as one of the drivers to default.

#### Impact of 'funded_amnt_inv_cat', 'funded_amnt_cat', and 'loan_amnt_cat' on 'charged_off?'
<img src="/images/funded_amnt_inv_cat.png" width = 800>
<img src="/images/funded_amnt_cat.png" width = 800>
<img src="/images/loan_amnt_cat.png" width = 800>
As can be seen, in all the above graphs, the percentage share of defaulters in the <strong>'30k-35k' category</strong> is higher compared to the rest of the categories. Hence, this category for 'funded_amnt_inv_cat', 'funded_amnt_cat', and 'loan_amnt_cat' can be considered as one of the drivers for the customer to be charged off.

## Recommendations
Analysis of the data of the Lending Club reveals that the customers within the following categories are most probable to default and cause loss of business to the Lending Club:

- interest rate more than 20%
- 2 public records of bankruptcy
- loan term of 60 months
- loan of 30k-35k during all the stages of application by the customer, approving by the club, and investing by the investors.
- loan purpose of 'small business'
- LC assigned loan grade of 'G'

## Acknowledgements

- I would like to acknowledge the feedback, support and dataset provision by [upGrad](https://www.upgrad.com/gb/) and [The International Institute of Information Technology (IIIT), Bangalore](https://www.iiitb.ac.in/).
- Also, I would like to express my gratitude to [Aditya Bhattacharya](https://www.linkedin.com/in/aditya-bhattacharya-b59155b6/) for providing clarification and guidance to carry out this project.
- Furthermore, the valuable feedback from [Dr Tayeb Jamali](https://www.linkedin.com/in/tayeb-jamali-b1a10937/) is highly appreciated.
