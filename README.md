# AB-Testing-Data-Analysis
The data analysis has been conducted on the dataset of an A/B test for a website. The purpose of the test was to determine whether inclusion of a Haptic feature (touch and feel) for a particular product line in an ecommerce website brought any significant results. In this report, I have made necessary assumptions, set KPIs to be evaluated and used statistical tests to reach a data-driven conclusion.

**About the dataset**

Company: One of the fastest growing online retailers in Dhaka, Bangladesh
Link to dataset and task brief: 
https://drive.google.com/drive/folders/1weqXOjnJk8GvUBT4DSQi2Edk6ciFbyO9?usp=sharing
Purpose: A/B testing to determine whether adding a haptic description (touch and feel) for the product category “Men’s Suit” would improve customer response or not.
Test: 	Page A – Contains ‘Touch & Feel’ haptic feature
	Page B – Does not contain ‘Touch & Feel’ haptic feature
Test duration: 83 days
Given data fields: 
-	Day Index
-	Date Range
-	Segment
-	Sessions
-	Percentage of New Sessions
-	New Users
-	Bounce Rate
-	Pages per Session
-	Average Session Duration
-	Ecommerce Conversion Rate
-	Transactions
-	Revenue (BDT)

**Assumptions and new calculated fields**

Since a glossary of the data was not provided, I have made the following core assumptions for the analysis of the dataset:
1.	The _Session_ field only contains number of Unique Sessions. This assumption has been made since checking the dataset revealed that the _New Users_ field is a calculation of (_Percentage of New Sessions_ * _Sessions_).
2.	According to Google Analytics, _Ecommerce Conversion Rate_ is defined as ratio of _Transactions_ to _Total Sessions_. I have used this formula to calculate the number of _Total Sessions_ for the website as (_Transactions_ / _Ecommerce Conversion Rate_).
3.	According to Google Analytics, _Bounce Rate_ is the ratio of the number of single-page sessions to that of _Total Sessions_. I have used this formula to calculate the number of _Bounced Sessions_ for the website as (_Bounce rate_ * _Total Sessions_). Hence, the _Session not Bounced_ are calculated as (_Total Sessions_ – _Bounced Sessions_). 
4.	I have assumed that _Transactions_ gives the number of _Sessions Converted_. Hence the _Sessions not Converted_ are calculated as (_Total Sessions_ – _Transactions_).
Other calculated fields include:
-	_Average order value_: _Revenue_ / _Transactions_
-	_Average Revenue per Session_: _Revenue_ / _Total Sessions_  
-	_Average Revenue per User_: _Revenue_ / _Unique Sessions_  

**A/B testing parameters and choice of statistical tests**

Since the website is a retail ecommerce website, the following Key Performance Indicators are important:
-	Number of new users 
-	Bounce rate
-	Conversion rate
-	Average session duration
-	Average revenue per session
-	Average order value
-	Average order value per user
Since the primary objective of a retail ecommerce is to generate sales, so I will consider –
_Primary KPI_: Conversion rate
_Secondary KPI_: Average revenue per user
Here, it is important to note that number of new sessions, bounce rate, conversion rate – these are discrete metrics. For example, conversion rate denotes two possible outcomes – the session either converted into a sale, or it did not. Similarly, bounce rate denotes two possible outcomes – the session bounced after single-page view, or it did not. 
On the other hand, KPIs such as average session duration, average revenue per session, average order value, average revenue per user – these are continuous metrics. Such metrics cannot denote any binary outcome like discrete metrics.
Chi Square test is a better fit for analyzing discrete data compared to T-Test. It is also better than the Fisher’s exact test since the sample size here is relatively large (n = 83). On the other hand, T-Test is a good fit for samples or population that are normally distributed. A preliminary visualization showed that although skewed to a degree, average session duration, average revenue per session, average order value, average revenue per user - are all relatively normally distributed. Please check the Appendix A to see the visualizations.
