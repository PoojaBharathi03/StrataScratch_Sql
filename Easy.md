## 1. Customer Details ([Question Link](https://platform.stratascratch.com/coding/9891-customer-details?code_type=3))
### Find the details of each customer regardless of whether the customer made an order. Output the customer's first name, last name, and the city along with the order details.
### You may have duplicate rows in your results due to a customer ordering several of the same items. Sort records based on the customer's first name and the order details in ascending order.

### Tables: customers, orders

### Solution:


```
select first_name, last_name,city, order_details
from customers c
left join orders o
on c.id = o.cust_id
order by c.first_name, order_details asc;
```

## 2. ORDER DETAILS ([Question Link](https://platform.stratascratch.com/coding/9913-order-details?code_type=3))

### Find order details made by Jill and Eva.
Consider the Jill and Eva as first names of customers.
Output the order date, details and cost along with the first name.
Order records based on the customer id in ascending order.

### Tables: customers, orders


### SOLUTION:
```
select c.first_name,	o.order_date,	o.order_details,	o.total_order_cost
from customers c
join orders o 
on c.id = o.cust_id
where first_name = 'Jill' or first_name = 'Eva'
order by c.id asc;
```

## 3. Popularity of Hack ([Question Link](https://platform.stratascratch.com/coding/10061-popularity-of-hack?code_type=3))

### Meta/Facebook has developed a new programing language called Hack.To measure the popularity of Hack they ran a survey with their employees. The survey included data on previous programing familiarity as well as the number of years of experience, age, gender and most importantly satisfaction with Hack. Due to an error location data was not collected, but your supervisor demands a report showing average popularity of Hack by office location. Luckily the user IDs of employees completing the surveys were stored.
##Based on the above, find the average popularity of the Hack per office location.
## Output the location along with the average popularity.

## Tables: facebook_employees, facebook_hack_survey

## solution:

```
select fe.location, avg(fs.popularity) as avg_popularity
FROM facebook_employees fe
join facebook_hack_survey fs
on fe.id = fs.employee_id
group by fe.location
```

## 4. Finding Updated Records ([Question Link](https://platform.stratascratch.com/coding/10299-finding-updated-records?code_type=3))

### We have a table with employees and their salaries, however, some of the records are old and contain outdated salary information. Find the current salary of each employee assuming that salaries increase each year. Output their id, first name, last name, department ID, and current salary. Order your list by employee ID in ascending order.

## Table: ms_employee_salary

## solution:
```
select id,	first_name,	last_name,	department_id,	max(salary) as current_salary
from ms_employee_salary
group by id;
```

## 5. Count the number of user events performed by MacBookPro users ([Question Link](https://platform.stratascratch.com/coding/9653-count-the-number-of-user-events-performed-by-macbookpro-users?code_type=3))

### Output the result along with the event name.
Sort the result based on the event count in the descending order.
###  Apple | Easy | General Practice | ID 9653

### Solution:
```
select event_name, count(user_id) as event_count
from playbook_events
where device = 'macbook pro'
group by event_name;
```

## 6. Churro Activity Date ([Question Link](https://platform.stratascratch.com/coding/9688-churro-activity-date?code_type=3))

### Find the activity date and the pe_description of facilities with the name 'STREET CHURROS' and with a score of less than 95 points.

### Table: los_angeles_restaurant_health_inspections

```
select activity_date, pe_description 
from los_angeles_restaurant_health_inspections
where facility_name = 'STREET CHURROS' and score<95 ;
```

## 7. Find libraries who haven't provided the email address in circulation year 2016 but their notice preference definition is set to email ([Question Link](https://platform.stratascratch.com/coding/9924-find-libraries-who-havent-provided-the-email-address-in-2016-but-their-notice-preference-definition-is-set-to-email?code_type=3))

### Find libraries who haven't provided the email address in circulation year 2016 but their notice preference definition is set to email.
Output the library code.

### Table: library_usage

