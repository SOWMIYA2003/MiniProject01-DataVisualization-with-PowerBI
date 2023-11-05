# MiniProject01-DataVisualization-with-PowerBI

## Introduction

Data visualization is a powerful tool for understanding numerical data. It can help users to identify patterns and trends that would be difficult to see in raw data. Power BI is a popular data visualization tool that provides a variety of features for creating interactive reports.

This project investigates the use of Power BI to visualize numerical data and identify trends. The goal of the project is to develop a method for generating interactive reports that can help business users make more informed decisions.

![A](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/9922042f-08dd-4550-8fbd-2c513e1e8ba9)

## Statement of the Problem

Business Intelligence is a technology-driven discipline that transforms raw data into meaningful insights to support business decisions. It involves the use of tools, applications, and methodologies to collect, analyse, and present data, helping businesses to improve efficiency and profitability. 

In this project , we will be creating a BI dashboard with the help of Microsoft PowerBI to analyze the Raw data from the business firm and identify patterns and trends. This helps the concerned people to deal with their product resources and enhance the firm’s performance in the market.

## Purpose of the project
The purpose of this project is to develop a method for generating interactive reports that can help business users make more informed decisions. The project will focus on using Power BI to visualize numerical data and identify trends.
## Proposed Methodology

The proposed methodology for this project is as follows:

1.	Clean the raw data using EDA methods and import into SQL database.

2.	Load cleaned numerical data from a SQL database into Power BI.

3.	Use Power BI's UI elements to generate interactive reports that can help business users identify trends and patterns.

4.	Test the reports with business users to ensure that they are easy to understand and use.

5.	Refine the reports based on feedback from business users.
   
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/aff95a48-2a3e-4802-87ae-8127568cc965)
## Flow Diagram
![Q](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/e63cf32a-616f-4a77-9fdd-58a050562966)

## Expected results and its Implications

The expected results of this project are as follows:

•	A method for generating interactive reports that can help business users make more informed decisions.

•	A set of interactive reports that can be used by business users to visualize numerical data and identify trends.

The implications of this project are that business users will be able to make more informed decisions based on data visualization. This can lead to improved business performance.
## Architecture Diagram
![Picture1](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/90bf6b58-439a-4236-b1d1-b35c0080deb6)

## Data Collection and Data Cleaning
Data collection or data gathering is the process of gathering and measuring information on targeted variables in an established system, which then enables one to answer relevant questions and evaluate outcomes.

The gathered dataset is being cleaned using python and pandas library. The dataset is being read and the null values , duplicate values are removed from the dataset and conversion of the terms is done and a new cleaned data is generated using pandas library and python.

![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/43c70dfb-55e5-4cd4-bb33-5bb2628bd695)

![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/7a531180-a9f5-4ee1-b272-df38eebcaa1e)

## Exploratory Data Analysis

In statistics, exploratory data analysis is an approach of analyzing data sets to summarize their main characteristics, often using statistical graphics and other data visualization methods. From the cleaned dataset , using python and pandas library we get the details regarding the total revenue that is the sum of sales amount from the transaction table and likewise for total sales quantity which is the total of sales qty from transaction table.

EDA involves studying of data and therefore certain information regarding the revenue and sales quantity based on the year and month has been studied with regard to the customer and market details. The python code to perform the exploratory data analysis is discussed in the below topic

![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/b0d128c4-f3fd-4e40-9863-736afdffdf19)

![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/89f8ba6d-2b7c-44f1-9b19-88fcd6d08180)

