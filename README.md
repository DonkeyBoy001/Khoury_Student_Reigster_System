# Khoury_Student_Reigster_System
In today's world, student course registration and management are becoming increasingly important. That's why we've designed a student course registration and management system based on GitHub. This system aims to help students register for courses they're interested in more easily, as well as help teachers manage and track students' learning progress more effectively.

The system features include the following:

Students can register for courses they're interested in on GitHub, including course names, teacher names, course times, and receive reminders before courses begin.

Students can easily view their registered courses and related information, as well as cancel registered courses.

Teachers can conveniently view the students who have registered for the course, and track their learning progress and grades at any time.

Teachers can publish course information, assignments, exams, and schedules on GitHub so that students can stay informed about relevant information.

The system has user management and identity authentication features to ensure that only authenticated users can access relevant information.

The system's advantages include its use of GitHub's platform and tools, which provide excellent scalability and maintainability. Additionally, the use of open-source technology and communities helps promote and improve the system. Furthermore, the system's implementation offers high flexibility and customization, allowing for adjustments and optimizations based on different needs.

If you're interested in this project, please visit our GitHub repository for more information and detailed documentation.


Login Page
![image](https://user-images.githubusercontent.com/91183483/232697194-05706e4c-477f-40c1-9627-afb99285aef7.png)


## Project Introduction
- Overall structure

    - The back-end adopts python+flask+mysql. There is no server deployment, and it can be tested and run on a single machine.

    - The front-end draws on the front-end page template found on the Internet and is modified on this basis. The main technology is html+css+js

    - Front-end and back-end separation development, see http interface design.docx, use postman and other tools for interface testing
## directory structure
<pre>
app/ Project Source Code
|--- models/ Backend model layer for reading and writing databases
|--- validate/ Backend verification layer, used to verify the validity of parameters for HTTP requests
|--- web/ Backend controller layer for processing HTTP requests
|--- __init__.py Entry function
|--- static/ Frontend static file directory
    |--- js/ Front end JavaScript file
    |--- *.html Frontend HTML page file
sql/ Database creation script and instructions, test data script
httpInterface designdocx
Frontend Page Template/ 
</pre>

## Project Environment Configuration
- Download and install MySQL 8
    - Execute SQL/Database Creation Script - No Comments. SQL
    - Execute SQL/System Test Data.sql
- Download and install Python 3.7.3
- IDE: pycharm community
- Relying on third-party libraries (installed using tools such as pipenv)
    - flask
    - wtforms
    - pymysql
    - flask-login

## Core requirements
### Overall requirements
- Web-based database application system
- E-R diagram design concept pattern, export logic pattern
- Design the system structure diagram of the application system and determine its functions
- Create databases and tables, input initial data, and require that the number of records in each table be no less than 18
- No need to connect to a remote database, just on one machine
- The division of labor can be based on student module, teacher module, administrator module, front-end interface, and database design
- Finding information about teachers on the college's website
- Just input student information to your own class
- Database tables can be extended on the basis of PPT
- It is possible to add features on top of PPT, and the more complete the features, the higher the score
- Make the interface more beautiful

### Role requirement description
- System interaction
- Login
- No registration required
- The administrator uses admin as the username and the password is fixed and cannot be modified
- The teacher uses the teacher ID as the username, and the password defaults to the teacher ID, which can be modified
- Students use their student ID as their username, and their password defaults to their student ID, which can be modified
- Change password
- Students
- Query
- Basic information of students
- The grades of each course chosen by the student
- Teacher
- Query
- Basic information of teachers
- Basic information of the courses taught
- Student course selection information
- The grades of all students in the course taught
- Statistical results of the grades of all students in the courses taught
- Calculate the distribution of students' grades in each score segment and draw histograms and pie charts.
- Entry
- Student's selected course grades
- Modify
- Student's selected course grades
- Delete
- Student's selected course grades
- Administrator
- Query
- Basic information of students
- Basic information of teachers
- Basic Course Information
- Entry
- Basic information of students
- Basic information of teachers
- Basic Course Information
- Professional course selection information
- Modify
- Basic information of students
- Basic information of teachers
- Basic Course Information
- Delete
- Basic information of students
- Basic information of teachers
- Basic Course Information
- Professional course selection information
### Detailed description of some requirements
-Basic information of students
    - Including student ID, name, gender, year of birth, place of origin, credits taken, number of courses selected, weighted average credits, etc; Among them, the completed course is divided into the total credits of all courses passed, and a score of 60 or above is considered as passed; Weighted average credits are weighted based on the credits of each course.
- Basic information of teachers
    - Including teacher ID, name, gender, year of birth, number of courses taught, etc.
- Basic Course Information
    - Including course number, course name, year of establishment, semester of establishment, instructor number, credits, number of selected students, average grade, etc; The average score is the arithmetic mean of all students' grades.
- Basic professional information
    - Including professional number, professional name, etc.
- Professional Course Selection Function Description
    - This system is a student grade management system, with the core function of managing student grades. However, at the same time, the system relies on the student course selection system.
    - We have added a simple course selection function, following the principle of small frequency and large batch, selecting courses based on majors. If a record of major course selection is added, all students in that major will take that course.

## Numbering Rules
- College ID: 2 digits
- Professional ID:
- College ID: 2 digits
- Major ID within the college: 2 digits
- Total: 4 digits
- Class ID:
- Year of enrollment: 4th place
- Professional code: 4 digits
- Class ID within the major: 2 digits
- Total: 10 digits
- Student ID:
- Class ID: 10 digits
- Class serial number: 2 digits
- Total: 12 digits
- Teacher ID:
- College ID: 2 digits
- College ID: 3 digits
- Total: 5 digits
- Course ID: 5 digits
- All database table IDs are stored in char, and some IDs are set to the existing maximum value of+1. Therefore, when inserting data, it is necessary to find the existing IDs in the database table, convert them to integers, take the maximum value of+1, convert them to strings, and use them as new IDs
## Database Description
Database is: MySQL
-The database username is: root, which can be found in the__ Init__ Modify in py
-The database password is asdfg13579, which can be found in the__ Init__ Modify in py

## Other configuration instructions
- Port: 6060, can be modified in __init__.py

- The access address is http://localhost:6060
- Current Running address is http://khoury-system.herokuapp.com/static/Login.html

- 127.0.0.1 cannot be used, because the hyperlink in the front page is a fixed localhost, otherwise it will cause cross-domain problems.

- The administrator's user name is admin, and the password is asdfg13579

- The initial passwords of students and teachers are numbered.

## Data flow diagram
![](imgs/数据流图.png)

## ER Diagram - Relationship Pattern
![](imgs/ER图.png)

The relationship pattern can be found in SQL/database creation script

## Integrity constraint analysis
### Entity integrity Constraints
-All primary keys cannot be empty, and all attributes defined as not null cannot be empty.
### Referential integrity constraints
- Student form: the major_id of the student form refers to the major_id of the professional form;

If a major is deleted, the cascade will delete the corresponding student;

Before inserting a student, his major must have been created;

Such a constraint should be implemented by a foreign key;

- Course schedule: the teacher_id of the course schedule refers to the teacher_id of the teacher's schedule;

If a teacher is deleted, the corresponding course will be deleted by cascadel;

Before inserting the course, its teacher must have been created;

Such a constraint should be implemented by a foreign key;

- The major_id of the professional course selection schedule refers to the major_id of the professional schedule, and the course_id of the professional course schedule refers to the course_id of the course schedule;

If a major is deleted, the cascadel will delete the corresponding major course selection information;

If a course is deleted, the cascadel will delete the corresponding professional course selection information;

Before inserting the professional course selection information, the corresponding major and course must have been created;

Such a constraint should be implemented by a foreign key;
### Custom Integrity Constraint
|Field | Constraint|
|--- | ---|
|Major_ ID | 3 digits, the newly added professional number will automatically be generated as the maximum value of the existing professional number+1
|Student_ ID | 10 digits, automatically generated. The newly added student ID consists of 4 digits for the year of enrollment, 3 digits for the major, and 3 digits for the maximum number of existing student IDs within the major of the current year+1
|Course_ ID | 5 digits, the newly added course number will automatically be generated as the maximum value of the existing course number+1
|Teacher_ ID | 5 digits, the newly added teacher ID will automatically be generated as the maximum value of the existing teacher ID+1
|Major_ Name | unique, names for different majors cannot be the same
|Sex | Value taken as' male 'or' female '
|Semester | Value taken as' spring 'or' autumn '
|All years | 4 digits
|Name, name, etc. | A string of no more than 20 characters
|Province | A string that does not exceed 20 digits
|Grade | integers between 0 and 100
|Credit | integer between 1 and 10

### Student Course Selection Table and Trigger
In fact, the student course selection information can be obtained through the student table and the professional course selection table, but due to the need to store the results, a new student course selection score table has been added;

When a record is added to the major course selection schedule, the students of the major will generate a corresponding course selection record; when a record is deleted from the professional course selection schedule, the students of the major will delete the corresponding course selection record; only the teacher can directly operate the operation of modifying the score; such a constraint should be realized by the trigger, and the trigger definition

When a record is added to the student table, the student's course selection record is automatically added according to the student's major; when a record is deleted from the student table, the student's course selection record is automatically deleted according to the student's major; such a constraint should also be implemented by the trigger, and the trigger statement is shown in the library script.

With the definition of triggers, students no longer need to set any foreign keys in the course schedule.

##Display of effect
### Login interface
- ![](imgs/登录页面.png)

### Student interface
- personal information
    - ![](imgs/学生个人信息.png)
- achievement
    - ![](imgs/学生成绩.png)
- Change password
    - ![](imgs/学生修改密码.png)

### Teacher interface
-Personal information
    - ![](imgs/教师个人信息.png)
-Course List
    - ![](imgs/教师课程列表.png)
-Course details (student list and grades)
    - ![](imgs/教师课程详情.png)
-Course score statistics
    - ![](imgs/教师课程成绩统计.png)
-Change password: same as student

### Administrator interface
- Student Information
    -List
        - ![](imgs/管理员学生列表.png)
    -Details/Modifications
        - ![](imgs/管理员学生详情.png)
    -Add
        - ![](imgs/管理员添加学生.png)
- Teacher Information
    -List
        - ![](imgs/管理员教师列表.png)
    -Details/Modifications
        - ![](imgs/管理员教师详情.png)
    -Add: Omitted
- Course Information
    -List
        - ![](imgs/管理员课程列表.png)
    -Details/Modifications
        - ![](imgs/管理员课程详情.png)
    -Add: Omitted
- Professional Information
      -List
        - ![](imgs/管理员专业列表.png)
      -Details/Modifications
        - ![](imgs/管理员专业详情.png)
      -Add: Omitted
- Professional course selection information
      -List
        - ![](imgs/管理员专业选课列表.png)
        -Details
        - ![](imgs/管理员专业选课详情.png)
      -Add
        - ![](imgs/管理员添加专业选课.png)


## Tutorial
> It is best to execute it under pychar

### Local operation

1. pip install -r requirements.txt
2. To create a database, you can use the 'Database Creation Script - Uncommented. SQL' in the SQL directory and run it directly in MySQL
3.Import test data, which is also an SQL file that can be run directly, 'System test data.sql'`
4. Configure the database for this Flask project
Modify the settings in the app directory`__ Init__ Py ` file,

```python
app.config['DATABASE_USER'] = 'django_app'  # Database account
app.config['DATABASE_PASSWORD'] = '123456'  #Password for database account
app.config['DATABASE_HOST'] = '127.0.0.1'  # Database address
app.config['DATABASE_NAME'] = 'grade_manage_system'  # Database name, it's best not to change it here. If you do, you need to change the script for creating the database
app.config['DATABASE_PORT'] = 3306  # Database Link Port
```

5. Run the`__ Init__ Py ` file
```
python __init__.py
```

### Docker operation

1. docker build -t test:1.0 .
2. docker run -itd --name test -p 6060:6060 -e SECRET_KEY=123455 -e DATABASE_USER=root -e DATABASE_PASSWORD=123456 -e DATABASE_HOST=172.17.0.1 -e DATABASE_NAME=grade_manage_system test:1.0



