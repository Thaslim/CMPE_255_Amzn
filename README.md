# Sentiment Analysis and Recommender System based on Amazon Reviews

Sentiment Analysis and Recommender System based on Amazon Reviews for Home and Kitchen Dataset.

## Overview
The number of people who prefer online shopping is rapidly increasing due to the technological advancement and convenience of shopping anywhere at any time. The recent studies show that the most of all online shoppers use reviews to decide on what products to buy. Reviews not only help customers, but it also helps to strengthen sellers' trustworthiness. Amazon is the world’s largest retailer with millions of products. This project deals with the study of statistical analysis of reviews and ratings by Amazon users.

   ### Project Goals:
   1. Do topic modeling(LDA) on review comments
   2. Build a recommendation system using collaborative filtering (ALS) method and topic modeling (LDA) method and compare their respective results
   3. Use topics generated from LDA and analyze sentiment of the reviews in order to score products by the topics mentioned in their reviews.


## Data Collection and Preparation

The [amazon review datasets](https://nijianmo.github.io/amazon/index.html) are freely available online. For this analysis we used a dataset specific to the “Home and Kitchen” category. Initially we explored the complete review data which had 21million entries, later we decided to work on a smaller subset which had 7million entries, due to technical difficulties faced by some of us.
The dataset has following fields – reviewerID - the id of the user, asin - Amazon product id, reviewerName - name of the user, vote - the number of times the review was voted helpful, reviewText - the actual content of the review, overall - the rating of the product ranging from 1 to 5, summary - the title of the review, unixReviewTime - the time of the review in Unix format, reviewTime - the time of the review, style -a dictionary of the product metadata, e.g., "Format" is "Hardcover" , image - images that users post after they have received the product.

Link to the preprocessed dataset => [Home & Kitchen Preprocessed Data](https://drive.google.com/drive/folders/1YIFgIOtMTuOEHUJEJfFV_mLE8lwz8unC?usp=sharing)

## Topic Modeling with [LDA](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation)

### Steps to run Topic_modeling.ipynb
The dataset contains roughly 6 million data points. GPU is preferred for faster execution.(used HPC access provided by sjsu)
#### Required packages:
     python version 3.6.10
     pip install gensim
     pip install pandas
     pip install nltk and download(stopwords, wordnet corpuses)
     pip install pyLDAvis
Download Topic_modeling.ipynb and run it using jupyter notebook
Visualize generated topic [here](https://thaslim.github.io/CMPE_255_Amzn/)

## [Recommender system](https://en.wikipedia.org/wiki/Recommender_system) using [ALS](https://spark.apache.org/docs/latest/mllib-collaborative-filtering.html)

### Steps to run file using Apache Spark:
Spark is implemented on Hadoop that is HDFS (hadoop distributed file system). Following versions of Java and Python needs to  be maintained to run recommendation system (ALS) file.
#### Packages:
    1. Maintain java 8 version. java version "1.8.0_102" (brew cask install java8)
    2. Upgrade python to latest version (brew upgrade python)
    3. Install pyspark. (pip3 install pyspark)
   
#### Run the following commands on your terminal:
    1. pip3 show pyspark
   
     Gives below output:

      Name: pyspark
      Version: 2.4.5
      Summary: Apache Spark Python API
      Home-page: https://github.com/apache/spark/tree/master/python
      Author: Spark Developers
      Author-email: dev@spark.apache.org
      License: http://www.apache.org/licenses/LICENSE-2.0
      Location: /opt/anaconda3/lib/python3.7/site-packages
      Requires: py4j
      Required-by: 

    2. vi ~/.bash_profile
    3. export SPARK_HOME= /opt/anaconda3/lib/python3.7/site-packages/pyspark
    4. export PATH=$SPARK_HOME/bin:$PATH
    5. pip3 install findspark
    6. jupyter notebook
   
Now download the [ALS_CF_Recommendation_System](https://github.com/shravanthi94/Amazon-Review-Data-Analysis/blob/master/ALS_CF_Recommendation_System.ipynb) file and run using jupyter notebook.

Dataset after preprocessing for ALS => [als_preprocessed_dataset](https://drive.google.com/drive/folders/1YIFgIOtMTuOEHUJEJfFV_mLE8lwz8unC?usp=sharing)


## Sentiment Analysis

### Steps:


## Tableau for Visualizations
Used tableau for making visualizations on our large dataset holding millions of data.

### Setting up [Tableau](https://www.tableau.com/academic/students/) for visualization
      1. Downloaded Tableau desktop-free version available for students.
      2. MySql workbench latest version is installed. 
      3. Install pymysql and sqlalchemy
      4. Open jupyter Notebook, load the preprocessed dataset into pandas dataframe
      5. Run the following command to establish connection to mysql server
            from sqlalchemy import create_engine
            import pymysql
            engine = create_engine("mysql+pymysql://{user}:{pw}@localhost/{db}".format(user="root",pw="pwd",db="DB_Name"))
      6. Insert whole DataFrame into MySQL using the following line
            df.to_sql('Table_name', con = engine, if_exists = 'append', chunksize = 1000)
      7. Open Tableau select Datasource from MySql server, Open worksheet and start plotting!
      8. Tableau worksheets can be viewed using Tableau Reader
 
### Visualizations : 
1. Sum of ratings for each product to show teh top products having highest ratings. The bars in this plot are labeled by number of records per each productID.
2. Rating category distribution for each product 
3. Overall Rating distribution

