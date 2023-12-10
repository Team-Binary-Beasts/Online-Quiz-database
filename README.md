# 🔸Online-Quiz-database
An Online quiz database project for education, built with SQL Server.

# 🔸Diagram
![Database Diagram](https://github.com/Team-Binary-Beasts/Online-Quiz-database/assets/93474063/7ca2e17b-14a2-4db0-a7b3-879053ea62b9)

# 🔸Entitys

## Person
- **ID**: INT (Primary Key, Identity)
- **FirstName**: NVARCHAR(50) NOT NULL
- **LastName**: NVARCHAR(50) NOT NULL
- **SSN**: NVARCHAR(10) NOT NULL

## Exam
- **ID**: INT (Primary Key, Identity)
- **Title**: NVARCHAR(100) NOT NULL
- **CreatedAt**: DATETIME DEFAULT(GETDATE()) NOT NULL

## Course
- **ID**: INT (Primary Key, Identity)
- **Title**: NVARCHAR(100) NOT NULL

## Question
- **ID**: INT (Primary Key, Identity)
- **CourseID**: INT (Foreign Key references Course(ID)) NOT NULL
- **Body**: NVARCHAR(100) NOT NULL

## Answer
- **ID**: INT (Primary Key, Identity)
- **Body**: NVARCHAR(100) NOT NULL

## Point
- **ID**: INT (Primary Key, Identity)
- **ExamID**: INT (Foreign Key references Exam(ID)) NOT NULL
- **PersonID**: INT (Foreign Key references Person(ID)) NOT NULL
- **CourseID**: INT (Foreign Key references Course(ID)) NOT NULL
- **TotalPoint**: INT NOT NULL
- **CreatedAt**: DATETIME DEFAULT(GETDATE()) NOT NULL

## Exam_Course
- **ID**: INT (Primary Key, Identity)
- **ExamID**: INT (Foreign Key references Exam(ID)) NOT NULL
- **CourseID**: INT (Foreign Key references Course(ID)) NOT NULL

## Question_Answer
- **ID**: INT (Primary Key, Identity)
- **AnswerID**: INT (Foreign Key references Answer(ID)) NOT NULL
- **QuestionID**: INT (Foreign Key references Question(ID)) NOT NULL
- **IsCorrectAnswer**: BIT NOT NULL DEFAULT(0)

## Exam_Person
- **ID**: INT (Primary Key, Identity)
- **ExamID**: INT (Foreign Key references Exam(ID)) NOT NULL
- **PersonID**: INT (Foreign Key references Person(ID)) NOT NULL

