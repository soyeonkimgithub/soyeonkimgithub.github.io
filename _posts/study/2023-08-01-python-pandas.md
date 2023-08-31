---
layout: post
title: LeetCode - Pandas
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Pandas

## Data Filtering - Big Countries
A country is big if:

it has an area of at least three million (i.e., 3000000 km2), or
it has a population of at least twenty-five million (i.e., 25000000).
Write a solution to find the name, population, and area of the big countries.

Return the result table in any order.

~~~python
import pandas as pd

def big_countries(world: pd.DataFrame) -> pd.DataFrame:
  df = world[(world['area']>=3000000) | (world['population']>=25000000)]
  columns = ['name', 'population', 'area']
  return df[columns]
~~~

## Data Filtering - Recyclable and Low Fat Products
Write a solution to find the ids of products that are both low fat and recyclable.

Return the result table in any order.

The result format is in the following example.

~~~python
import pandas as pd

def find_products(products: pd.DataFrame) -> pd.DataFrame:
    df = products[(products['low_fats']=='Y') & (products['recyclable']=='Y')]
    return df[['product_id']]
~~~

## Data Filtering - Customers Who Never Order
Write a solution to find all customers who never order anything.

Return the result table in any order.

The result format is in the following example.

~~~python
import pandas as pd

def find_customers(customers: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    df = customers[~customers['id'].isin(orders['customerId'])][['name']]
    df = df.rename(columns={"name": "Customers"})
    return df
~~~

## Data Filtering - Article Views I
Write a solution to find all the authors that viewed at least one of their own articles.

Return the result table sorted by id in ascending order.

The result format is in the following example.

~~~python
import pandas as pd

def article_views(views: pd.DataFrame) -> pd.DataFrame:
    df = views[views['author_id']==views['viewer_id']]
    df.drop(['article_id', 'viewer_id', 'view_date'], axis='columns', inplace=True)
    df = df.drop_duplicates().rename(columns={'author_id':'id'}).sort_values(by=['id'])
    return df
~~~

## String Methods - Invalid Tweets

Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15.

Return the result table in any order.

The result format is in the following example.

~~~python
import pandas as pd

def invalid_tweets(tweets: pd.DataFrame) -> pd.DataFrame:
    return tweets[tweets['content'].str.len()>15][['tweet_id']]
~~~

## String Methods - Calculate Special Bonus

Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15.

Return the result table in any order.

The result format is in the following example.

~~~python
import pandas as pd

def invalid_tweets(tweets: pd.DataFrame) -> pd.DataFrame:
    return tweets[tweets['content'].str.len()>15][['tweet_id']]
~~~
