# yelp dataset worksheet

# Data Scientist Role Play: Profiling and Analyzing the Yelp Dataset Coursera Worksheet

This is a 2-part assignment. In the first part, you are asked a series of questions that will help you profile and understand the data just like a data scientist would. For this first part of the assignment, you will be assessed both on the correctness of your findings, as well as the code you used to arrive at your answer. You will be graded on how easy your code is to read, so remember to use proper formatting and comments where necessary.

In the second part of the assignment, you are asked to come up with your own inferences and analysis of the data for a particular research question you want to answer. You will be required to prepare the dataset for the analysis you choose to do. As with the first part, you will be graded, in part, on how easy your code is to read, so use proper formatting and comments to illustrate and communicate your intent as required.

For both parts of this assignment, use this "worksheet." It provides all the questions you are being asked, and your job will be to transfer your answers and SQL coding where indicated into this worksheet so that your peers can review your work. You should be able to use any Text Editor (Windows Notepad, Apple TextEdit, Notepad ++, Sublime Text, etc.) to copy and paste your answers. If you are going to use Word or some other page layout application, just be careful to make sure your answers and code are lined appropriately.
In this case, you may want to save as a PDF to ensure your formatting remains intact for you reviewer.

---

## Part 1: Yelp Dataset Profiling and Understanding

### Profile the data by finding the total number of records for each of the tables below:

i. Attribute table = 10000

```sql
SELECT COUNT(*)
FROM attribute;
+----------+
| COUNT(*) |
+----------+
|    10000 |
+----------+
```

ii. Business table = 10000

```sql
SELECT COUNT(*)
FROM business;
+----------+
| COUNT(*) |
+----------+
|    10000 |
+----------+
```

iii. Category table = 10000

```sql
SELECT COUNT(*)
FROM category;
+----------+
| COUNT(*) |
+----------+
|    10000 |
+----------+
```

iv. Checkin table = 10000 

```sql
SELECT COUNT(*)
FROM checkin;
+----------+
| COUNT(*) |
+----------+
|    10000 |
+----------+
```

v. elite_years table = 10000 

```sql
SELECT COUNT(*)
FROM elite_years;
+----------+
| COUNT(*) |
+----------+
|    10000 |
+----------+
```

vi. friend table = 10000 

```sql
SELECT COUNT(*)
FROM friend;
+----------+
| COUNT(*) |
+----------+
|    10000 |
+----------+
```

vii. hours table = 10000 

```sql
SELECT COUNT(*)
FROM friend;
+----------+
| COUNT(*) |
+----------+
|    10000 |
+----------+
```

viii. photo table =

```sql
SELECT COUNT(*)
FROM photo;
+----------+
| COUNT(*) |
+----------+
|    10000 |
+----------+
```

ix. review table =

```sql
SELECT COUNT(*)
FROM review;
+----------+
| COUNT(*) |
+----------+
|    10000 |
+----------+
```

x. tip table =

```sql
SELECT COUNT(*)
FROM tip;
+----------+
| COUNT(*) |
+----------+
|    10000 |
+----------+
```

xi. user table =

```sql
SELECT COUNT(*)
FROM user;
+----------+
| COUNT(*) |
+----------+
|    10000 |
+----------+
```

### Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key.

i. Business = 10000 

primary key `id`

foreign key/s `none`

```sql
PRAGMA table_info('business'); -- list out table info including pk
+-----+--------------+--------------+---------+------------+----+
| cid | name         | type         | notnull | dflt_value | pk |
+-----+--------------+--------------+---------+------------+----+
|   0 | id           | varchar(22)  |       1 |       None |  1 |
|   1 | name         | varchar(255) |       0 |       NULL |  0 |
|   2 | neighborhood | varchar(255) |       0 |       NULL |  0 |
|   3 | address      | varchar(255) |       0 |       NULL |  0 |
|   4 | city         | varchar(255) |       0 |       NULL |  0 |
|   5 | state        | varchar(255) |       0 |       NULL |  0 |
|   6 | postal_code  | varchar(255) |       0 |       NULL |  0 |
|   7 | latitude     | float        |       0 |       NULL |  0 |
|   8 | longitude    | float        |       0 |       NULL |  0 |
|   9 | stars        | float        |       0 |       NULL |  0 |
|  10 | review_count | integer      |       0 |       NULL |  0 |
|  11 | is_open      | integer      |       0 |       NULL |  0 |
+-----+--------------+--------------+---------+------------+----+

SELECT COUNT(DISTINCT(id))
FROM Business;
+---------------------+
| COUNT(DISTINCT(id)) |
+---------------------+
|               10000 |
+---------------------+
```

ii. Hours = 1562 

primary key `none`

foreign key/s `business_id`

