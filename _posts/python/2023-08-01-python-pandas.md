---
layout: post
title: LeetCode - Pandas
categories: python
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Pandas

#### 595. Data Filtering - Big Countries
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

#### 1757. Data Filtering - Recyclable and Low Fat Products
Write a solution to find the ids of products that are both low fat and recyclable.

Return the result table in any order.

~~~python
import pandas as pd

def find_products(products: pd.DataFrame) -> pd.DataFrame:
    df = products[(products['low_fats']=='Y') & (products['recyclable']=='Y')]
    return df[['product_id']]
~~~

#### 183. Data Filtering - Customers Who Never Order
Write a solution to find all customers who never order anything.

Return the result table in any order.

~~~python
import pandas as pd

def find_customers(customers: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    df = customers[~customers['id'].isin(orders['customerId'])][['name']]
    df = df.rename(columns={"name": "Customers"})
    return df
~~~

#### 1148. Data Filtering - Article Views I
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

#### 1683. String Methods - Invalid Tweets

Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15.

Return the result table in any order.

~~~python
import pandas as pd

def invalid_tweets(tweets: pd.DataFrame) -> pd.DataFrame:
    return tweets[tweets['content'].str.len()>15][['tweet_id']]
~~~

#### 1873. String Methods - Calculate Special Bonus

Write a solution to calculate the bonus of each employee. The bonus of an employee is 100% of their salary if the ID of the employee is an odd number and the employee's name does not start with the character 'M'. The bonus of an employee is 0 otherwise.

Return the result table ordered by employee_id.

~~~python
import pandas as pd

def calculate_special_bonus(employees: pd.DataFrame) -> pd.DataFrame:
    employees['bonus'] = employees[(employees['employee_id']%2==1) & (~employees['name'].str.startswith('M'))][['salary']]
    employees['bonus'] = employees['bonus'].fillna(0)
    return employees[['employee_id', 'bonus']].sort_values(by='employee_id')    
~~~

#### 1667. String Methods - Fix Names in a Table

Write a solution to fix the names so that only the first character is uppercase and the rest are lowercase.

Return the result table ordered by user_id.

~~~python
import pandas as pd

def fix_names(users: pd.DataFrame) -> pd.DataFrame:
    users['name'] = users['name'].str.upper().str[0] + users['name'].str.lower().str[1:]
    return users.sort_values(by='user_id')
~~~

#### 1517. String Methods - Find Users With Valid E-Mails

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

#### 1527. ## String Methods - Patients With a Condition

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

#### 177. Data Manipulation - Nth Highest Salary

Write a solution to find the nth highest salary from the Employee table. If there is no nth highest salary, return null.

~~~python
import pandas as pd

def nth_highest_salary(employee: pd.DataFrame, N: int) -> pd.DataFrame:
    employee.drop_duplicates(subset='salary', inplace=True)
    
    df = employee.sort_values('salary', ascending=False)
    df.reset_index(inplace=True, drop=True)
    df = df.iloc[N-1:N][['salary']]

    colName = 'getNthHighestSalary(' + str(N) + ')'
    
    if df.empty:
        return pd.DataFrame({colName: [None]})
    
    df.rename(columns={'salary':colName}, inplace=True)
    return df

~~~

#### 176. Data Manipulation - Second Highest Salary

Write a solution to find the second highest salary from the Employee table. If there is no second highest salary, return null (return None in Pandas).

~~~python
import pandas as pd

def second_highest_salary(employee: pd.DataFrame) -> pd.DataFrame:
    employee.drop_duplicates(subset='salary', inplace=True)
    df = employee.sort_values('salary', ascending=False)
    df.reset_index(inplace=True, drop=True)
    df = df.iloc[1:2]

    if df.empty:
        return pd.DataFrame({'SecondHighestSalary':[None]})

    df.rename(columns={'salary':'SecondHighestSalary'}, inplace=True)
    return df[['SecondHighestSalary']]

~~~

#### 184. Data Manipulation -  Department Highest Salary

Write a solution to find employees who have the highest salary in each of the departments.

Return the result table in any order.

~~~python
import pandas as pd

def department_highest_salary(employee: pd.DataFrame, department: pd.DataFrame) -> pd.DataFrame:
    df = pd.merge(employee, department, left_on='departmentId', right_on='id')
    df.drop(['id_y'], axis=1, inplace=True)
    df.rename(columns={'id_x':'id', 'name_x':'Employee', 'salary':'Salary', 'name_y':'Department'}, inplace=True)
    df_max = employee.groupby(['departmentId'])['salary'].max().reset_index()
    df = pd.merge(df, df_max, on='departmentId')
    df = df[df['Salary']==df['salary']][['Department', 'Employee', 'Salary']]

    return df
~~~

#### 178. Data Manipulation -  Rank Scores

Write a solution to find the rank of the scores. The ranking should be calculated according to the following rules:

The scores should be ranked from the highest to the lowest.
If there is a tie between two scores, both should have the same ranking.
After a tie, the next ranking number should be the next consecutive integer value. In other words, there should be no holes between ranks.
Return the result table ordered by score in descending order.

~~~python
import pandas as pd

def order_scores(scores: pd.DataFrame) -> pd.DataFrame:
    df = scores.sort_values('score', ascending=False)
    df = df[['score']]
    df['rank'] = df['score'].rank(ascending=False, method='dense')
    return df
~~~

#### 196. Data Manipulation - Delete Duplicate Emails

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

#### 1795. Data Manipulation - Rearrange Products Table

Write a solution to rearrange the Products table so that each row has (product_id, store, price). If a product is not available in a store, do not include a row with that product_id and store combination in the result table.

Return the result table in any order.

~~~python
import pandas as pd

def rearrange_products_table(products: pd.DataFrame) -> pd.DataFrame:
    melted_of = products.melt(id_vars='product_id', var_name='store', value_name='price')
    melted_of = melted_of.dropna()
    return melted_of
~~~

#### 2082. Statistics - The Number of Rich Customers

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

#### 1173. Statistics - Immediate Food Delivery I

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

#### 1907. Statistics - Count Salary Categories

Write a solution to calculate the number of bank accounts for each salary category. The salary categories are:

- "Low Salary": All the salaries strictly less than $20000.
- "Average Salary": All the salaries in the inclusive range [$20000, $50000].
- "High Salary": All the salaries strictly greater than $50000.
- The result table must contain all three categories. If there are no accounts in a category, return 0.

Return the result table in any order.
~~~python
import pandas as pd

def count_salary_categories(accounts: pd.DataFrame) -> pd.DataFrame:
    lowCnt = accounts[accounts['income']<20000].shape[0]
    averageCnt = accounts[(accounts['income']>=20000) & (accounts['income']<=50000)].shape[0]
    highCnt = accounts[accounts['income']>50000].shape[0]
    df = pd.DataFrame({'category':['Low Salary', 'Average Salary', 'High Salary'], 
                        'accounts_count':[lowCnt, averageCnt, highCnt]})
    return df
~~~

#### 1741. Data Aggregation - Find Total Time Spent by Each Employee

Write a solution to calculate the total time in minutes spent by each employee on each day at the office. Note that within one day, an employee can enter and leave more than once. The time spent in the office for a single entry is out_time - in_time.

Return the result table in any order.

~~~python
import pandas as pd

def total_time(employees: pd.DataFrame) -> pd.DataFrame:
    employees['total_time'] = employees['out_time'] - employees['in_time']
    employees = employees[['event_day', 'emp_id', 'total_time']]
    df = employees.groupby(by=['event_day', 'emp_id']).sum()
    df = df.reset_index().rename(columns={'event_day':'day'})
    return df
~~~

#### 511. Data Aggregation - Game Play Analysis I

Write a solution to find the first login date for each player.

Return the result table in any order.

~~~python
import pandas as pd

def game_analysis(activity: pd.DataFrame) -> pd.DataFrame:
    df = activity.sort_values(by=['player_id', 'event_date'])
    df = df.groupby(by=['player_id'])['event_date'].min().to_frame().reset_index()
    df.rename(columns={'event_date':'first_login'}, inplace=True)
    return df
    
~~~

#### 2356. Data Aggregation - Number of Unique Subjects Taught by Each Teacher

Write a solution to calculate the number of unique subjects each teacher teaches in the university.

Return the result table in any order.

~~~python
import pandas as pd

def count_unique_subjects(teacher: pd.DataFrame) -> pd.DataFrame:
    df = teacher.groupby(by=['teacher_id'])['subject_id'].nunique()
    df = df.to_frame().reset_index()
    df.rename(columns={'subject_id':'cnt'}, inplace=True)
    return df
~~~

#### 596. Data Aggregation - Classes More Than 5 Students

Write a solution to find all the classes that have at least five students.

Return the result table in any order.

~~~python
import pandas as pd

def find_classes(courses: pd.DataFrame) -> pd.DataFrame:
    df = courses.groupby(['class']).count().reset_index()
    return df[df['student']>=5][['class']]
~~~

#### 586. Data Aggregation - Customer Placing the Largest Number of Orders

Write a solution to find the customer_number for the customer who has placed the largest number of orders.

The test cases are generated so that exactly one customer will have placed more orders than any other customer.

~~~python
import pandas as pd

def largest_orders(orders: pd.DataFrame) -> pd.DataFrame:
    df = orders.groupby(['customer_number']).count().reset_index()
    return df[df['order_number']==df['order_number'].max()][['customer_number']]
~~~

#### 1484. Data Aggregation - Group Sold Products By The Date

Write a solution to find for each date the number of different products sold and their names.

The sold products names for each date should be sorted lexicographically.

Return the result table ordered by sell_date.

~~~python
import pandas as pd

def categorize_products(activities: pd.DataFrame) -> pd.DataFrame:
    by_sell_date = activities.groupby('sell_date')
    df = by_sell_date.agg(num_sold=('product', 'nunique'), 
    products=('product', lambda x : ','.join(sorted(set(x))))).reset_index()
    return df
~~~

#### 1693. Data Aggregation - Daily Leads and Partners

For each date_id and make_name, find the number of distinct lead_id's and distinct partner_id's.

Return the result table in any order.

~~~python
import pandas as pd

def daily_leads_and_partners(daily_sales: pd.DataFrame) -> pd.DataFrame:
    byDate = daily_sales.groupby(['date_id', 'make_name'])
    df = byDate.agg(unique_leads=('lead_id', 'nunique'), unique_partners=('partner_id', 'nunique')).reset_index()
    df = df.sort_values(['make_name'], ascending=False)
    return df    
~~~

#### 1050. Data Integration - Actors and Directors Who Cooperated At Least Three Times

Write a solution to find all the pairs (actor_id, director_id) where the actor has cooperated with the director at least three times.

Return the result table in any order.

~~~python
import pandas as pd

def actors_and_directors(actor_director: pd.DataFrame) -> pd.DataFrame:
    by_ad = actor_director.groupby(['actor_id', 'director_id']).count().reset_index()
    return by_ad[by_ad['timestamp']>=3][['actor_id', 'director_id']]    
~~~

#### 1378. Data Integration - Replace Employee ID With The Unique Identifier

Write a solution to show the unique ID of each user, If a user does not have a unique ID replace just show null.

Return the result table in any order.

~~~python
import pandas as pd

def replace_employee_id(employees: pd.DataFrame, employee_uni: pd.DataFrame) -> pd.DataFrame:
    df = pd.merge(employees, employee_uni, on='id', how='left')
    return df[['unique_id', 'name']]
~~~

#### 1280. Data Integration - Students and Examinations

Write a solution to find the number of times each student attended each exam.

Return the result table ordered by student_id and subject_name.

~~~python
import pandas as pd

def students_and_examinations(students: pd.DataFrame, subjects: pd.DataFrame, examinations: pd.DataFrame) -> pd.DataFrame:
    df = students.merge(subjects, how='cross')
    exam = examinations.groupby(['student_id', 'subject_name']).agg(attended_exams=('subject_name', 'count')).reset_index()
    df = df.merge(exam, on=['student_id', 'subject_name'], how='left').sort_values(by=['student_id', 'subject_name'], ascending=True)
    return df.fillna(0)[['student_id', 'student_name', 'subject_name', 'attended_exams']]
~~~

#### 570. Data Integration - Managers with at Least 5 Direct Reports

Write a solution to find managers with at least five direct reports.

Return the result table in any order.

~~~python
import pandas as pd

def find_managers(employee: pd.DataFrame) -> pd.DataFrame:
    byemp = employee.groupby('managerId')['name'].count().reset_index()
    emp = byemp[byemp['name']>=5]
    df = pd.merge(employee, emp, left_on='id', right_on='managerId')
    df = df[['name_x']]
    df.rename(columns={'name_x':'name'}, inplace=True)

    return df
~~~

#### 607. Data Integration - Sales Person

Write a solution to find the names of all the salespersons who did not have any orders related to the company with the name "RED".

Return the result table in any order.

~~~python
import pandas as pd

def sales_person(sales_person: pd.DataFrame, company: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    company_ids = 0
    company_id = company[company['name']=='RED'][['com_id']]
    if not company_id.empty :
        company_ids = company_id['com_id']
    sales_id = orders[orders['com_id']==int(company_ids)][['sales_id']]
    exclude_df = pd.merge(sales_id, sales_person, on='sales_id')
    df = sales_person[(~sales_person['sales_id'].isin(exclude_df['sales_id']))][['name']]
    return df
~~~

#### 610. Triangle Judgement
Report for every three line segments whether they can form a triangle.

~~~ python
import pandas as pd

def triangle_judgement(triangle: pd.DataFrame) -> pd.DataFrame:

    def tri(x,y,z):
        if x+y>z and x+z>y and y+z>x:
            return 'Yes'
        else:
            return 'No'

    print(triangle)
    triangle['triangle'] = triangle.apply(lambda row:tri(row['x'], row['y'], row['z']), axis=1)

    return triangle
~~~ 

#### 619. Biggest Single Number
A single number is a number that appeared only once in the MyNumbers table.

~~~ python
import pandas as pd

def biggest_single_number(my_numbers: pd.DataFrame) -> pd.DataFrame:
    return my_numbers.groupby(['num']).filter(lambda x: len(x)==1).max().to_frame(name='num')   
~~~ 