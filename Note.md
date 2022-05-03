# Part 1: Yelp Dataset Profiling and Understanding

### 1. Profile the data by finding the total number of records for each of the tables below:
	
i. Attribute table = 10000

	 Select count(*)
	 from attribute

ii. Business table = 10000

	 Select count(*)
	 from Business

iii. Category table = 10000

	 Select count(*)
	 from Category

iv. Checkin table = 10000

	 Select count(*)
	 from Checkin

v. elite_years table = 10000

	 Select count(*)
	 from elite_years


vi. friend table = 10000

	 Select count(*)
	 from friend

vii. hours table = 10000

	 Select count(*)
	 from hours

viii. photo table = 10000

	 Select count(*)
	 from photo

ix. review table = 10000

	 Select count(*)
	 from review

x. tip table = 10000

	 Select count(*)
	 from tip

xi. user table = 10000

	 Select count(*)
	 from user


### 2. Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key.

i. Business = 10000

	 Select count(Distinct id)
	 from Business

ii. Hours = 1562

	 Select count(Distinct business_id)
	 from Hours

iii. Category = 2643

	 Select count(Distinct business_id)
	 from Category

iv. Attribute = 1115

	 Select count(Distinct business_id)
	 from Attribute

v. Review = 10000

	 Select count(Distinct id)  
	 from Review
##### Used the id as primary key

vi. Checkin = 493

	 Select count(Distinct business_id)
	 from Checkin

vii. Photo = 10000
 
	 Select count(Distinct id)  'Used the id as primary key'
	 from Photo 

viii. Tip = 537 

	 Select count(Distinct user_id)    'Used the user_id as primary key'
	 from Tip

ix. User = 10000

	 Select count(Distinct id)
	 from user

x. Friend = 11

	 Select count(Distinct user_id)
	 from Friend
 
xi. Elite_years = 2780

	 Select count(Distinct user_id)
	 from Elite_years

Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.	



### 3. Are there any columns with null values in the Users table? Indicate "yes," or "no."

Answer: No 

SQL code used to arrive at answer:


	 select *
	 from user
	 where (id is null) OR (name is null)  OR (review_count is null) OR (yelping_since is null) OR (useful is null) 
	 OR (funny is null) OR (cool is null) OR (fans is null) OR (average_stars is null) OR (compliment_hot is null)
	 OR (compliment_more is null) OR (compliment_profile is null) OR (compliment_cute is null) OR (compliment_list is null)
	 OR (compliment_note is null) OR (compliment_plain is null) OR (compliment_cool is null) OR (compliment_funny is null)
	 OR (compliment_writer is null) OR (compliment_photos is null)


	
### 4. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:

i. Table: Review, Column: Stars

min: 1	max: 5	avg: 3.7082

	 select  min (Stars) As min_stars , max (Stars) As max_stars , avg (Stars) As avg_stars
	 from Review

ii. Table: Business, Column: Stars

min: 1.0  max: 5.0	avg: 3.6549

	select  min (Stars) As min_stars , max (Stars) As max_stars , avg (Stars) As avg_stars
	from Business

iii. Table: Tip, Column: Likes

min: 0	 max: 2	  avg: 0.0144

	select  min (Likes) As min_Likes , max (Likes) As max_Likes , avg (Likes) As avg_Likes
	from Tip

iv. Table: Checkin, Column: Count

min: 1	max: 53	avg: 1.9414

	select  min (Count) As min_Count , max (Count) As max_Count , avg (Count) As avg_Count
	from Checkin	

v. Table: User, Column: Review_count

min: 0	 max: 2000  avg: 24.2995

	select  min (Review_count) As min_Review_count , max (Review_count) As Review_count , avg (Review_count) As Review_count
	from User


### 5. List the cities with the most reviews in descending order:

SQL code used to arrive at answer:

	select sum(review_count) , city
	from business
	group by city
	order by sum(review_count) desc