```sql
PRAGMA table_info('hours'); -- list out table info including pk
+-----+-------------+--------------+---------+------------+----+
| cid | name        | type         | notnull | dflt_value | pk |
+-----+-------------+--------------+---------+------------+----+
|   0 | hours       | varchar(255) |       0 | NULL       |  0 |
|   1 | business_id | varchar(22)  |       1 | None       |  0 |
+-----+-------------+--------------+---------+------------+----+

PRAGMA foreign_key_list('hours'); -- list foreign keys
+----+-----+----------+-------------+----+-----------+-----------+-------+
| id | seq | table    | from        | to | on_update | on_delete | match |
+----+-----+----------+-------------+----+-----------+-----------+-------+
|  0 |   0 | business | business_id | id | NO ACTION | NO ACTION | NONE  |
+----+-----+----------+-------------+----+-----------+-----------+-------+

SELECT COUNT(DISTINCT(business_id))
FROM hours;
+------------------------------+
| COUNT(DISTINCT(business_id)) |
+------------------------------+
|                         1562 |
+------------------------------+
```

iii. Category = 2643 

primary key `none`

foreign key/s `business_id`

```sql
PRAGMA table_info('category'); -- list out table info including pk
+-----+-------------+--------------+---------+------------+----+
| cid | name        | type         | notnull | dflt_value | pk |
+-----+-------------+--------------+---------+------------+----+
|   0 | business_id | varchar(22)  |       1 |       None |  0 |
|   1 | category    | varchar(255) |       0 |       NULL |  0 |
+-----+-------------+--------------+---------+------------+----+

PRAGMA foreign_key_list('hours'); -- list foreign keys
+----+-----+----------+-------------+----+-----------+-----------+-------+
| id | seq | table    | from        | to | on_update | on_delete | match |
+----+-----+----------+-------------+----+-----------+-----------+-------+
|  0 |   0 | business | business_id | id | NO ACTION | NO ACTION | NONE  |
+----+-----+----------+-------------+----+-----------+-----------+-------+

SELECT COUNT(DISTINCT(business_id))
FROM category;
+------------------------------+
| COUNT(DISTINCT(business_id)) |
+------------------------------+
|                         2643 |
+------------------------------+
```

iv. Attribute = 1115 

primary key `none`

foreign key/s `business_id`

```sql
PRAGMA table_info('attribute'); -- list out table info including pk
+-----+-------------+--------------+---------+------------+----+
| cid | name        | type         | notnull | dflt_value | pk |
+-----+-------------+--------------+---------+------------+----+
|   0 | business_id | varchar(22)  |       1 |       None |  0 |
|   1 | name        | varchar(255) |       0 |       NULL |  0 |
|   2 | value       | text         |       0 |       None |  0 |
+-----+-------------+--------------+---------+------------+----+
PRAGMA foreign_key_list('attribute'); -- list foreign keys
+----+-----+----------+-------------+----+-----------+-----------+-------+
| id | seq | table    | from        | to | on_update | on_delete | match |
+----+-----+----------+-------------+----+-----------+-----------+-------+
|  0 |   0 | business | business_id | id | NO ACTION | NO ACTION | NONE  |
+----+-----+----------+-------------+----+-----------+-----------+-------+

SELECT COUNT(DISTINCT(business_id))
FROM category;
+------------------------------+
| COUNT(DISTINCT(business_id)) |
+------------------------------+
|                         1115 |
+------------------------------+

```

v. Review = 10000

primary key `id`

foreign key/s `user_id | business_id`

```sql
PRAGMA table_info('review'); -- list out table info including pk
+-----+-------------+-------------+---------+------------+----+
| cid | name        | type        | notnull | dflt_value | pk |
+-----+-------------+-------------+---------+------------+----+
|   0 | id          | varchar(22) |       1 |       None |  1 |
|   1 | stars       | integer     |       0 |       NULL |  0 |
|   2 | date        | datetime    |       0 |       NULL |  0 |
|   3 | text        | text        |       0 |       None |  0 |
|   4 | useful      | integer     |       0 |       NULL |  0 |
|   5 | funny       | integer     |       0 |       NULL |  0 |
|   6 | cool        | integer     |       0 |       NULL |  0 |
|   7 | business_id | varchar(22) |       1 |       None |  0 |
|   8 | user_id     | varchar(22) |       1 |       None |  0 |
+-----+-------------+-------------+---------+------------+----+
PRAGMA foreign_key_list('review'); -- list foreign keys
+----+-----+----------+-------------+----+-----------+-----------+-------+
| id | seq | table    | from        | to | on_update | on_delete | match |
+----+-----+----------+-------------+----+-----------+-----------+-------+
|  0 |   0 | user     | user_id     | id | NO ACTION | NO ACTION | NONE  |
|  1 |   0 | business | business_id | id | NO ACTION | NO ACTION | NONE  |
+----+-----+----------+-------------+----+-----------+-----------+-------+

SELECT COUNT(DISTINCT(id))
FROM review;
+---------------------+
| COUNT(DISTINCT(id)) |
+---------------------+
|               10000 |
+---------------------+
```