## Code 
This project involves 5 different datasets namely customers, transactions , date, markets, products. 
```
# importing pandas library
import pandas as pd

# reading dataset
data_1=pd.read_csv('sales_market.csv')
data_1
data_2=pd.read_csv('sales_customers.csv')
data_2
data_3=pd.read_csv('sales_transactions.csv')
data_3
data_4=pd.read_csv('sales_date.csv')
data_4
data_5=pd.read_csv('sales_products.csv')
data_5

# checking for non null data count and type of data
data_1.info()
data_2.info()
data_3.info()
data_4.info()
data_5.info()

# checking for duplicate values
duplicates1 = data_1[data_1.duplicated()]
duplicates1
duplicates2 = data_2[data_2.duplicated()]
duplicates2
duplicates3 = data_3[data_3.duplicated()]
duplicates3
duplicates4 = data_4[data_4.duplicated()]
duplicates4
duplicates5 = data_5[data_5.duplicated()]
duplicates5

# dropping the duplicate data
data_1 = data_1.drop_duplicates()
data_1
data_2 = data_2.drop_duplicates()
data_2
data_3 = data_3.drop_duplicates()
data_3
data_4 = data_4.drop_duplicates()
data_4
data_5 = data_5.drop_duplicates()
data_5

# to find the count of particular type
value_counts_5 = data_5['product_type'].value_counts()
value_counts_5
value_counts_4 = data_4['year'].value_counts()
value_counts_4
value_counts_3 = data_3['currency'].value_counts()
value_counts_3

# to drop the null values 
data_1 = data_1.dropna()
data_1

# to find the unique terms
unique_values_3 = data_3['currency'].unique()
unique_values_3

# replacing INR\r into INR and USD\r to USD

data_3['currency'] = data_3['currency'].str.replace('INR\r', 'INR')
data_3['currency'] = data_3['currency'].str.replace('USD\r', 'USD')
data_3

# checking record that has currency type as USD
usd_data = data_3[data_3['currency'] == 'USD']
usd_data

# converting USD into INR
def convert_to_inr(row):
    if row['currency'] == 'USD':
        return row['sales_amount'] * 75
    else:
        return row['sales_amount']
data_3['sales_amount'] = data_3.apply(convert_to_inr, axis=1)
data_3

# to download the cleaned data into csv file
data_1.to_csv('eda_market.csv', index=False)
data_2.to_csv('eda_customers.csv', index=False)
data_3.to_csv('eda_transactions.csv', index=False)
data_4.to_csv('eda_date.csv', index=False)
data_5.to_csv('eda_products.csv', index=False)

##EDA
# total revenue
total_sales_sum = data_3['sales_amount'].sum()
total_sales_sum

#total sales qty
total_sales_qty = data_3['sales_qty'].sum()
total_sales_qty

# overall revenue based on month 
data_3['order_date'] = pd.to_datetime(data_3['order_date'])
monthly_sales_sum = data_3.groupby(data_3['order_date'].dt.month)['sales_amount'].sum()
monthly_sales_sum

# overall sales qty based on month 
data_3['order_date'] = pd.to_datetime(data_3['order_date'])
monthly_sales_qty = data_3.groupby(data_3['order_date'].dt.month)['sales_qty'].sum()
monthly_sales_qty

# revenue based on year
data_3['year'] = data_3['order_date'].dt.year
yearly_sales_sum = data_3.groupby('year')['sales_amount'].sum().reset_index()
yearly_sales_sum

# sales qty based on year
data_3['year'] = data_3['order_date'].dt.year
yearly_sales_qty = data_3.groupby('year')['sales_qty'].sum().reset_index()
yearly_sales_qty

#revenue based on year and month
data_3['month'] = data_3['order_date'].dt.month
data_3['year'] = data_3['order_date'].dt.year
yearmonth_sales_sum = data_3.groupby(['year', 'month'])['sales_amount'].sum()
yearmonth_sales_sum

# sales qty based on year and month
data_3['month'] = data_3['order_date'].dt.month
data_3['year'] = data_3['order_date'].dt.year
yearmonth_sales_qty = data_3.groupby(['year', 'month'])['sales_qty'].sum()
yearmonth_sales_qty

# to calculate revenue based on the customer name
customerdata=pd.read_csv('sales_customers.csv')
customerdata

#customer name - sales amount
merged_data = pd.merge(data_3, customerdata, on='customer_code', how='inner')
customer_revenue = merged_data.groupby('customer_code')['sales_amount'].sum().reset_index()
print(customer_revenue)

#customer name - sales Qty
merged_data = pd.merge(data_3, customerdata, on='customer_code', how='inner')
customer_qty = merged_data.groupby('customer_code')['sales_qty'].sum().reset_index()
print(customer_qty)

# products - sales qty sum
product_sales_qty = data_3.groupby('product_code')['sales_qty'].sum().reset_index()
product_sales_qty

# records of year 2018 - month 3
odata = data_3[(data_3['month'] == 3) & (data['year'] == 2018)]
odata

```
### Output
### Dataset - Customer 
![1](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/3f59697b-fc27-44ed-aca7-2a5086c7b699)
### Dataset - Date
![2](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/c28e6d7d-1664-4447-be0d-7ba5505d3473)
### Dataset - Market 
![3](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/2f9c88d8-60ba-4495-ac0f-4130e5574240)
### Dataset - Products 
![4](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/d74e2a23-be81-4ee3-8d0e-645e9abeb4b7)
### Dataset - Transaction
![5](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/456a5c9d-e459-4a52-a899-e2426e5a2da7)
## Nominal Data
Using the above code of EDA , we will be obtained with the numerical data. These numerical data is useful so as to compare the output after visualization.
### Total Revenue and Sales Quantity
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/f8f59b5e-17f1-41d4-9789-59bd4c1668ef)
### Revenue Based on Months
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/01ceb6ba-ddb3-48cf-b48c-8218fd82bb1a)

