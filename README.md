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
<img src="/images/int_rate_cat.png" width = 1000>
As can be seen, the <strong>interest rate of more than 20%</strong> can potentially be considered as one of the drivers of the customer being charged off, since the percentage of the defaulters in this category of interest rate is much higher than the same percentage in the rest of the categories.


## General Information
- Provide general information about your project here.
- What is the background of your project?
- What is the business probem that your project is trying to solve?
- What is the dataset that is being used?

<!-- You don't have to answer all the questions - just the ones relevant to your project. -->

## Conclusions
- Conclusion 1 from the analysis
- Conclusion 2 from the analysis
- Conclusion 3 from the analysis
- Conclusion 4 from the analysis

<!-- You don't have to answer all the questions - just the ones relevant to your project. -->


## Technologies Used
- library - version 1.0
- library - version 2.0
- library - version 3.0

<!-- As the libraries versions keep on changing, it is recommended to mention the version of library used in this project -->

## Acknowledgements
Give credit here.
- This project was inspired by...
- References if any...
- This project was based on [this tutorial](https://www.example.com).


## Contact
Created by [@githubusername] - feel free to contact me!


<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->
