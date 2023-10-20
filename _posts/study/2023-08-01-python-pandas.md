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

~~~python
import pandas as pd

def find_products(products: pd.DataFrame) -> pd.DataFrame:
    df = products[(products['low_fats']=='Y') & (products['recyclable']=='Y')]
    return df[['product_id']]
~~~

## Data Filtering - Customers Who Never Order
Write a solution to find all customers who never order anything.

Return the result table in any order.

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

~~~python
import pandas as pd

def article_views(views: pd.DataFrame) -> pd.DataFrame:
    df = views[views['viewer_id']==views['author_id']][['viewer_id']]
    df.rename(columns={'viewer_id':'id'}, inplace=True)
    df = pd.DataFrame(df['id'].unique(), columns=['id']).sort_values(by='id', ascending=True)
    return df
~~~

## String Methods - Invalid Tweets

Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15.

Return the result table in any order.

~~~python
import pandas as pd

def invalid_tweets(tweets: pd.DataFrame) -> pd.DataFrame:
    return tweets[tweets['content'].str.len()>15][['tweet_id']]
~~~

## String Methods - Calculate Special Bonus

Write a solution to calculate the bonus of each employee. The bonus of an employee is 100% of their salary if the ID of the employee is an odd number and the employee's name does not start with the character 'M'. The bonus of an employee is 0 otherwise.

Return the result table ordered by employee_id.

~~~python
import pandas as pd

def calculate_special_bonus(employees: pd.DataFrame) -> pd.DataFrame:
    employees['bonus'] = employees[(employees['employee_id']%2==1) & (~employees['name'].str.startswith('M'))][['salary']]
    employees['bonus'] = employees['bonus'].fillna(0)
    return employees[['employee_id', 'bonus']].sort_values(by='employee_id')    
~~~

## String Methods - Fix Names in a Table

Write a solution to fix the names so that only the first character is uppercase and the rest are lowercase.

Return the result table ordered by user_id.

~~~python
import pandas as pd

def fix_names(users: pd.DataFrame) -> pd.DataFrame:
    users['name'] = users['name'].str.upper().str[0] + users['name'].str.lower().str[1:]
    return users.sort_values(by='user_id')
~~~

## String Methods - Find Users With Valid E-Mails

Write a solution to find the users who have valid emails.

A valid e-mail has a prefix name and a domain where:

The prefix name is a string that may contain letters (upper or lower case), digits, underscore '_', period '.', and/or dash '-'. The prefix name must start with a letter.
The domain is '@leetcode.com'.
Return the result table in any order.

~~~python
import pandas as pd

def valid_emails(users: pd.DataFrame) -> pd.DataFrame:
    regexp = "^[a-zA-Z][a-zA-Z\d_.-]*@leetcode\.com"
    df = users[users['mail'].str.match(regexp)]
    return df
~~~

## String Methods - Patients With a Condition

Write a solution to find the patient_id, patient_name, and conditions of the patients who have Type I Diabetes. Type I Diabetes always starts with DIAB1 prefix.

Return the result table in any order.

~~~python
import pandas as pd

def find_diabetes(conditions) :
    for con in conditions.split(' '):
        if con.startswith('DIAB1'):
            return True
    return False

def find_patients(patients: pd.DataFrame) -> pd.DataFrame:
    patients = patients[patients['conditions'].apply(find_diabetes)]
    return patients
~~~

## Data Manipulation - Delete Duplicate Emails

Write a solution to delete all duplicate emails, keeping only one unique email with the smallest id.

For Pandas users, please note that you are supposed to modify Person in place.

After running your script, the answer shown is the Person table. The driver will first compile and run your piece of code and then show the Person table. The final order of the Person table does not matter.

~~~python
import pandas as pd

# Modify Person in place
def delete_duplicate_emails(person: pd.DataFrame) -> None:
    person.sort_values(by=['id'], ascending=True, inplace=True)
    person.drop_duplicates(subset='email', keep='first', inplace=True)
~~~    

## Data Manipulation - Rearrange Products Table

Write a solution to rearrange the Products table so that each row has (product_id, store, price). If a product is not available in a store, do not include a row with that product_id and store combination in the result table.

Return the result table in any order.

~~~python
import pandas as pd

def rearrange_products_table(products: pd.DataFrame) -> pd.DataFrame:
    melted_of = products.melt(id_vars='product_id', var_name='store', value_name='price')
    melted_of = melted_of.dropna()
    return melted_of
~~~

## Statistics - The Number of Rich Customers

Write a solution to report the number of customers who had at least one bill with an amount strictly greater than 500.

The result format is in the following example.

~~~python
import pandas as pd

def count_rich_customers(store: pd.DataFrame) -> pd.DataFrame:
    rich_customers = store[store['amount'] > 500]
    num_rich_customers = rich_customers['customer_id'].nunique()
    df = pd.DataFrame({'rich_count' : [num_rich_customers]})
    return df
~~~

## Statistics - Immediate Food Delivery I

If the customer's preferred delivery date is the same as the order date, then the order is called immediate; otherwise, it is called scheduled.

Write a solution to find the percentage of immediate orders in the table, rounded to 2 decimal places.

~~~python
import pandas as pd

def food_delivery(delivery: pd.DataFrame) -> pd.DataFrame:
    imm_count = delivery[delivery['order_date']==delivery['customer_pref_delivery_date']].shape[0]
    total_orders = delivery.shape[0]
    imm_percentage = (imm_count / total_orders) * 100
    df = pd.DataFrame({'immediate_percentage':[round(imm_percentage, 2)]})
    return df