From the above figure , we infer that the month January over the 4 years have a total revenue of 1201268 and likewise for others.
### Sales Quantity Based on Months
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/a78893be-336c-4b3d-a373-5b2d42d5ce90)

From the above figure , we infer that the sales quantity for the month January over the 4 years is 564 and likewise for others.

### Revenue Based on Months 
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/40fe6ae4-e63d-4bdf-bfff-20e98ad295cb)

From the above figure , we infer that the revenue for the year 2017 is around 1142610 and likewise for others.

### Sales Quantity Based on Months
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/dffb1572-e237-45db-b7c7-12f36625cddf)

From the above figure , we infer that the sales quantity for the year 2017 is around 1462 and likewise for others.

### Revenue Based on Month and Year
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/fa40fbab-7a93-47cc-b2a6-eb1561d56261)

From the above figure , we infer that the revenue for the year 2017  and month 12 is around 218050 and likewise for others.

### Sales Quantity Based on Month and Year
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/dd9e09d5-132d-4af0-9bcd-78057a0e48d2)

From the above figure , we infer that the sales quantity for the year 2017  and month 12 is around 163 and likewise for others.

### Revenue and Sales quantity based on Customer Code
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/7fbe11ec-1359-427c-a43f-3ceb44011109)

From the above figure , we infer that the revenue for the customer with code Cus001is 300282  and likewise for others.

![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/749d9fa7-8f69-43a8-a5e6-ebb03b25cfc5)

From the above figure , we infer that the sales quantity for the customer with code Cus001 is 527 and likewise for others.

### Transaction that occurred on the year 2018 March
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/fbae554f-2945-4afb-9cc1-4586f5dd33f2)

## Dumping Into SQL database
The cleaned dataset is being loaded into a SQL Database. MySQL Workbench is a visual database design tool that integrates SQL development, administration, database design, creation and maintenance into a single integrated development environment for the MySQL database system.

For the maintenance of the data , the cleaned dataset is being loaded into SQL Database created which can be later used to establish connection with powerbi.

![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/dd91b7b8-c340-4744-9e54-2d1b71783ebe)

## Data Visualization tool – PowerBI
The data from the database named eda is connected with the powerbi tool inorder to manipulate and work with the data and create a interactive dashboard. The tables from the database is being loaded and on loading the dataset , we will be obtained with a data relationship model .

![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/8c8aa8a4-ea43-4cf6-ae50-d00507c4db0c)

## Data Modelling
The data relationship model related the connection between the tables in the database. In the data model we have , all the table is been connected with the transaction table . The transaction table maintains a relationship with all other tables by the attributes present in the table . For example the relation between transaction table and customer table is established via the attribute customer_code from both the tables. Customer_codem is found to be a common attribute from both the tables and thus the relation  and likewise for other tables are also established.

![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/502f9fe2-ad48-43dc-9561-96b81a7b2e3a)

## UI Elements
The Microsoft PowerBI tool offers a number of UI Elements with which an interactive dashboard can be created . The project uses UI elements like Card to display the revenue and sales quantity over the years , it uses Multi-row cards to display the year and months , based on our records we have transaction being recorded over 4 year which is 2017 to 2020 . These four years along with month is displayed using multi-row card , then it uses stacked bar charts that represents the revenue by customer name and we have also used the bar charts to display top 5 customers and products over the year and finally line chart has been used to display the graph of revenue over the time period two more line charts to display sales quantity by year and revenue by year is also be created. For UI elements like bar charts and line chart we have two axis and they take two values into consideration to plot the graph. For example in the main line graph for displaying revenue  , the x axis holds the month details and the y axis holds the revenue details .