### Solution:
```
select distinct home_library_code 
from library_usage 
where circulation_active_year =2016 and provided_email_address=0  and notice_preference_definition='email' ;
```

## 8. Find the base pay for Police Captains ([Question Link](https://platform.stratascratch.com/coding/9972-find-the-base-pay-for-police-captains?code_type=3))

### Find the base pay for Police Captains.
Output the employee name along with the corresponding base pay.

### Table: sf_public_salaries

### Solution:

```
select distinct employeename, basepay 
from sf_public_salaries
where jobtitle like 'captain%'
```

## 9. Find the most profitable company in the financial sector of the entire world along with its continent ([Question Link](https://platform.stratascratch.com/coding/9663-find-the-most-profitable-company-in-the-financial-sector-of-the-entire-world-along-with-its-continent?code_type=3))

### Find the most profitable company from the financial sector. Output the result along with the continent.

### Table: forbes_global_2010_2014

### Solution:

```
select company, continent 
from forbes_global_2010_2014
where sector = 'Financials'
order by profits desc
limit 1;
```

## 10. Bikes Last Used ([Question Link](https://platform.stratascratch.com/coding/10176-bikes-last-used?code_type=3))


### Find the last time each bike was in use. Output both the bike number and the date-timestamp of the bike's last use (i.e., the date-time the bike was returned). Order the results by bikes that were most recently used.

### Table: dc_bikeshare_q1_2012

### Solution:
```
select  bike_number, max(end_time) as last_used
from dc_bikeshare_q1_2012
group by bike_number
order by end_time desc;
```

## 11. Lyft Driver Wages ([Question Link](https://platform.stratascratch.com/coding/10003-lyft-driver-wages?code_type=3))

### Find all Lyft drivers who earn either equal to or less than 30k USD or equal to or more than 70k USD.
Output all details related to retrieved records.

### Table: lyft_drivers
### Solution:

```
select * 
from lyft_drivers
where yearly_salary <= 30000 or yearly_salary>=70000;
```

## 12. Find all posts which were reacted to with a heart ([Question Link](https://platform.stratascratch.com/coding/10087-find-all-posts-which-were-reacted-to-with-a-heart?code_type=3))

### Find all posts which were reacted to with a heart. For such posts output all columns from facebook_posts table.

### Tables: facebook_reactions, facebook_posts

### Solution:
```
select distinct p.* 
from facebook_reactions r 
join facebook_posts p 
on r.post_id = p.post_id
where r.reaction = 'heart';
```

## 13. Count the number of movies that Abigail Breslin nominated for oscar ([Question Link](https://platform.stratascratch.com/coding/10128-count-the-number-of-movies-that-abigail-breslin-nominated-for-oscar?code_type=3))

### Count the number of movies that Abigail Breslin was nominated for an oscar.

### Solution:
```
select count(*) as n_movies_by_abi
from oscar_nominees
where nominee = 'Abigail Breslin';
```

## 14. Find how many times each artist appeared on the Spotify ranking list ([Question Link](https://platform.stratascratch.com/coding/9992-find-artists-that-have-been-on-spotify-the-most-number-of-times?code_type=3))

### Find how many times each artist appeared on the Spotify ranking list
Output the artist name along with the corresponding number of occurrences.
Order records by the number of occurrences in descending order.

### Table: spotify_worldwide_daily_song_ranking

### Solutio:
```
select artist, count(*) as n_occurences 
from spotify_worldwide_daily_song_ranking
group by artist
order by n_occurences desc;
```

## 15.Number Of Bathrooms And Bedrooms ([Question Link](https://platform.stratascratch.com/coding/9622-number-of-bathrooms-and-bedrooms?code_type=3))

## Airbnb | Easy | Interview Questions | ID |  962261

### Find the average number of bathrooms and bedrooms for each city’s property types. Output the result along with the city name and the property type.

### able: airbnb_search_details

### Solution:
```
select city, property_type, avg(bathrooms) as bathrooms_avg , avg(bedrooms) as     bedrooms_avg
from airbnb_search_details
group by city, property_type;
```