~~~

## Data Aggregation - Find Total Time Spent by Each Employee

Write a solution to calculate the total time in minutes spent by each employee on each day at the office. Note that within one day, an employee can enter and leave more than once. The time spent in the office for a single entry is out_time - in_time.

Return the result table in any order.

~~~python
import pandas as pd

def total_time(employees: pd.DataFrame) -> pd.DataFrame:
    df = employees.groupby(['emp_id', 'event_day']).sum().reset_index()
    df['total_time'] = df['out_time'] - df['in_time']
    df.rename(columns={"event_day": "day", "emp_id":"emp_id", "total_time":"total_time"}, inplace=True)
    df.drop(['in_time', 'out_time'], axis=1, inplace=True)

    return df
~~~

## Data Aggregation - Game Play Analysis I

Write a solution to find the first login date for each player.

Return the result table in any order.

~~~python
import pandas as pd

def game_analysis(activity: pd.DataFrame) -> pd.DataFrame:
    df = activity.groupby(['player_id']).min().reset_index()
    df.rename(columns={'player_id':'player_id', 'event_date':'first_login'}, inplace=True)
    df.drop(['device_id', 'games_played'], axis=1, inplace=True)
    return df
    
~~~

## Data Aggregation - Number of Unique Subjects Taught by Each Teacher

Write a solution to calculate the number of unique subjects each teacher teaches in the university.

Return the result table in any order.

~~~python
import pandas as pd

def count_unique_subjects(teacher: pd.DataFrame) -> pd.DataFrame:
    df = teacher.groupby(['teacher_id']).nunique('subject_id').reset_index()
    df.rename(columns={'teacher_id':'teacher_id', 'subject_id':'cnt'}, inplace=True)
    df.drop(['dept_id'], axis=1, inplace=True)
    return df
    
~~~

## Data Aggregation - Classes More Than 5 Students

Write a solution to find all the classes that have at least five students.

Return the result table in any order.

~~~python
import pandas as pd

def find_classes(courses: pd.DataFrame) -> pd.DataFrame:
    df = courses.groupby('class').count().reset_index()
    df = df[df['student'] >= 5]
    df.drop(['student'], axis=1, inplace=True)
    return df
~~~

## Data Aggregation - Customer Placing the Largest Number of Orders

Write a solution to find the customer_number for the customer who has placed the largest number of orders.

The test cases are generated so that exactly one customer will have placed more orders than any other customer.

~~~python
import pandas as pd

def largest_orders(orders: pd.DataFrame) -> pd.DataFrame:
    df = orders.groupby('customer_number').count().reset_index()
    df = df[df['order_number']==df['order_number'].max()]
    df.drop(['order_number'], axis=1, inplace=True)
    return df
    
~~~

## Data Aggregation - Group Sold Products By The Date

Write a solution to find for each date the number of different products sold and their names.

The sold products names for each date should be sorted lexicographically.

Return the result table ordered by sell_date.

~~~python
import pandas as pd

def categorize_products(activities: pd.DataFrame) -> pd.DataFrame:
    df = activities.groupby(['sell_date'])['product'].agg([('num_sold', 'nunique'), ('products', lambda x: ','.join(sorted(x.unique())))]).reset_index()
    return df
    
~~~

## Data Aggregation - Daily Leads and Partners

For each date_id and make_name, find the number of distinct lead_id's and distinct partner_id's.

Return the result table in any order.

~~~python
import pandas as pd

def daily_leads_and_partners(daily_sales: pd.DataFrame) -> pd.DataFrame:
    df = daily_sales.groupby(['date_id', 'make_name']).nunique().reset_index()
    df.rename(columns={'date_id':'date_id', 'make_name':'make_name', 'lead_id':'unique_leads','partner_id':'unique_partners'}, inplace=True)
    return df
~~~

## Data Integration - Actors and Directors Who Cooperated At Least Three Times

Write a solution to find all the pairs (actor_id, director_id) where the actor has cooperated with the director at least three times.

Return the result table in any order.

~~~python
import pandas as pd

def actors_and_directors(actor_director: pd.DataFrame) -> pd.DataFrame:
    df = actor_director.groupby(['actor_id', 'director_id']).count().reset_index()
    df = df[df['timestamp']>=3]
    df.drop('timestamp', axis=1, inplace=True)
    return df
    
~~~

## Data Integration - Replace Employee ID With The Unique Identifier

Write a solution to show the unique ID of each user, If a user does not have a unique ID replace just show null.

Return the result table in any order.

~~~python
import pandas as pd

def replace_employee_id(employees: pd.DataFrame, employee_uni: pd.DataFrame) -> pd.DataFrame:
    df = employee_uni.merge(employees, how='right', on='id')
    df.drop('id', axis=1, inplace=True)
    return df
~~~

## Data Integration - Students and Examinations

Write a solution to find the number of times each student attended each exam.

Return the result table ordered by student_id and subject_name.

~~~python
import pandas as pd

def students_and_examinations(students: pd.DataFrame, subjects: pd.DataFrame, examinations: pd.DataFrame) -> pd.DataFrame:
    df = students.merge(subjects, how="cross")
    exam = examinations.groupby(["student_id", "subject_name"]).agg(attended_exams=("subject_name", "count")).reset_index()
    x = df.merge(exam, on=["student_id", "subject_name"],how="left").sort_values(by=["student_id", "subject_name"])
    return x.fillna(0)[['student_id', 'student_name', 'subject_name', 'attended_exams']]
    
~~~
