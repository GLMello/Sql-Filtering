<h1> Applying filters to SQL queries</h1>

 ### You can also read this in: [Português](https://github.com/GLMello/Filtro_Sql)

<h2>Description</h2>
This project consists of utilizing SQL filters to investigate potential security risks across different tasks. Throughout this project I will make use of different filters and operators in order to obtain the information needed to start mitigating the risks.
<br />


<h2>Scenario</h2>
You are a security professional at a large organization. Part of your job is to investigate security issues to help keep the system secure. You recently discovered some potential security issues that involve login attempts and employee machines.

Your task is to examine the organization’s data in their employees and log in attempts tables. You’ll need to use SQL filters to retrieve records from different datasets and investigate the potential security issues.


<h2>Walkthrough</h2>

<p align="left">
  
**Task 1:** <br/>
  
_You recently discovered a potential security incident that occurred after business hours. To investigate this, you need to query the log_in_attempts table and review after hours login activity. Use filters in SQL to create a query that identifies all failed login attempts that occurred after 18:00._ <br/><br/>

In order to be left with only failed login attempts that happened after 18:00 I went with the following command:<br/>

``
SELECT * FROM log_in_attempts WHERE login_time > '18:00' AND success = '0';
``
<br/><br />
By using the 'and' operator, I was able to set both restrictions at once and got the following:<br/><br />
<img src="https://i.imgur.com/fc6lFqw.png" height="55%" width="55%" alt="After hours failed logins"/>
<br /><br />

**Task 2**:<br />
_A suspicious event occurred on 2022-05-09. To investigate this event, you want to review all login attempts which occurred on this day and the day before. Use filters in SQL to create a query that identifies all login attempts that occurred on 2022-05-09 or 2022-05-08._
<br/><br/>
Here, I went with:<br/><br/>
``
SELECT * FROM log_in_attempts WHERE login_date = '2022-05-09' or login_date = '2022-05-08';``<br/> <br/>
With the 'or' operator, I restricted the query to the two desired days:<br/><br/>
<img src="https://i.imgur.com/tD5lA3T.png" height="55%" width="55%" alt="Between date"/>
<br /><br />
**Task 3**:<br />
_There’s been suspicious activity with login attempts, but the team has determined that this activity didn't originate in Mexico. Now, you need to investigate login attempts that occurred outside of Mexico. Use filters in SQL to create a query that identifies all login attempts that occurred outside of Mexico._ <br/><br />

For this task, I went back and looked at previous queries to see how Mexico was input in the table. I found out that both MEXICO and MEX were common in the table. This called for a wildcard to complement the filtering. I then went with the command: <br/>

``SELECT * FROM log_in_attempts WHERE NOT country LIKE 'MEX%';``<br/> <br/>
Using the '%' wildcard allowed me to filter out both MEX and MEXICO from the query. I ended up with: <br/><br/>
<img src="https://i.imgur.com/Qtxknw7.png" height="55%" width="55%" alt="Not Mexico"/>
<br /><br />
**Task 4**:
_Your team wants to perform security updates on specific employee machines in the Marketing department. You’re responsible for getting information on these employee machines and will need to query the employees table. Use filters in SQL to create a query that identifies all employees in the Marketing department for all offices in the East building._
<br /><br />
Once again, I was faced with multiple desired inputs as there are multiple offices in the East building. This, once again, asked for wild card usage along with a change of tables to query from: <br/>

``
SELECT * FROM Employees WHERE department = 'marketing' AND office LIKE 'east%';``<br/> <br/>

I was left with the desired query which included all marketing employees within any of the offices in the East building.<br/><br/>
<img src="https://i.imgur.com/gNwfTwJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<h2>Note</h2>

 This project was part of the [Google Cybersecurity Professional Certificate](https://www.coursera.org/professional-certificates/google-cybersecurity) course.<br />