vi. Checkin = 493 

primary key `none`

foreign key/s `business_id`

```sql
PRAGMA table_info('checkin'); -- list out table info including pk
+-----+-------------+--------------+---------+------------+----+
| cid | name        | type         | notnull | dflt_value | pk |
+-----+-------------+--------------+---------+------------+----+
|   0 | business_id | varchar(22)  |       1 |       None |  0 |
|   1 | date        | varchar(255) |       0 |       NULL |  0 |
|   2 | count       | integer      |       0 |       NULL |  0 |
+-----+-------------+--------------+---------+------------+----+
PRAGMA foreign_key_list('checkin'); -- list foreign keys
+----+-----+----------+-------------+----+-----------+-----------+-------+
| id | seq | table    | from        | to | on_update | on_delete | match |
+----+-----+----------+-------------+----+-----------+-----------+-------+
|  0 |   0 | business | business_id | id | NO ACTION | NO ACTION | NONE  |
+----+-----+----------+-------------+----+-----------+-----------+-------+

SELECT COUNT(DISTINCT(business_id))
FROM checkin;
+------------------------------+
| COUNT(DISTINCT(business_id)) |
+------------------------------+
|                          493 |
+------------------------------+
```

vii. Photo = 10000 

primary key `id`

foreign key/s `business_id`

```sql
PRAGMA table_info('photo'); -- list out table info including pk
+-----+-------------+--------------+---------+------------+----+
| cid | name        | type         | notnull | dflt_value | pk |
+-----+-------------+--------------+---------+------------+----+
|   0 | id          | varchar(22)  |       1 |       None |  1 |
|   1 | business_id | varchar(22)  |       1 |       None |  0 |
|   2 | caption     | varchar(255) |       0 |       NULL |  0 |
|   3 | label       | varchar(255) |       0 |       NULL |  0 |
+-----+-------------+--------------+---------+------------+----+
PRAGMA foreign_key_list('photo'); -- list foreign keys
+----+-----+----------+-------------+----+-----------+-----------+-------+
| id | seq | table    | from        | to | on_update | on_delete | match |
+----+-----+----------+-------------+----+-----------+-----------+-------+
|  0 |   0 | business | business_id | id | NO ACTION | NO ACTION | NONE  |
+----+-----+----------+-------------+----+-----------+-----------+-------+

SELECT COUNT(DISTINCT(id))
FROM photo;
+---------------------+
| COUNT(DISTINCT(id)) |
+---------------------+
|               10000 |
+---------------------+
```

viii. Tip = user_id (537) | business_id (3979)
primary key `none`

foreign key/s `user_id | business_id`

```sql
PRAGMA table_info('tip'); -- list out table info including pk
+-----+-------------+-------------+---------+------------+----+
| cid | name        | type        | notnull | dflt_value | pk |
+-----+-------------+-------------+---------+------------+----+
|   0 | user_id     | varchar(22) |       1 |       None |  0 |
|   1 | business_id | varchar(22) |       1 |       None |  0 |
|   2 | text        | text        |       0 |       None |  0 |
|   3 | date        | datetime    |       0 |       NULL |  0 |
|   4 | likes       | integer     |       0 |       NULL |  0 |
+-----+-------------+-------------+---------+------------+----+
PRAGMA foreign_key_list('tip'); -- list foreign keys
+----+-----+----------+-------------+----+-----------+-----------+-------+
| id | seq | table    | from        | to | on_update | on_delete | match |
+----+-----+----------+-------------+----+-----------+-----------+-------+
|  0 |   0 | user     | user_id     | id | NO ACTION | NO ACTION | NONE  |
|  1 |   0 | business | business_id | id | NO ACTION | NO ACTION | NONE  |
+----+-----+----------+-------------+----+-----------+-----------+-------+

SELECT 
COUNT(DISTINCT(user_id)),
COUNT(DISTINCT(business_id))
FROM tip;
+--------------------------+------------------------------+
| COUNT(DISTINCT(user_id)) | COUNT(DISTINCT(business_id)) |
+--------------------------+------------------------------+
|                      537 |                         3979 |
+--------------------------+------------------------------+
```

ix. User = 10000

primary key `id`

foreign key/s `none`