Copy and Paste the Result Below:
	
	+-------------------+-----------------+
	| sum(review_count) | city            |
	+-------------------+-----------------+
	|             82854 | Las Vegas       |
	|             34503 | Phoenix         |
	|             24113 | Toronto         |
	|             20614 | Scottsdale      |
	|             12523 | Charlotte       |
	|             10871 | Henderson       |
	|             10504 | Tempe           |
	|              9798 | Pittsburgh      |
	|              9448 | Montréal        |
	|              8112 | Chandler        |
	|              6875 | Mesa            |
	|              6380 | Gilbert         |
	|              5593 | Cleveland       |
	|              5265 | Madison         |
	|              4406 | Glendale        |
	|              3814 | Mississauga     |
	|              2792 | Edinburgh       |
	|              2624 | Peoria          |
	|              2438 | North Las Vegas |
	|              2352 | Markham         |
	|              2029 | Champaign       |
	|              1849 | Stuttgart       |
	|              1520 | Surprise        |
	|              1465 | Lakewood        |
	|              1155 | Goodyear        |
	+-------------------+-----------------+
(Output limit exceeded, 25 of 362 total rows shown)


### 6. Find the distribution of star ratings to the business in the following cities:

i. Avon

SQL code used to arrive at answer:

	select stars As star_ratings , count(stars) as count
	from business
	where city = "Avon"
	group by stars

Copy and Paste the Resulting Table Below (2 columns â€“ star rating and count):

	+--------------+-------+
	| star_ratings | count |
	+--------------+-------+
	|          1.5 |     1 |
	|          2.5 |     2 |
	|          3.5 |     3 |
	|          4.0 |     2 |
	|          4.5 |     1 |
	|          5.0 |     1 |
	+--------------+-------+

ii. Beachwood

SQL code used to arrive at answer:

	select stars As star_ratings , count(stars) as count
	from business
	where city = "Beachwood"
	group by stars

Copy and Paste the Resulting Table Below (2 columns â€“ star rating and count):
		
	+--------------+-------+
	| star_ratings | count |
	+--------------+-------+
	|          2.0 |     1 |
	|          2.5 |     1 |
	|          3.0 |     2 |
	|          3.5 |     2 |
	|          4.0 |     1 |
	          4.5 |     2 |
	|          5.0 |     5 |
	+--------------+-------+

### 7. Find the top 3 users based on their total number of reviews:

SQL code used to arrive at answer:

	select id, name , sum(review_count)
	from user
	group by id
	order by sum(review_count) desc
	limit 3

Copy and Paste the Result Below:

	+------------------------+--------+-------------------+
	| id                     | name   | sum(review_count) |
	+------------------------+--------+-------------------+
	| -G7Zkl1wIWBBmD0KRy_sCw | Gerald |              2000 |
	| -3s52C4zL_DHRK0ULG6qtg | Sara   |              1629 |
	| -8lbUNlXVSoXqaRRiHiSNg | Yuri   |              1339 |
	+------------------------+--------+-------------------+		


### 8. Does posing more reviews correlate with more fans?

Please explain your findings and interpretation of the results:

Yes there is a correlation between the number of reviews and fans, it is a positive correlation but it is not a strong one 
we calculated the correlation coefficient and it is 0.00083033897859 positive and not close to one so the correlation is positive and weak

	select review_count , fans ,
	(Avg(review_count * fans) - (Avg(review_count) * Avg(fans))) / ((AVG(review_count*review_count) - AVG(review_count)*AVG(review_count)) * 			(AVG(fans*fans) - AVG(fans)*AVG(fans))) As correlation  
	from user

### 9. Are there more reviews with the word "love" or with the word "hate" in them?

Answer: love


QL code used to arrive at answer:

	SELECT reaction, count(*) AS count
	FROM (
	      SELECT CASE WHEN LOWER(text) LIKE '%love%' THEN 'love'
	                  WHEN LOWER(text) LIKE '%hate%' THEN 'hate' 
	                  ELSE NULL
	                  END reaction
	      FROM review)
	GROUP BY reaction
	

### 10. Find the top 10 users with the most fans:

SQL code used to arrive at answer:

	SELECT id , name , fans
	FROM user
	order by fans desc
	limit 10

