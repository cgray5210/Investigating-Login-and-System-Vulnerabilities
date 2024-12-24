# Investigating-Login-and-System-Vulnerabilities in SQL

## Objective

In this lab, I acted as a security professional tasked with investigating potential security issues related to login attempts and employee machines. Using SQL, I analyzed data from the employees and log_in_attempts tables to uncover suspicious patterns and identify possible vulnerabilities in the organization’s system. This hands-on experience reinforced the importance of database analysis in cybersecurity investigations.


### Skills Learned

- Writing and executing SQL queries to filter and retrieve specific data.
- Using conditional clauses (WHERE, BETWEEN, etc.) for targeted data analysis.
- Investigating security concerns through database records.
- Identifying anomalies in login attempts and employee records.



### Tools Used

- SQL Database Management System (DBMS).
- SQL queries for data retrieval and analysis.
- Dataset filters to isolate and investigate security-related patterns.

## Steps

![Screen Shot 2024-12-23 at 6 14 49 PM](https://github.com/user-attachments/assets/6103b448-cc25-4169-ba3a-9e6a0c269ba4)

Ref 1. This is a screenshot of the prompt given for the lab I will be breaking down

![Screen Shot 2024-12-23 at 6 15 49 PM](https://github.com/user-attachments/assets/6ec9f1d5-0dbb-499e-a5f2-ccf8917e2430)

![Screen Shot 2024-12-23 at 6 18 28 PM](https://github.com/user-attachments/assets/fd41a519-8e01-44b1-988b-7c63f3a87954)

![Screen Shot 2024-12-23 at 6 19 30 PM](https://github.com/user-attachments/assets/281ff29a-4a00-4782-8129-bccc72656a5d)

Ref 2. In this first scenario we are asked to retrieve failed login attempts made after business hours. Office hours end at '18:00'. In order to do that, I had to use filters in SQL to create a query for this data. The query works like this, I used the command "SELECT *" because I would like to retrieve all columns of data from the table. "FROM log_in_attempts" specifies which table I am pulling data from in this case it would be the log in attempts table. The command "WHERE login_time > '18:00'" filters the results to include only the login attempts that happened after office hours. Lastly, the command "AND success = FALSE" narrows down the results to unsucessful login attempts. The last screenshot shows the result of my query.

![Screen Shot 2024-12-23 at 6 28 16 PM](https://github.com/user-attachments/assets/1da544c5-cc62-4f2a-8f94-2e4e477a7e64)

![Screen Shot 2024-12-23 at 6 27 41 PM](https://github.com/user-attachments/assets/da88d3c3-1546-4e14-ad0a-df0d993a5c99)

![Screen Shot 2024-12-23 at 6 34 32 PM](https://github.com/user-attachments/assets/f7b34db1-125b-4319-ae5d-9136b060a605)

Ref 3. This screenshot shows the scenario and the code that I wrote in order to address the scenario. To investigate this event it is similar to the previous one. I need to use command "SELECT *" to retrieve all columns of data. I would like to pull data from the log in attempts table again so that stays the same. This time I am investigating login attempts that occurred on 2022-05-09 or 2022-05-08, so in this case I needed to use the OR operator. This filters out the results to include records on either of those dates. The last screenshot is the result of my query.

![Screen Shot 2024-12-23 at 6 35 05 PM](https://github.com/user-attachments/assets/c148e992-1213-4c73-9aff-bab28e83abd9)

![Screen Shot 2024-12-23 at 6 36 09 PM](https://github.com/user-attachments/assets/625a02df-7b5c-48c4-a598-808264118dd9)

![Screen Shot 2024-12-23 at 6 36 29 PM](https://github.com/user-attachments/assets/2a5a8797-60c5-42d0-a30b-5030227766aa)

Ref 4. In this scenario we are asked to investigate logins that did NOT originate in Mexico. We must also note that the country field includes entries with 'MEX' and 'MEXICO' so we must write our SQL query to filter those results out completely. The code starts the same as the previous scenarios, I ask to retrieve all columns of data from the table with "SELECT *" and pull data form the log in attempts table. In this case, we use the NOT operator because we want results of countries that are not Mexico and we use the LIKE operator for pattern matching since there are two potential entries that Mexico could be under. So I used the command "WHERE NOT country LIKE 'MEX%". The % is a wildcard that matches zero or more characters, which means in 'MEX%' if there are any characters after that then it will find it. This query retreives all records from the login attempts table where the country does not match MEX or MEXICO. The last screenshot shows the result of my query.

![Screen Shot 2024-12-23 at 6 45 25 PM](https://github.com/user-attachments/assets/d151434c-27a5-4fae-b24f-b2e5914c9ace)

![Screen Shot 2024-12-23 at 6 47 24 PM](https://github.com/user-attachments/assets/59d0f2ea-6b86-4d0a-a9c1-da242414c99e)

Ref 5. We are asked to retrieve information about all employees in the "Marketing" department whose offices are located in the East building. In order to obtain that data I used "SELECT *" again to retrieve all columns of data. This time we will be pulling information from the employees table, I used the AND and LIKE operators in order to filter out the data for this scenario. We want to find all employees in the marketing department using the command "WHERE department = 'Marketing'" , we also only want the employees who are in the marketing department AND east building which is why I used the command "AND office LIKE 'East%'". Lastly, I used a wildcard again so we can filter out all employees in the east building no matter what office number comes after east. The results of my query are above.

![Screen Shot 2024-12-23 at 7 00 52 PM](https://github.com/user-attachments/assets/f406f7c6-10dd-4a02-af37-2c85cde46359)

![Screen Shot 2024-12-23 at 6 56 42 PM](https://github.com/user-attachments/assets/07f85549-0340-4224-9d7f-07951e4e3ca1)

Ref 6. This time we are asked to locate the information of employees in the Finance or Sales department. The code is similar to the ones above, "SELECT *" to retrieve all columns of data, and we are pulling data from the employees table. This time we are using the OR operator so in the code, I wrote "WHERE department = 'Finance' or department = 'Sales'" that way I am able to retrieve employees in both departments. In this case, it is important to specify what department is equal to for both departments or it will only retrieve one of the departments information. The results of my query are above.

![Screen Shot 2024-12-23 at 7 01 18 PM](https://github.com/user-attachments/assets/34bb401c-3ff9-41c6-a904-525eebbc11fe)

![Screen Shot 2024-12-23 at 7 03 05 PM](https://github.com/user-attachments/assets/7851f3b2-15d1-40b3-974b-fdb6055c05b0)

Ref 7. In this last scenario we are asked to retrieve records for employees who are not in the information technology department. This is obtained by a similar process as the other scenarios where I am retrieving all columns of data, and pulling data form the employees table. In this case we use the NOT operator to filter out employees who aren't in the Information Technology department. The code is written as follows "WHERE NOT department = 'Information Technology';" as you can see the results of my query above give me all the employees who are not in the Information Technology department.