```sql
PRAGMA table_info('user'); -- list out table info including pk
+-----+--------------------+--------------+---------+------------+----+
| cid | name               | type         | notnull | dflt_value | pk |
+-----+--------------------+--------------+---------+------------+----+
|   0 | id                 | varchar(22)  |       1 |       None |  1 |
|   1 | name               | varchar(255) |       0 |       NULL |  0 |
|   2 | review_count       | integer      |       0 |       NULL |  0 |
|   3 | yelping_since      | datetime     |       0 |       NULL |  0 |
|   4 | useful             | integer      |       0 |       NULL |  0 |
|   5 | funny              | integer      |       0 |       NULL |  0 |
|   6 | cool               | integer      |       0 |       NULL |  0 |
|   7 | fans               | integer      |       0 |       NULL |  0 |
|   8 | average_stars      | float        |       0 |       NULL |  0 |
|   9 | compliment_hot     | integer      |       0 |       NULL |  0 |
|  10 | compliment_more    | integer      |       0 |       NULL |  0 |
|  11 | compliment_profile | integer      |       0 |       NULL |  0 |
|  12 | compliment_cute    | integer      |       0 |       NULL |  0 |
|  13 | compliment_list    | integer      |       0 |       NULL |  0 |
|  14 | compliment_note    | integer      |       0 |       NULL |  0 |
|  15 | compliment_plain   | integer      |       0 |       NULL |  0 |
|  16 | compliment_cool    | integer      |       0 |       NULL |  0 |
|  17 | compliment_funny   | integer      |       0 |       NULL |  0 |
|  18 | compliment_writer  | integer      |       0 |       NULL |  0 |
|  19 | compliment_photos  | integer      |       0 |       NULL |  0 |
+-----+--------------------+--------------+---------+------------+----+

SELECT COUNT(DISTINCT(id))
FROM user;
+---------------------+
| COUNT(DISTINCT(id)) |
+---------------------+
|               10000 |
+---------------------+

```

x. Friend = 11 

primary key `none`

foreign key/s `user_id`

```sql
PRAGMA table_info('friend'); -- list out table info including pk
+-----+-----------+-------------+---------+------------+----+
| cid | name      | type        | notnull | dflt_value | pk |
+-----+-----------+-------------+---------+------------+----+
|   0 | user_id   | varchar(22) |       1 |       None |  0 |
|   1 | friend_id | varchar(22) |       0 |       NULL |  0 |
+-----+-----------+-------------+---------+------------+----+
PRAGMA foreign_key_list('friend'); -- list foreign keys
+----+-----+-------+---------+----+-----------+-----------+-------+
| id | seq | table | from    | to | on_update | on_delete | match |
+----+-----+-------+---------+----+-----------+-----------+-------+
|  0 |   0 | user  | user_id | id | NO ACTION | NO ACTION | NONE  |
+----+-----+-------+---------+----+-----------+-----------+-------+

SELECT COUNT(DISTINCT(user_id))
FROM friend;
+--------------------------+
| COUNT(DISTINCT(user_id)) |
+--------------------------+
|                       11 |
+--------------------------+
```

xi. Elite_years = 2780 

primary key `none`

foreign key/s `user_id`

```sql
PRAGMA table_info('elite_years'); -- list out table info including pk
+-----+---------+-------------+---------+------------+----+
| cid | name    | type        | notnull | dflt_value | pk |
+-----+---------+-------------+---------+------------+----+
|   0 | user_id | varchar(22) |       1 |       None |  0 |
|   1 | year    | char(4)     |       0 |       NULL |  0 |
+-----+---------+-------------+---------+------------+----+
PRAGMA foreign_key_list('elite_years'); -- list foreign keys
+----+-----+-------+---------+----+-----------+-----------+-------+
| id | seq | table | from    | to | on_update | on_delete | match |
+----+-----+-------+---------+----+-----------+-----------+-------+
|  0 |   0 | user  | user_id | id | NO ACTION | NO ACTION | NONE  |
+----+-----+-------+---------+----+-----------+-----------+-------+

SELECT COUNT(DISTINCT(user_id))
FROM elite_years;
+--------------------------+
| COUNT(DISTINCT(user_id)) |
+--------------------------+
|                     2780 |
+--------------------------+
```

Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.

1. Are there any columns with null values in the Users table? Indicate "yes," or "no."
    
    Answer: no
    
    SQL code used to arrive at answer:
    
    ```sql
    SELECT COUNT(*)
    FROM user
    WHERE 
    id || name || review_count || yelping_since || useful || funny || cool || fans || average_stars || compliment_hot || compliment_more || compliment_profile || compliment_cute || compliment_list || compliment_note || compliment_plain || compliment_cool || compliment_funny || compliment_writer || compliment_photos IS NULL; -- check every column for NULL
    
    +----------+
    | COUNT(*) |
    +----------+
    |        0 |
    +----------+
    ```
    
2. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:
    
    i. Table: Review, Column: Stars
    
    ```
     min: 1		max:	5	avg: 3.7082
    
    ```
    
    ii. Table: Business, Column: Stars
    
    ```
     min:	1.0	max:	5.0	avg: 3.6549
    
    ```
    
    iii. Table: Tip, Column: Likes
    
    ```
     min:	0	max:	2	avg:0.0144
    
    ```
    
    iv. Table: Checkin, Column: Count
    
    ```
     min:	1	max:	53	avg: 1.9414
    
    ```
    
    v. Table: User, Column: Review_count
    
    ```
     min:	0	max:	2000	avg: 24.2995
    
    ```
    