Copy and Paste the Result Below:

	+------------------------+-----------+------+
	| id                     | name      | fans |
	+------------------------+-----------+------+
	| -9I98YbNQnLdAmcYfb324Q | Amy       |  503 |
	| -8EnCioUmDygAbsYZmTeRQ | Mimi      |  497 |
	| --2vR0DIsmQ6WfcSzKWigw | Harald    |  311 |
	| -G7Zkl1wIWBBmD0KRy_sCw | Gerald    |  253 |
	| -0IiMAZI2SsQ7VmyzJjokQ | Christine |  173 |
	| -g3XIcCb2b-BD0QBCcq2Sw | Lisa      |  159 |
	| -9bbDysuiWeo2VShFJJtcw | Cat       |  133 |
	| -FZBTkAZEXoP7CYvRV2ZwQ | William   |  126 |
	| -9da1xk7zgnnfO1uTVYGkA | Fran      |  124 |
	| -lh59ko3dxChBSZ9U7LfUw | Lissa     |  120 |
	+------------------------+-----------+------+
		

# Part 2: Inferences and Analysis

### 1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. Compare the businesses with 2-3 stars to the businesses with 4-5 stars and answer the following questions. Include your code.
	
i. Do the two groups you chose to analyze have a different distribution of hours?

	select  case
	When stars >= 4 Then "4-5 stars"
	when stars >= 2 Then "2-3 stars"
	Else "Below 2"
	End Stars_category , COUNT(DISTINCT business.id) AS id_count , count(hours) As Total_hours 
	, count(hours) / count(business.id) As avg_hour
	from business Inner Join category on business.id = category.business_id
	Inner Join hours on category.business_id = hours.business_id
	WHERE city = 'Las Vegas' and category ='Food'
	group by stars

	+----------------+----------+-------------+----------+
	| Stars_category | id_count | Total_hours | avg_hour |
	+----------------+----------+-------------+----------+
	| 2-3 stars      |        1 |           7 |        1 |
	| 4-5 stars      |        1 |           6 |        1 |
	+----------------+----------+-------------+----------+

These is a small difference between hours for two groups

ii. Do the two groups you chose to analyze have a different number of reviews?

	select  case
	When stars >= 4 Then "4-5 stars"
	when stars >= 2 Then "2-3 stars"
	Else "Below 2"
	End Stars_category , COUNT(DISTINCT business.id) AS id_count , sum(review_count)
	from business Inner Join category on business.id = category.business_id
	WHERE city = 'Las Vegas' and category ='Food'
	group by stars   

	+----------------+----------+-------------------+
	| Stars_category | id_count | sum(review_count) |
	+----------------+----------+-------------------+
	| 2-3 stars      |        1 |                 6 |
	| 4-5 stars      |        1 |                30 |
	+----------------+----------+-------------------+
 
Yes, there is a huge difference between the number of reviews for two groups
 
iii. Are you able to infer anything from the location data provided between these two groups? Explain.

SQL code used for analysis:

	select *,  case
	When stars >= 4 Then "4-5 stars"
	when stars >= 2 Then "2-3 stars"
	Else "Below 2"
	End Stars_category
	from business Inner Join category on business.id = category.business_id
	WHERE city = 'Las Vegas' and category ='Food'
	group by stars

	+------------------------+-----------------------------+--------------+-----------------------------+-----------+-------+-------------+----------	+-----------+-------+--------------+---------+------------------------+----------+----------------+
	| id                     | name                        | neighborhood | address                     | city      | state | postal_code | latitude 	| longitude | stars | review_count | is_open | business_id            | category | Stars_category |
	+------------------------+-----------------------------+--------------+-----------------------------+-----------+-------+-------------+----------	+-----------+-------+--------------+---------+------------------------+----------+----------------+
	| 1q44aWEcDN7uRvA2l8xpvQ | Walgreens                   | Eastside     | 3808 E Tropicana Ave        | Las Vegas | NV    | 89121       |  36.1007 	|  -115.091 |   2.5 |            6 |       1 | 1q44aWEcDN7uRvA2l8xpvQ | Food     | 2-3 stars      |
	| 0aKsGxx7XP2TMs_fn_9xVw | Sweet Ruby Jane Confections | Southeast    | 8975 S Eastern Ave, Ste 3-B | Las Vegas | NV    | 89123       |   36.015 	|  -115.118 |   4.0 |           30 |       0 | 0aKsGxx7XP2TMs_fn_9xVw | Food     | 4-5 stars      |
	+------------------------+-----------------------------+--------------+-----------------------------+-----------+-------+-------------+----------	+-----------+-------+--------------+---------+------------------------+----------+----------------+	

