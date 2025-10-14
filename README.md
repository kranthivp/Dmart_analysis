# Dmart_analysis


## Description



## Problem Statement

The task is to create a data pipeline using PySpark to integrate and analyze sales data from three different sources: product information, sales transactions, and customer details. The goal is to establish a connection with PySpark, load the datasets, perform data transformations, and answer a set of analytical questions.

## Steps followed

Step 1:-  From the given url the data is downloaded in to local

    'https://drive.google.com/drive/folders/1Y7Q27S00milOYuPnO7NHLl3sQGd49Ng6?usp=sharing'

Step 2:-  Installing pyspark environment
 
    '!pip install pyspark'

Step 3:- Establishing  pyspark connection

    'from pyspark.sql import SparkSession
     spark = SparkSession.builder\
     .master("local")\
     .appName("Colab")\
     .config('spark.ui.port', '4050')\
     .getOrCreate()'

Step 4:-  Script to load the data from csv files to pyspark dataframes.    

    'customer_df = spark.read.csv('Customer.csv', header=True)'
    'product_df = spark.read.csv('Product.csv', header=True)'
    'sales_df = spark.read.csv('Sales.csv', header=True)'

Step 5:-  Checking if there are any null values in the dataframe.

    'from pyspark.sql.functions import col, isnan, when, count
     sales_df.select([count(when(col(a).isNull(), a)).alias(a) for a in sales_df.columns]).show()
     product_df.select([count(when(col(b).isNull(),b)).alias(b) for b in product_df.columns]).show()
     customer_df.select([count(when(col(c).isNull(),c)).alias(c) for c in customer_df.columns]).show()'