![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/a999f327-a592-4bf6-af63-95f41ab79905)

## Interactive Dashboard
Interactive Dashboard with help of the UI elements is finally created in powerbi. The UI elements are just dragged to the main report space and the parameters along with the additional filters such as color , text style are adding . The initial report contains the data visualization of all the four years transaction . On selecting the particular year and month , we will be able to visualize only the particular transactions that occurred in that particular year. We can also select a particular customer from the bar chart and analyze the records of that particular customer. Thus by creating an interactive dashboard the person concerned with the business can analyze , visualize and get information regarding his business in a understandable manner. The Dashboard can also be created in mobile view enabling easy access . The powerbi dashboard can be published using powerbi account in the website and the access can be provided to a team who will also be allowed to manipulate the data and make the dashboard better. On working with a team on collaboration this might turn useful for the people concerned.
### Report over the 4 years
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/34867cd4-28cd-4916-8570-a0c1536a569e)
### Report in the year 2018
![image](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/4f2c3386-4377-4804-b18c-3f493c9f7479)
## Testing 
![a](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/73b682e8-35b6-4649-9f3c-4b4acde4d516)

The above image shows the revenue in the month March in the year 2018.In the left most side we have the image of our interactive dashboard and in the right we have result of python code.
We infer that , Both the values are the same from the above picture , thus verifying that our report is correct.
### Updating 
Let's say that some transaction have been entered incorrectly and thus there is a need to change it in the database.And therefore the organization who deals with the database management makes some changes regarding the sales amount in the database. Example : Let's assume that there is a change in sales amount in 569th transaction .
![b](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/e495ba2b-eaf6-47d1-8dbc-3844527fc13a)

Initially the sales amount in the 569th transaction is Rs. 6713 and lets say the updation amount to be 900000. Thus using SQL query the database management team will change it in the database.

![c](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/af1b7996-a5a4-4af7-b518-95a46f9bcb59)

After the updation in the database , we come to the powerbi dashboard and refresh the dashboard , Now the sales amount has been changed and this will eventually change the revenue for the year 2018 in the month March and even the overall revenue will be changed.

![d](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/73a791d5-ed45-4b3a-b4ba-ce012fa12070)
## Conclusion
The significance of the project is that it provides a method for generating interactive reports that can be used to visualize numerical data and identify patterns and trends. This can help business users make more informed decisions
![Picture2](https://github.com/SOWMIYA2003/MiniProject01-DataVisualization-with-PowerBI/assets/93427443/4bbd1fef-ba02-4d54-8dfc-15a03ae2aa17)

## References

##### Paper

https://www.researchgate.net/publication/321804138_Data_Visualization_for_Business_Intelligence

https://www.researchgate.net/publication/352735133_Data_Visualization_A_Study_of_Tools_and_Challenges

https://www.ijsce.org/wp-content/uploads/papers/v7i3/C3011077317.pdf

##### Books

[1]	Cole Nussbaumer Knaflic “Storytelling with Data” : A Data Visualization Guide for Business Professionals

[2]	Andy Kirk “ Data Visualisation” : A Handbook for Data Driven Design 2019

[3]	Suren Machiraju, Suraj Gaurav “Power BI Data Analysis and Visualization” 2018

[4]	Brian Larson · “Data Analysis with Microsoft Power BI” 2020

[5]	Brett Powell  “Mastering Microsoft Power BI” : Expert Techniques for Effective Data Analytics and Business Intelligence 2018

[6]	Devin Knight, Brian Knight, Mitchell Pearson, Manuel Quintana · 2018“Microsoft Power BI Quick Start Guide” : Build Dashboards and Visualizations to Make Your Data Come to Life

[7]	Alberto Ferrari, Marco Russo “Introducing Microsoft Power BI” · 2016

[8]	Ryan Wade “Advanced Analytics in Power BI with R and Python”Ingesting, Transforming, Visualizing · 2020

[9]	Chandraish Sinha “Mastering Power BI”Build Business Intelligence Applications Powered with DAX Calculations, Insightful Visualizations, Advanced BI Techniques, and Loads of Data Sources (English Edition) 2021