3. List the cities with the most reviews in descending order:
    
    SQL code used to arrive at answer:
    
    ```sql
    SELECT b.city 
    ,COUNT(r.id) AS reviews
    FROM business b -- declare business as b
    JOIN review r ON r.business_id = b.id -- declare review as r. join review and business on business_id fk
    GROUP BY b.city
    ORDER BY reviews DESC;
    ```
    
    Copy and Paste the Result Below:
    
    ```sql
    +-----------------+---------+
    | city            | reviews |
    +-----------------+---------+
    | Las Vegas       |     193 |
    | Phoenix         |      65 |
    | Toronto         |      51 |
    | Scottsdale      |      37 |
    | Henderson       |      30 |
    | Tempe           |      28 |
    | Pittsburgh      |      23 |
    | Chandler        |      22 |
    | Charlotte       |      21 |
    | Montréal        |      18 |
    | Madison         |      16 |
    | Gilbert         |      13 |
    | Mesa            |      13 |
    | Cleveland       |      12 |
    | North Las Vegas |       6 |
    | Edinburgh       |       5 |
    | Glendale        |       5 |
    | Lakewood        |       5 |
    | Cave Creek      |       4 |
    | Champaign       |       4 |
    | Markham         |       4 |
    | North York      |       4 |
    | Mississauga     |       3 |
    | Surprise        |       3 |
    | Avondale        |       2 |
    +-----------------+---------+
    (Output limit exceeded, 25 of 67 total rows shown)
    ```
    
4. Find the distribution of star ratings to the business in the following cities:
    
    i. Avon
    
    SQL code used to arrive at answer:
    
    ```sql
    SELECT stars AS star_rating, COUNT(stars) AS count -- formatting
    FROM business
    WHERE city LIKE 'Avon' -- LIKE tends to give more consitent results than '='
    GROUP BY star_rating;
    ```
    
    Copy and Paste the Resulting Table Below (2 columns – star rating and count):
    
    ```sql
    +-------------+-------+
    | star_rating | count |
    +-------------+-------+
    |         1.5 |     1 |
    |         2.5 |     2 |
    |         3.5 |     3 |
    |         4.0 |     2 |
    |         4.5 |     1 |
    |         5.0 |     1 |
    +-------------+-------+
    ```
    
    ii. Beachwood
    
    SQL code used to arrive at answer:
    
    ```sql
    SELECT stars AS star_rating, COUNT(stars) AS count
    FROM business
    WHERE city LIKE 'Beachwood'
    GROUP BY star_rating;
    ```
    
    Copy and Paste the Resulting Table Below (2 columns – star rating and count):
    
    ```sql
    +-------------+-------+
    | star_rating | count |
    +-------------+-------+
    |         2.0 |     1 |
    |         2.5 |     1 |
    |         3.0 |     2 |
    |         3.5 |     2 |
    |         4.0 |     1 |
    |         4.5 |     2 |
    |         5.0 |     5 |
    +-------------+-------+
    ```
    
5. Find the top 3 users based on their total number of reviews:
    
    SQL code used to arrive at answer:
    
    ```sql
    SELECT id -- probably dont need id column but gives a good basis for GROUP BY
    ,name
    ,review_count
    FROM user
    GROUP BY id
    ORDER BY review_count DESC
    LIMIT 3;
    ```
    
    Copy and Paste the Result Below:
    
    ```sql
    +------------------------+--------+--------------+
    | id                     | name   | review_count |
    +------------------------+--------+--------------+
    | -G7Zkl1wIWBBmD0KRy_sCw | Gerald |         2000 |
    | -3s52C4zL_DHRK0ULG6qtg | Sara   |         1629 |
    | -8lbUNlXVSoXqaRRiHiSNg | Yuri   |         1339 |
    +------------------------+--------+--------------+
    ```
    
6. Does posing more reviews correlate with more fans?
    
    Please explain your findings and interpretation of the results:
    
    - there seems to be a correlation between making more reviews and the number of fans
    
    *first is to split the users into demographics based on how many fans a user has.*
    
    *then calculate the average review count for each demographic.*
    
    *get the average fan count for each demographic for good measure.*
    
    ```sql
    SELECT
      CASE
        WHEN fans BETWEEN 0 AND 9 THEN '0 - 9'
        WHEN fans BETWEEN 10 AND 99 THEN '10 - 99'
        ELSE '>=100'
      END AS range,
      COUNT(*) AS users,
      AVG(review_count) AS avg_review_count,
      AVG(fans) AS avg_fan_count
      FROM user
    GROUP BY range;
    
    +---------+-------+------------------+----------------+
    | range   | users | avg_review_count |  avg_fan_count |
    +---------+-------+------------------+----------------+
    | 0 - 9   |  9690 |    15.0085655315 | 0.447265221878 |
    | 10 - 99 |   294 |    283.326530612 |  25.5986394558 |
    | >=100   |    16 |            891.5 |         189.75 |
    +---------+-------+------------------+----------------+
    ```
    