Since the groups I choose tend to be two records only, there is no such info can we get. 
		
### 2. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones that are still open and the ones that are closed? List at least two differences and the SQL code you used to arrive at your answer.

i. Difference 1:
 
Number of businesses of the open ones is much higher than the closed onese.
         
ii. Difference 2:
         
The total review for the open businesses is so huge compared to close businesses.   
         
SQL code used for analysis:

	select count(name) As Number_of_business , is_open ,count(distinct neighborhood ),
	sum(review_count), avg(latitude) , avg(longitude), avg(stars)
	from business
	group by is_open

	+--------------------+---------+-------------------------------+-------------------+---------------+----------------+---------------+
	| Number_of_business | is_open | count(distinct neighborhood ) | sum(review_count) | avg(latitude) | avg(longitude) |    avg(stars) |
	+--------------------+---------+-------------------------------+-------------------+---------------+----------------+---------------+
	|               1520 |       0 |                           168 |             35261 | 38.8135013816 | -92.3074901316 | 3.52039473684 |
	|               8480 |       1 |                           280 |            269300 | 38.5594333019 | -92.7458396236 | 3.67900943396 |
	+--------------------+---------+-------------------------------+-------------------+---------------+----------------+---------------+
	
### 3. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare the data for analysis.

Ideas for analysis include: Parsing out keywords and business attributes for sentiment analysis, clustering businesses to find commonalities or anomalies between them, predicting the overall star rating for a business, predicting the number of fans a user will have, and so on. These are just a few examples to get you started, so feel free to be creative and come up with your own problem you want to solve. Provide answers, in-line, to all of the following:
	
i. Indicate the type of analysis you chose to do:

	Predicting and identifying the categories for the most successful businesses         
         
ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:
 
	I would know the categories than the most successful businesses belong to, so that will help to predict when someone would like to start new 		business, I analyze that depending on 
	the Number of business and average of stars rating also putting the total reviews on front of you with the results will help to know how much 		this avg is significant, calculated the average
	of openness will give us better understanding of how much of these businesses continue

The table below show the results I got.
                  
iii. Output of your finished dataset:

	+------------------------+--------------------+-----------+-------------+---------------+
	| category               | Number_of_business | Avg_stars | Avg_openess | total_reviews |
	+------------------------+--------------------+-----------+-------------+---------------+
	| Restaurants            |                 71 |      3.46 |        0.75 |          4504 |
	| Shopping               |                 30 |      3.98 |        0.83 |           977 |
	| Food                   |                 23 |      3.78 |        0.87 |          1781 |
	| Nightlife              |                 20 |      3.48 |         0.6 |          1351 |
	| Bars                   |                 17 |       3.5 |        0.65 |          1322 |
	| Health & Medical       |                 17 |      4.09 |        0.94 |           203 |
	| Home Services          |                 16 |       4.0 |        0.94 |            94 |
	| Beauty & Spas          |                 13 |      3.88 |        0.92 |           119 |
	| Local Services         |                 12 |      4.21 |        0.83 |           100 |
	| American (Traditional) |                 11 |      3.82 |        0.73 |          1128 |
	+------------------------+--------------------+-----------+-------------+---------------+        
         
iv. Provide the SQL code you used to create your final dataset:

	select category , count (Name) As Number_of_business,round(avg(stars),2) As Avg_stars,
	round(avg(is_open),2) As Avg_openess ,sum(review_count) As total_reviews
	from business Inner Join category on business.id = category.business_id
	group by category
	Having Number_of_business > 10
	order by Number_of_business desc
