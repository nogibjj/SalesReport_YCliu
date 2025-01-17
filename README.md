[![Python Continuous Integration](https://github.com/nogibjj/SalesReport_YCLiu/actions/workflows/cicd.yml/badge.svg)](https://github.com/nogibjj/SalesReport_YCLiu/actions/workflows/cicd.yml)

## Sales Status Dashboard for Actionable Insights

This repository demonstrates how to use **Azure Databricks Notebook to automaticaly generate year to date (YTD) sales report everyday**. Using a Databricks notebook, online retail data saved on the cloud was extracted, turned into table, filterd and aggregated to generate **a bar chart of top revenue generating products** that can be used for regular sales status monitoring. The pipeline is set to be triggered every day at _3am_ ([Project walkthrough video](https://youtu.be/3xreA-jm0aY)).

Below is an overview of the repository:
   
1. **Main script generating sales dashboard**
   <br>a. _SalesReport.ipynb_: The ipython notebook for generating sales dashboard, specifically, the following are executed:
   <br>i. **Load** online sales data in the cloud.
   <br>ii. **Create PySpark SQL table** _sales_data_ and fill in _all_ rows from sales data source, namely _InvoiceNo_, _StockCode_, _Description_, _Quantity_, _InvoiceDate_, _UnitPrice_, _CustomerID_. Also, add a column name _Revenue_, which is the product of _Quantity_ and _UnitPrice_.
   <br>iii. **Filter data of the the year** to **reduce the amount of data** and turn the result into a pandas dataframe.
   <br>iv. **Aggregate revenue per product** and **sort products from the highest YTD revenue to the lowest**.
   <br>v. **Generate a dashboard of top YTD revenue generating products**.
   <br>vi. **Validate result correctness**.

   ## Actionable Insights for Sales Management Team
      The **sales comapaign for couples giving each other gifts**（e.g. hanging heart light holder, heart of wicker) worked well. However, white light holder seems to be more popular than the red ones, we should **work on making sure our stock can meet customers' needs**.
      
   **Resulted Dashboard**
   
   <img width="587" alt="Dashboard" src="https://github.com/nogibjj/SalesReport_YCLiu/assets/46064664/b15c0a34-9198-4c98-ac94-a9d32e9b160b">

   | StockCode | Description | Revenue |
   |---|---|---|
   | 85123A | WHITE HANGING HEART T-LIGHT HOLDER | 13313.72 |
   | DOT | DOTCOM POSTAGE | 9506.67 |
   | 22423 | REGENCY CAKESTAND 3 TIER | 8223.05 |
   | 21108 | FAIRY CAKE FLANNEL ASSORTED COLOUR | 6687.22 |
   | 48185 | DOORMAT FAIRY CAKE | 5043.64 |
   | 79321 | CHILLI LIGHTS | 5008.77 |
   | 22470 | HEART OF WICKER LARGE | 4876.32 |
   | 21175 | GIN + TONIC DIET METAL SIGN | 4387.64 |
   | 22469 | HEART OF WICKER SMALL | 4114.07 |
   | 21733 | RED HANGING HEART T-LIGHT HOLDER | 3853.05 |
   

   **Scheduled execution** (The **dashboard is updated everyday at 3 am**)
   
<img width="811" alt="ScheduledUpdate" src="https://github.com/nogibjj/SalesReport_YCLiu/assets/46064664/e817a97c-b07e-4bea-950f-c49d0865ea97">

2. **Github actions setup for continuous integration**
  <br>b. _.github/workflows/cicd.yml_: Quality control actions are triggered when pushed/ pulled to main branch.  

3. **Other files for development environment settings**
  <br>c. _.gitignore_: specify file names to ignore.
  <br>d. _requirements.txt_: list required packages for the project.

4. **Description of the project**
   <br>e. _README.md_: THIS FILE, explaining the purpose and structure of the directory, with example output and screenshots of scheduled execution.