7. Are there more reviews with the word "love" or with the word "hate" in them?
    
    Answer: *******************more love than hate*******************
    
    ```sql
    +---------+-------+
    | reviews | count |
    +---------+-------+
    |    None |  8042 |
    |    hate |   178 |
    |    love |  1780 |
    +---------+-------+
    ```
    
    SQL code used to arrive at answer:
    
    ```sql
    SELECT CASE -- double conditional
    	WHEN LOWER(text) LIKE '%love%' THEN 'love' -- if search hits a love, then love 
    	WHEN LOWER(text) LIKE '%hate%' THEN 'hate' -- if search hits a hate, then hate
      ELSE NULL END AS reviews, -- NULL Condition
    COUNT(*) AS count -- count all reviews
    FROM review
    GROUP BY reviews; -- separate the loves from the hate counts
    ```
    
8. Find the top 10 users with the most fans:
    
    SQL code used to arrive at answer:
    
    ```sql
    SELECT name
    ,fans
    FROM user
    ORDER BY fans DESC
    LIMIT 10;
    ```
    
    Copy and Paste the Result Below:
    
    ```sql
    +-----------+------+
    | name      | fans |
    +-----------+------+
    | Amy       |  503 |
    | Mimi      |  497 |
    | Harald    |  311 |
    | Gerald    |  253 |
    | Christine |  173 |
    | Lisa      |  159 |
    | Cat       |  133 |
    | William   |  126 |
    | Fran      |  124 |
    | Lissa     |  120 |
    +-----------+------+
    ```
    

Part 2: Inferences and Analysis

1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. Compare the businesses with 2-3 stars to the businesses with 4-5 stars and answer the following questions. Include your code.

i. Do the two groups you chose to analyze have a different distribution of hours?

- the two groups seem to have different open hours

```sql
SELECT b.city
	,CASE -- split businesses into groups according to stars
		WHEN b.stars > 4.0 THEN '4-5 stars' WHEN b.stars > 3.0 THEN '3-4 stars' WHEN b.stars > 2.0 THEN '2-3 stars' ELSE 'below 2' END AS rating
	,COUNT(DISTINCT b.id) AS count -- count distinct businesses in cleveland
	,COUNT(h.hours) AS open_days_total -- count total days open of each business
	,COUNT(h.hours) / COUNT(DISTINCT b.id) AS open_days_avg -- averages the open days of the businesses
FROM Business b
INNER JOIN category c ON c.business_id = b.id
INNER JOIN hours h ON h.business_id = b.id
WHERE city LIKE 'Cleveland'
GROUP BY rating;-- split businesses into groups according to stars

+-----------+-----------+-------+-----------------+---------------+
| city      | rating    | count | open_days_total | open_days_avg |
+-----------+-----------+-------+-----------------+---------------+
| Cleveland | 3-4 stars |     3 |              51 |            17 |
| Cleveland | 4-5 stars |     3 |              96 |            32 |
+-----------+-----------+-------+-----------------+---------------+
```

ii. Do the two groups you chose to analyze have a different number of reviews?

- the two groups have different number of reviews

```sql
SELECT b.city
	,CASE -- split businesses into groups according to stars
		WHEN b.stars >= 4.0
			THEN '4-5 stars'
		WHEN b.stars >= 2.0
			THEN '2-3 stars'
		ELSE 'below 2'
		END AS rating
	,COUNT(DISTINCT b.id) AS num_of_businesses -- count distinct businesses in cleveland
	,COUNT(r.id) -- summation of all reviews for each business group
FROM Business b
LEFT JOIN review r ON r.business_id = b.id
WHERE city LIKE 'Cleveland'
GROUP BY rating
ORDER BY rating DESC;-- split businesses into groups according to stars

+-----------+-----------+-------------------+-------------+
| city      | rating    | num_of_businesses | COUNT(r.id) |
+-----------+-----------+-------------------+-------------+
| Cleveland | below 2   |                 7 |           0 |
| Cleveland | 4-5 stars |               103 |           8 |
| Cleveland | 2-3 stars |                79 |           4 |
+-----------+-----------+-------------------+-------------+
```

iii. Are you able to infer anything from the location data provided between these two groups? Explain.

SQL code used for analysis:

