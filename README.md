# Pewlett-Hackard-Analysis
Making an employee analysis, Module 7. 


1. Overview of the analysis: Explain the purpose of this analysis.
* This project's goal was to discover the number of retiring employees by title and also identify which employees are able to participate in a mentorship program. 
* For finding the number of retiring employees by title, we limited our list to employees only born between January 1st, 1952, and December 31st, 1955. Then, we used the "DISTINCT ON" funtion to create a table that only contains the most recent title of each employee, eliminating past employee entries with a non-current title. Lastly in our retirement_titles table we excluded employees who have already left the company, and ordered by employee number. 
* For identifying which employees are eligible for mentorships, we created a table with current employees that were born between January 1st, 1965, and December 31st, 1965. 

2. Results:  Provide a bulleted list with four major points from the two analysis deliverables. Use images as support where needed.
* Deliverable 1: The number of retiring employees by Title: 
  * Point 1- Using "LEFT JOIN" to join the employees and titles tables. We joined the employees and titles tables on the "emp_no" column, and then used the "WHERE" function to only select rows with birth dates between January 1st, 1952, and December 31st, 1955. Finally, we ordered by ascending employee number. A screenshot of the code can be seen below: 
  * <img width="480" alt="Screen Shot 2022-02-01 at 5 51 06 PM" src="https://user-images.githubusercontent.com/96043107/152075856-c5582e4b-8876-4cc5-b6c4-97b0f0dc2464.png"
  * Point 2- Using "DISTINCT ON()" to remove duplicate rows. We selected the first_name, last_name, and title columns from out retiring_titles table we created in the step above, but used a "DISTINCT ON" command to eliminate any duplicate rows where the same name has been used more than once. A screenshot of the code can be seen below. 
  * <img width="410" alt="Screen Shot 2022-02-01 at 5 53 39 PM" src="https://user-images.githubusercontent.com/96043107/152076071-ea7a0c41-0d3b-4238-9e4b-1bc0e02a7a5d.png">

* Deliverable 2: Identifying employees eligible for the mentorship program. 
  * Point 1- Using a "DISTINCT ON()" statement to retrieve the first occurance of the employee number for each row defined by the ON() clause. This is different from above because we are using columns from three different tables, using "INNER JOIN()" twice with first the dept_emp table on the employees table, and then adding the titles table. This means that only the first occurance of the employee number is retrieved, which in this case would be in the employees table. A screenshot of the code can be seen below:
  * <img width="345" alt="Screen Shot 2022-02-01 at 5 59 01 PM" src="https://user-images.githubusercontent.com/96043107/152076578-ad4863c6-1549-4dbc-bb6c-1134ca2810d4.png">
  * Point 2- Filtering the data on the to_date column to all the current employees. We first filter out all employees who are not eligible for the mentorship program by filtering the birth_date column for employees only born between January 1st, 1965, and December 31st, 1965. Then, using an "AND" statement, we select the to_date column from the dept_emp table and set it equal to '9999-01-01" which assures that the data on the to_date column is for all current employees. A screenshot of the code can be seen below: 
  * <img width="492" alt="Screen Shot 2022-02-01 at 6 12 08 PM" src="https://user-images.githubusercontent.com/96043107/152077660-fbd10d7e-8608-4411-ba4f-c7e62655d315.png">


3. Summary: High-level responses to the following questions: 

--How many roles will need to be filled as the "silver tsunami" begins to make an impact?
* The retiring_titles table tells us that 29,414 Senior Engineers, 28,254 Senior Staff, 14,222 Engineers, 12,243 Staff, 4,502 Technique Leaders, 1,761 Assistant Engineers, and 2 Managers were all born between January 1st, 1952, and December 31st, 1955. The total number of employees born between those dates is 90,398. When I break this down into the roles that are needed to be filled by title and department, we can get a better understanding of which roles are needed to be filled. 
<img width="370" alt="Screen Shot 2022-02-01 at 6 33 49 PM" src="https://user-images.githubusercontent.com/96043107/152079577-e230dd56-bc5a-4573-8e81-f1ae195acab7.png">
* The table above does not include the departments "Human Resources", "Finance", "Development", or "Customer Service" and is just an excerpt of the table I created. 

--Are there enough qualified, retirment-ready employees in the departments to mentor the next generatiuon of PH employees?
In order to determine of there are enough qualified staff to train others at PH, I used an additional filter on our "unique_titles_department" table that only gives employees who are in high-level positions; those being: 'Senior Engineer', 'Senior Staff', 'Technique Leader', and 'Manager'. From the table below, we can examine how many employees are qualified for staff training in each department. 
* <img width="371" alt="Screen Shot 2022-02-01 at 6 41 03 PM" src="https://user-images.githubusercontent.com/96043107/152080206-e76c7d49-5afe-4a7f-ad3b-96aba03ea2a8.png">