```sql
SELECT city,
b.name
	,CASE -- split businesses into groups according to stars
		WHEN stars >= 4.0
			THEN '4-5 stars'
		WHEN stars >= 2.0
			THEN '2-3 stars'
		ELSE 'below 2'
		END AS rating,
neighborhood,
c.category
FROM Business b
LEFT JOIN Category c ON c.business_id = b.id
WHERE city LIKE 'Cleveland'
GROUP BY rating, category-- split businesses into groups according to stars
+-----------+---------------------+-----------+-------------------+------------------------+
| city      | name                | rating    | neighborhood      |               category |
+-----------+---------------------+-----------+-------------------+------------------------+
| Cleveland | Manna Food Truck    | 2-3 stars | St Clair-Superior |                   None |
| Cleveland | Saigon Grille       | 2-3 stars | Goodrich Kirtland |            Restaurants |
| Cleveland | Saigon Grille       | 2-3 stars | Goodrich Kirtland |             Vietnamese |
| Cleveland | Grog Shop           | 4-5 stars |                   |                   None |
| Cleveland | Slyman's Restaurant | 4-5 stars | Goodrich Kirtland | American (Traditional) |
| Cleveland | Koko Bakery         | 4-5 stars | Goodrich Kirtland |               Bakeries |
| Cleveland | B.A. Sweetie Candy  | 4-5 stars |                   |           Candy Stores |
| Cleveland | Clean Machine       | 4-5 stars |                   |        Carpet Cleaning |
| Cleveland | Koko Bakery         | 4-5 stars | Goodrich Kirtland |           Coffee & Tea |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |            Ethnic Food |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |         Farmers Market |
| Cleveland | B.A. Sweetie Candy  | 4-5 stars |                   |                   Food |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |       Fruits & Veggies |
| Cleveland | Clean Machine       | 4-5 stars |                   |          Home Cleaning |
| Cleveland | Clean Machine       | 4-5 stars |                   |          Home Services |
| Cleveland | Tuesday Morning     | 4-5 stars |                   |        Interior Design |
| Cleveland | Clean Machine       | 4-5 stars |                   |         Local Services |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |          Market Stalls |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |             Meat Shops |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |         Public Markets |
| Cleveland | Slyman's Restaurant | 4-5 stars | Goodrich Kirtland |            Restaurants |
| Cleveland | Slyman's Restaurant | 4-5 stars | Goodrich Kirtland |             Sandwiches |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |        Seafood Markets |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |               Shopping |
| Cleveland | B.A. Sweetie Candy  | 4-5 stars |                   |         Specialty Food |
+-----------+---------------------+-----------+-------------------+------------------------+
(Output limit exceeded, 25 of 26 total rows shown)
```

```sql
SELECT city,
b.name
	,CASE -- split businesses into groups according to stars
		WHEN stars >= 4.0
			THEN '4-5 stars'
		WHEN stars >= 2.0
			THEN '2-3 stars'
		ELSE 'below 2'
		END AS rating,
neighborhood,
c.category
FROM Business b
LEFT JOIN Category c ON c.business_id = b.id
WHERE city LIKE 'Cleveland'
GROUP BY rating, category-- split businesses into groups according to stars
+-----------+---------------------+-----------+-------------------+------------------------+
| city      | name                | rating    | neighborhood      |               category |
+-----------+---------------------+-----------+-------------------+------------------------+
| Cleveland | Manna Food Truck    | 2-3 stars | St Clair-Superior |                   None |
| Cleveland | Saigon Grille       | 2-3 stars | Goodrich Kirtland |            Restaurants |
| Cleveland | Saigon Grille       | 2-3 stars | Goodrich Kirtland |             Vietnamese |
| Cleveland | Grog Shop           | 4-5 stars |                   |                   None |
| Cleveland | Slyman's Restaurant | 4-5 stars | Goodrich Kirtland | American (Traditional) |
| Cleveland | Koko Bakery         | 4-5 stars | Goodrich Kirtland |               Bakeries |
| Cleveland | B.A. Sweetie Candy  | 4-5 stars |                   |           Candy Stores |
| Cleveland | Clean Machine       | 4-5 stars |                   |        Carpet Cleaning |
| Cleveland | Koko Bakery         | 4-5 stars | Goodrich Kirtland |           Coffee & Tea |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |            Ethnic Food |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |         Farmers Market |
| Cleveland | B.A. Sweetie Candy  | 4-5 stars |                   |                   Food |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |       Fruits & Veggies |
| Cleveland | Clean Machine       | 4-5 stars |                   |          Home Cleaning |
| Cleveland | Clean Machine       | 4-5 stars |                   |          Home Services |
| Cleveland | Tuesday Morning     | 4-5 stars |                   |        Interior Design |
| Cleveland | Clean Machine       | 4-5 stars |                   |         Local Services |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |          Market Stalls |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |             Meat Shops |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |         Public Markets |
| Cleveland | Slyman's Restaurant | 4-5 stars | Goodrich Kirtland |            Restaurants |
| Cleveland | Slyman's Restaurant | 4-5 stars | Goodrich Kirtland |             Sandwiches |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |        Seafood Markets |
| Cleveland | West Side Market    | 4-5 stars | Ohio City         |               Shopping |
| Cleveland | B.A. Sweetie Candy  | 4-5 stars |                   |         Specialty Food |
+-----------+---------------------+-----------+-------------------+------------------------+
(Output limit exceeded, 25 of 26 total rows shown)
```

1. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones that are still open and the ones that are closed? List at least two differences and the SQL code you used to arrive at your answer.

i. Difference 1:

- There are more open businesses than closed

ii. Difference 2:

- There are more reviews for the open businesses than closed

SQL code used for analysis:

```sql
SELECT city
,CASE
	WHEN is_open = 1 THEN 'open'
	ELSE 'closed'
	END AS status
,COUNT(is_open) AS status_count
,review_count
,CASE -- split businesses into groups according to stars
	WHEN stars >= 4.0
		THEN '4-5 stars'
	WHEN stars >= 2.0
		THEN '2-3 stars'
	ELSE 'below 2' END AS rating
FROM business
WHERE city LIKE 'Cleveland'
GROUP BY status, rating;

+-----------+--------+--------------+--------------+-----------+
| city      | status | status_count | review_count | rating    |
+-----------+--------+--------------+--------------+-----------+
| Cleveland | closed |           16 |            6 | 2-3 stars |
| Cleveland | closed |           14 |            5 | 4-5 stars |
| Cleveland | open   |           63 |            8 | 2-3 stars |
| Cleveland | open   |           89 |           65 | 4-5 stars |
| Cleveland | open   |            7 |            6 | below 2   |
+-----------+--------+--------------+--------------+-----------+
```

1. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare the data for analysis.

Ideas for analysis include: Parsing out keywords and business attributes for sentiment analysis, clustering businesses to find commonalities or anomalies between them, predicting the overall star rating for a business, predicting the number of fans a user will have, and so on. These are just a few examples to get you started, so feel free to be creative and come up with your own problem you want to solve. Provide answers, in-line, to all of the following:

i. Indicate the type of analysis you chose to do:

- Analyzing the distribution of star ratings for restaurants in the Yelp dataset.

ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:

1. I will need the category from CATEGORY table, avg(stars) and review_count from the BUSINESS table. This will be my basis for analyzing the star distributions for the restaurants. It's easier to find the correlation between the review count and the star rating for cities themselves, since we're only looking at one category. From these, we can infer if the restaurants in one city will be high-rated statistically. I also included the review count to lend credibility to its rating (i.e. *if a lot of people say the restaurants are good, then it must be good*). We can forgive any bias this leads to since we're looking at the data in bulk.

iii. Output of your finished dataset:

```sql
+-------------------+-------------+---------------+--------------+
| city              | category    | average_stars | review_count |
+-------------------+-------------+---------------+--------------+
| Mesa              | Restaurants |           4.5 |          267 |
| Phoenix           | Restaurants |           3.5 |          188 |
| Chandler          | Restaurants |           3.5 |          141 |
| Westlake          | Restaurants |           4.0 |          105 |
| Pittsburgh        | Restaurants |          2.75 |          103 |
| Medina            | Restaurants |           4.0 |           94 |
| Scottsdale        | Restaurants |           4.0 |           91 |
| Sun Prairie       | Restaurants |           3.5 |           87 |
| Litchfield Park   | Restaurants |           3.5 |           83 |
| Toronto           | Restaurants |           3.4 |           75 |
| Fitchburg         | Restaurants |           3.5 |           74 |
| Cleveland         | Restaurants |           4.0 |           62 |
| Cuyahoga Falls    | Restaurants |           4.0 |           55 |
| Oakville          | Restaurants |           4.0 |           55 |
| Stuttgart         | Restaurants |           3.0 |           50 |
| Middleton         | Restaurants |           4.0 |           37 |
| Aurora            | Restaurants |           3.5 |           32 |
| Chesterland       | Restaurants |           4.0 |           30 |
| Mississauga       | Restaurants |           3.5 |           27 |
| Sheffield Village | Restaurants |           3.5 |           27 |
| Markham           | Restaurants |           3.0 |           25 |
| Tolleson          | Restaurants |           4.0 |           23 |
| Fountain Hills    | Restaurants |           3.5 |           21 |
| Montréal          | Restaurants |          3.25 |           15 |
| Verdun            | Restaurants |           3.5 |           11 |
+-------------------+-------------+---------------+--------------+
(Output limit exceeded, 25 of 43 total rows shown)
```

iv. Provide the SQL code you used to create your final dataset:

```sql
SELECT b.city
,c.category
,AVG(b.stars) AS average_stars
,b.review_count
FROM business b
JOIN category c ON c.business_id = b.id
WHERE c.category = 'Restaurants'
GROUP BY b.city
ORDER BY review_count DESC;
```