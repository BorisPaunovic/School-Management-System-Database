# School Management System Database

Welcome to the School Management System Database repository! This repository contains the SQL scripts and database schema for implementing the database component of a school management system. The database is designed to store and manage various data related to students, teachers, courses, subjects, countries, and other aspects of school operations.

## Database Schema

![SMS-DB-Diagram](https://github.com/BorisPaunovic/School-Management-System-Database/assets/119711363/bff84a11-141f-4838-adaf-6022f189c2fe)

Figure 1 SMS Database Diagram


The database schema consists of the following tables:

- **Students:** Stores information about students, including their unique IDs, names, contact details, and other relevant details.
- **Teachers:** Contains information about teachers, such as their IDs, names, contact information, and other related data.
- **Courses:** Stores details about the courses offered by the school, including course IDs, names, descriptions, and other pertinent information.
- **Subjects:** Stores details about the individual subjects offered by the courses in school, including course IDs, names, descriptions, and other pertinent information.
- **Countries:** Stores the countries of students, along with other relevant data.
- **Users:** Stores information about Users of the website or app, including their unique IDs, names, contact details, and other relevant details.

And tables that connect two or more tables: StudentsCourses, CoursesSubjects, TeacherCourses.

## Setup

To set up the School Management System Database on your MS SQL Server, follow these steps:

1. Connect to your MS SQL Server using your preferred client or SQL Server Management Studio (SSMS).
2. Create a new database using the following SQL commands:

```sql
CREATE DATABASE SchoolManagementSystem;

CREATE TABLE [dbo].[Countries](
	[CountriesID] [int] IDENTITY(1,1) NOT NULL,
	[ISO] [nvarchar](10) NOT NULL,
	[CountryName] [nvarchar](100) NOT NULL,
	[PhoneCode] [int] NOT NULL,
	[ISO3] [nchar](10) NOT NULL,
	[Deleted] [bit] NULL,
 CONSTRAINT [PK_Countries] PRIMARY KEY CLUSTERED 
(
	[CountriesID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[CouresSubjects]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[CouresSubjects](
	[CoursesSubjectsID] [int] IDENTITY(1,1) NOT NULL,
	[CoursesID] [int] NOT NULL,
	[SubjectsID] [int] NOT NULL,
 CONSTRAINT [PK_CouresSubjects] PRIMARY KEY CLUSTERED 
(
	[CoursesSubjectsID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Courses]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Courses](
	[CoursesID] [int] IDENTITY(1,1) NOT NULL,
	[CoursesName] [nvarchar](50) NOT NULL,
	[CoursesDescription] [nvarchar](500) NOT NULL,
	[Deleted] [bit] NULL,
 CONSTRAINT [PK_Courses] PRIMARY KEY CLUSTERED 
(
	[CoursesID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Students]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Students](
	[StudentsID] [int] IDENTITY(1,1) NOT NULL,
	[FirstName] [nvarchar](20) NOT NULL,
	[LastName] [nvarchar](20) NULL,
	[Email] [nvarchar](50) NULL,
	[Gender] [nchar](10) NULL,
	[DateOfBirth] [datetime] NULL,
	[Adress] [nvarchar](100) NULL,
	[CountriesID] [int] NULL,
	[Deleted] [bit] NULL,
 CONSTRAINT [PK_Students] PRIMARY KEY CLUSTERED 
(
	[StudentsID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[StudentsCourses]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[StudentsCourses](
	[StudentsCoursesID] [int] IDENTITY(1,1) NOT NULL,
	[StudentsID] [int] NOT NULL,
	[CoursesID] [int] NOT NULL,
	[Passed] [bit] NULL,
	[StartDate] [datetime] NOT NULL,
 CONSTRAINT [PK_StudentsCourses] PRIMARY KEY CLUSTERED 
(
	[StudentsCoursesID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Subjects]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Subjects](
	[SubjectID] [int] IDENTITY(1,1) NOT NULL,
	[SubjectName] [nvarchar](50) NOT NULL,
	[SubjectDescription] [nvarchar](500) NOT NULL,
	[Deleted] [bit] NULL,
 CONSTRAINT [PK_Subjects] PRIMARY KEY CLUSTERED 
(
	[SubjectID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Teachers]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Teachers](
	[TeachersID] [int] IDENTITY(1,1) NOT NULL,
	[FirstName] [nvarchar](20) NOT NULL,
	[LastName] [nvarchar](20) NOT NULL,
	[Email] [nvarchar](20) NOT NULL,
	[Gender] [nvarchar](10) NOT NULL,
	[DateOfBirth] [datetime] NOT NULL,
	[Adress] [nvarchar](100) NOT NULL,
	[Deleted] [bit] NULL,
 CONSTRAINT [PK_Teachers] PRIMARY KEY CLUSTERED 
(
	[TeachersID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[TeachersCourses]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[TeachersCourses](
	[TeachersCoursesID] [int] IDENTITY(1,1) NOT NULL,
	[TeachersID] [int] NOT NULL,
	[CoursesID] [int] NOT NULL,
 CONSTRAINT [PK_TeachersCourses] PRIMARY KEY CLUSTERED 
(
	[TeachersCoursesID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Users]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Users](
	[UsersID] [int] IDENTITY(1,1) NOT NULL,
	[UserName] [nvarchar](50) NOT NULL,
	[UserPassword] [nvarchar](50) NOT NULL,
	[Administrator] [bit] NULL,
	[UserEmail] [nvarchar](50) NOT NULL,
	[Deleted] [bit] NULL,
 CONSTRAINT [PK_Users] PRIMARY KEY CLUSTERED 
(
	[UsersID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
ALTER TABLE [dbo].[Countries] ADD  CONSTRAINT [DF_Countries_Deleted]  DEFAULT ((0)) FOR [Deleted]
GO
ALTER TABLE [dbo].[Courses] ADD  CONSTRAINT [DF_Courses_Deleted]  DEFAULT ((0)) FOR [Deleted]
GO
ALTER TABLE [dbo].[Students] ADD  CONSTRAINT [DF_Students_Deleted]  DEFAULT ((0)) FOR [Deleted]
GO
ALTER TABLE [dbo].[Subjects] ADD  CONSTRAINT [DF_Subjects_Deleted]  DEFAULT ((0)) FOR [Deleted]
GO
ALTER TABLE [dbo].[Teachers] ADD  CONSTRAINT [DF_Teachers_Deleted]  DEFAULT ((0)) FOR [Deleted]
GO
ALTER TABLE [dbo].[Users] ADD  CONSTRAINT [DF_Users_Deleted]  DEFAULT ((0)) FOR [Deleted]
GO
ALTER TABLE [dbo].[CouresSubjects]  WITH CHECK ADD  CONSTRAINT [FK_CouresSubjects_Courses] FOREIGN KEY([CoursesID])
REFERENCES [dbo].[Courses] ([CoursesID])
GO
ALTER TABLE [dbo].[CouresSubjects] CHECK CONSTRAINT [FK_CouresSubjects_Courses]
GO
ALTER TABLE [dbo].[CouresSubjects]  WITH CHECK ADD  CONSTRAINT [FK_CouresSubjects_Subjects] FOREIGN KEY([SubjectsID])
REFERENCES [dbo].[Subjects] ([SubjectID])
GO
ALTER TABLE [dbo].[CouresSubjects] CHECK CONSTRAINT [FK_CouresSubjects_Subjects]
GO
ALTER TABLE [dbo].[Students]  WITH CHECK ADD  CONSTRAINT [FK_Students_Countries] FOREIGN KEY([CountriesID])
REFERENCES [dbo].[Countries] ([CountriesID])
GO
ALTER TABLE [dbo].[Students] CHECK CONSTRAINT [FK_Students_Countries]
GO
ALTER TABLE [dbo].[StudentsCourses]  WITH CHECK ADD  CONSTRAINT [FK_StudentsCourses_Courses] FOREIGN KEY([CoursesID])
REFERENCES [dbo].[Courses] ([CoursesID])
GO
ALTER TABLE [dbo].[StudentsCourses] CHECK CONSTRAINT [FK_StudentsCourses_Courses]
GO
ALTER TABLE [dbo].[StudentsCourses]  WITH CHECK ADD  CONSTRAINT [FK_StudentsCourses_Students] FOREIGN KEY([StudentsID])
REFERENCES [dbo].[Students] ([StudentsID])
GO
ALTER TABLE [dbo].[StudentsCourses] CHECK CONSTRAINT [FK_StudentsCourses_Students]
GO
ALTER TABLE [dbo].[TeachersCourses]  WITH CHECK ADD  CONSTRAINT [FK_TeachersCourses_Courses] FOREIGN KEY([CoursesID])
REFERENCES [dbo].[Courses] ([CoursesID])
GO
ALTER TABLE [dbo].[TeachersCourses] CHECK CONSTRAINT [FK_TeachersCourses_Courses]
GO
ALTER TABLE [dbo].[TeachersCourses]  WITH CHECK ADD  CONSTRAINT [FK_TeachersCourses_Teachers1] FOREIGN KEY([TeachersID])
REFERENCES [dbo].[Teachers] ([TeachersID])
GO
ALTER TABLE [dbo].[TeachersCourses] CHECK CONSTRAINT [FK_TeachersCourses_Teachers1]
GO
/****** Object:  StoredProcedure [dbo].[AddCourseSubject]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[AddCourseSubject] (@CoursesID int,@SubjectsID int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	INSERT INTO CouresSubjects(CoursesID,SubjectsID) 
	VALUES(@CoursesID,@SubjectsID)
END
GO
/****** Object:  StoredProcedure [dbo].[AddStudentCourse]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE  [dbo].[AddStudentCourse] (@StudentId int,@CourseId int,@Startdate datetime)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	INSERT INTO StudentsCourses(StudentsID,CoursesID,StartDate)
	VALUES(@StudentId,@CourseId,@Startdate)
END
GO
/****** Object:  StoredProcedure [dbo].[AddTeacherCourses]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE  [dbo].[AddTeacherCourses](@TeachersID int,@CoursesID int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	insert into TeachersCourses(TeachersID,CoursesID) values(@TeachersID,@CoursesID)
END
GO
/****** Object:  StoredProcedure [dbo].[DeleteCountry]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Boris	>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[DeleteCountry] (@CountryId int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;
	/*
   UPDATE Students 
   SET CountriesID = null WHERE CountriesID=@CountryId 
   DELETE FROM Countries WHERE CountriesID=@CountryId
   */
   
   UPDATE Countries
   SET Deleted=@CountryId
   WHERE CountriesID=@CountryId
  

END
GO
/****** Object:  StoredProcedure [dbo].[DeleteCourse]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Boris>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[DeleteCourse](@CoursesID int)
	-- Add the parameters for the stored procedure here
	 
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	/*
DELETE FROM CouresSubjects
WHERE CoursesID=@CoursesID
DELETE FROM TeachersCourses
WHERE CoursesID = @CoursesID
DELETE FROM StudentsCourses
WHERE CoursesID = @CoursesID
DELETE FROM Courses 
WHERE CoursesID = @CoursesID*/
UPDATE Courses
   SET Deleted=1
   WHERE CoursesID=@CoursesID



END
GO
/****** Object:  StoredProcedure [dbo].[DeleteStudent]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[DeleteStudent] (@StudentsID int)
	-- Add the parameters for the stored procedure here

AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;
	/*
    -- Insert statements for procedure here
	DELETE FROM dbo.StudentsCourses 
	WHERE dbo.StudentsCourses.StudentsID=@StudentsID 
	DELETE FROM Students 
	WHERE Students.StudentsID=@StudentsID
	*/
	UPDATE Students
   SET Deleted=1
   WHERE StudentsID=@StudentsID
END
GO
/****** Object:  StoredProcedure [dbo].[DeleteSubject]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[DeleteSubject](@SubjectId int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

	/*
    -- Insert statements for procedure here
	delete from CouresSubjects
where SubjectsID=@SubjectId
delete from Subjects 
where SubjectID = @SubjectId
*/
UPDATE Subjects
   SET Deleted=1
   WHERE SubjectID=@SubjectId

END
GO
/****** Object:  StoredProcedure [dbo].[DeleteTeacher]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[DeleteTeacher](@TeachersID int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;
	/*
    -- Insert statements for procedure here
	delete TeachersCourses 
	where TeachersID = @TeachersID 
	delete Teachers 
	where TeachersID = @TeachersID
	*/
	UPDATE Teachers
   SET Deleted=1
   WHERE TeachersID=@TeachersID

END
GO
/****** Object:  StoredProcedure [dbo].[DeleteUser]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[DeleteUser](@UserID int) 
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;
	/*
    -- Insert statements for procedure here
	delete  from Users where UsersID= @UserID
	*/
	UPDATE Users
   SET Deleted=1
   WHERE UsersID=@UserID
END
GO
/****** Object:  StoredProcedure [dbo].[GetUserByUsername]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[GetUserByUsername](@Username nvarchar(50)) 
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	Select Username,UserPassword,UserEmail,Administrator 
	FROM Users 
	where Username=@Username and Deleted=0
END
GO
/****** Object:  StoredProcedure [dbo].[InsertUser]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[InsertUser](@UserName nvarchar(50),@UserPassword nvarchar(50),@UserEmail nvarchar(50),@Administrator bit)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	INSERT INTO Users(UserName,UserPassword,UserEmail,Administrator)
	VALUES(@UserName,@UserPassword,@UserEmail,@Administrator)
END
GO
/****** Object:  StoredProcedure [dbo].[SaveCountry]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Boris>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SaveCountry](@ISO nvarchar(2),@CountryName nvarchar(50),@PhoneCode int,@ISO3 nvarchar(3))
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	INSERT INTO Countries(ISO,CountryName,PhoneCode,ISO3)
	VALUES(@ISO,@CountryName,@PhoneCode,@ISO3)
END
GO
/****** Object:  StoredProcedure [dbo].[SaveCourse]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SaveCourse](@CoursesName nvarchar(50),@CoursesDescription nvarchar(500))
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	INSERT INTO Courses(CoursesName,CoursesDescription)
	VALUES (@CoursesName,@CoursesDescription)
END
GO
/****** Object:  StoredProcedure [dbo].[SaveStudent]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SaveStudent](@FirstName nvarchar(50),@LastName nvarchar(50),@Email nvarchar(50),@Gender nvarchar(10),@DateOfBirth datetime,@Adress nvarchar(50),@CountriesID int) 
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	INSERT INTO Students(FirstName,LastName,Email,Gender,DateOfBirth,Adress,CountriesID) 
	VALUES(@FirstName,@LastName,@Email,@Gender,@DateOfBirth,@Adress,@CountriesID)
END
GO
/****** Object:  StoredProcedure [dbo].[SaveSubject]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SaveSubject] (@SubjectName nvarchar(50),@SubjectDescription nvarchar (500))
	-- Add the parameters for the stored procedure here


AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	insert into Subjects(SubjectName,SubjectDescription) values(@SubjectName,@SubjectDescription)
END
GO
/****** Object:  StoredProcedure [dbo].[SaveTeacher]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SaveTeacher](@FirstName nvarchar(50),@LastName nvarchar(50),@Email nvarchar(50),@Gender nvarchar (10),@DateOfBirth datetime,@Adress nvarchar(50))
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	insert into Teachers(FirstName,LastName,Email,Gender,DateOfBirth,Adress)
	values(@FirstName,@LastName,@Email,@Gender,@DateOfBirth,@Adress)
END
GO
/****** Object:  StoredProcedure [dbo].[SelectAllCountryes]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Boris>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectAllCountryes] 
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    select countriesid,CountryName,ISO,iso3,PhoneCode,Deleted from Countries where Deleted=0
END
GO
/****** Object:  StoredProcedure [dbo].[SelectAllCourses]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE  [dbo].[SelectAllCourses]
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	SELECT CoursesID,CoursesName,CoursesDescription,Deleted FROM Courses where Deleted=0
END
GO
/****** Object:  StoredProcedure [dbo].[SelectAllCoursesSubjects]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectAllCoursesSubjects]
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	SELECT CoursesSubjectsID,CoursesID,SubjectsID FROM CouresSubjects
END
GO
/****** Object:  StoredProcedure [dbo].[SelectAllStudentsResault]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectAllStudentsResault]
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	SELECT S.StudentsID ,S.FirstName,S.LastName,S.Email,s.Gender,s.DateOfBirth,s.Adress,C.CoursesName,SC.Passed,SC.StartDate,C.CoursesDescription,Co.CountryName
	FROM Students AS S 
	left join StudentsCourses AS SC ON S.StudentsID=SC.StudentsID 
	left join Courses AS C ON SC.CoursesID=C.CoursesID
	left join Countries AS Co ON S.CountriesID=Co.CountriesID
	where s.Deleted=0 and c.Deleted=0 
END

GO
/****** Object:  StoredProcedure [dbo].[SelectAllSubjects]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectAllSubjects]
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	select SubjectID,SubjectName,SubjectDescription,Deleted
	from Subjects
	where Deleted=0
END
GO
/****** Object:  StoredProcedure [dbo].[SelectAllTeachersJoinCourses]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectAllTeachersJoinCourses]
	-- Add the parameters for the stored procedure here

AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	select T.TeachersID,T.FirstName,T.LastName,T.Email,T.Gender,T.DateOfBirth,T.Adress,TC.TeachersCoursesID,C.CoursesID,C.CoursesName,C.CoursesDescription 
	from Teachers as T
	left join TeachersCourses as TC on t.TeachersID= TC.TeachersID
	left join Courses as C on TC.CoursesID= C.CoursesID  
	where C.Deleted=0 and T.Deleted=0
END
GO
/****** Object:  StoredProcedure [dbo].[SelectAllUsers]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectAllUsers] 
	-- Add the parameters for the stored procedure here
	

AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	SELECT UsersID,UserName,UserEmail,UserPassword,Administrator,Deleted 
	FROM Users
	where Deleted=0
END
GO
/****** Object:  StoredProcedure [dbo].[SelectCountryByName]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Boris Paunovic>
-- Create date: <Create Date,,>
-- Description:	<Description,, Selects country by name>
-- =============================================
CREATE PROCEDURE [dbo].[SelectCountryByName](@CountryName nvarchar(50))
	-- Add the parameters for the stored procedure here
	--select CountriesID from Countries where CountryName = @CountryName
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	select CountriesID from Countries where CountryName = @CountryName and Deleted=0
END
GO
/****** Object:  StoredProcedure [dbo].[SelectCourseByName]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectCourseByName](@CoursesName nvarchar(50))
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	SELECT CoursesID,CoursesName,CoursesDescription 
	FROM Courses
	WHERE CoursesName=@CoursesName and Deleted=0
END
GO
/****** Object:  StoredProcedure [dbo].[SelectCoursesSubjectsById]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectCoursesSubjectsById] (@CoursesID int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	SELECT CoursesSubjectsID,CoursesID,SubjectsID
	FROM CouresSubjects 
	WHERE CoursesID=@CoursesID
END
GO
/****** Object:  StoredProcedure [dbo].[SelectLastStudent]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectLastStudent]
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	SELECT top 1 StudentsID,FirstName,LastName,Email,Gender,DateOfBirth,Adress,CountriesID 
	FROM Students  
	where Deleted=0
	ORDER BY StudentsID DESC
END
GO
/****** Object:  StoredProcedure [dbo].[SelectStudentByName]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectStudentByName](@FirstName nvarchar(50))
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	select StudentsID,FirstName,LastName,Email,Gender,DateOfBirth,Adress,CountriesID
	from Students 
	where FirstName=@FirstName and Deleted=0
END
GO
/****** Object:  StoredProcedure [dbo].[SelectSubjectByName]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectSubjectByName](@SubjectName nvarchar(50))
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	select SubjectID,SubjectDescription,SubjectName
	from Subjects
	where SubjectName=@SubjectName and Deleted=0
END
GO
/****** Object:  StoredProcedure [dbo].[SelectTeacherByName]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[SelectTeacherByName](@FirstName nvarchar(50))
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	 select TeachersID,FirstName,LastName,Email,Gender,DateOfBirth,Adress
	 from Teachers
	 where FirstName = @FirstName
END
GO
/****** Object:  StoredProcedure [dbo].[UpdateCountry]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[UpdateCountry](@CountryName nvarchar(50),@ISO nvarchar(5),@ISO3 nvarchar(5), @PhoneCode int ,@CountriesID int) 
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	UPDATE Countries 
	SET CountryName = @CountryName, ISO = @ISO,ISO3 = @ISO3, PhoneCode = @PhoneCode
	WHERE CountriesID = @CountriesID
END

GO
/****** Object:  StoredProcedure [dbo].[UpdateCourse]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Boris>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[UpdateCourse](@CourseName nvarchar(50),@CoursesDescription nvarchar (500),@CourseID int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	UPDATE Courses
	SET CoursesName=@CourseName , CoursesDescription=@CoursesDescription 
	WHERE CoursesID=@CourseID
END
GO
/****** Object:  StoredProcedure [dbo].[UpdateCourseSubject]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE  [dbo].[UpdateCourseSubject](@SubjectsID int,@CoursesSubjectsID int,@CoursesID int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	update CouresSubjects 
	set SubjectsID=@SubjectsID 
	where CoursesSubjectsID=@CoursesSubjectsID and CoursesID=@CoursesID
END
GO
/****** Object:  StoredProcedure [dbo].[UpdateCourseSubjects2]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[UpdateCourseSubjects2](@SubjectsID int,@CoursesID int,@CoursesSubjectsID int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	update CouresSubjects
	set SubjectsID=@SubjectsID
	where CoursesSubjectsID=@CoursesSubjectsID and CoursesID=@CoursesID
END
GO
/****** Object:  StoredProcedure [dbo].[UpdateStudent]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[UpdateStudent](@FirstName nvarchar(50),@LastName nvarchar(50),@Email nvarchar(50),@Gender nvarchar(10),@DateOfBirth datetime,@Adress nvarchar(100),@CountriesID int,@StudentsId int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	Update Students
	SET FirstName=@FirstName,LastName=@LastName,Email=@Email,Gender=@Gender,DateOfBirth=@DateOfBirth,Adress=@Adress,CountriesID=@CountriesID
	WHERE StudentsID=@StudentsId
END
GO
/****** Object:  StoredProcedure [dbo].[UpdateStudentCourse]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[UpdateStudentCourse](@CoursesID int,@Passed bit,@StudentsID int,@CourseIDFromGrid int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	UPDATE StudentsCourses 
	SET CoursesID=@CoursesID,Passed=@Passed
	WHERE StudentsID=@StudentsID AND CoursesID=@CourseIDFromGrid
END
GO
/****** Object:  StoredProcedure [dbo].[UpdateSubject]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[UpdateSubject] (@SubjectName nvarchar(50),@SubjectDescription nvarchar(500),@SubjectID int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	update Subjects
	set SubjectName=@SubjectName,SubjectDescription=@SubjectDescription
	where SubjectID=@SubjectID
END
GO
/****** Object:  StoredProcedure [dbo].[UpdateTeacher]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[UpdateTeacher](@FirstName nvarchar(50),@LastName nvarchar(50),@Adress nvarchar(100),@Email nvarchar(50),@DateOfBirth datetime,@Gender nvarchar(10),@TeachersId int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	update Teachers 
	set FirstName=@FirstName,LastName=@LastName,Adress=@Adress,Email=@Email,DateOfBirth=@DateOfBirth,Gender=@Gender
	where TeachersID= @TeachersId
END
GO
/****** Object:  StoredProcedure [dbo].[UpdateTeachersCourses]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[UpdateTeachersCourses](@CoursesId int,@TeachersCoursesId int,@TeachersId int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	update TeachersCourses 
	set CoursesID=@CoursesId
	where TeachersCoursesID=@TeachersCoursesId and TeachersID=@TeachersId
END
GO
/****** Object:  StoredProcedure [dbo].[UpdateUser]    Script Date: 29.1.2022. 01:47:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
CREATE PROCEDURE [dbo].[UpdateUser](@Administrator bit,@UserId int)
	-- Add the parameters for the stored procedure here
	
AS
BEGIN
	-- SET NOCOUNT ON added to prevent extra result sets from
	-- interfering with SELECT statements.
	SET NOCOUNT ON;

    -- Insert statements for procedure here
	update Users set Administrator=@Administrator where Usersid=@UserId 
END

```
If you have any questions, suggestions, or feedback, please feel free to reach out. You can contact the project maintainers by opening an issue on the repository.

Thank you for your interest in the School Management System Database project. We hope it proves to be a valuable resource for implementing the database component of your school management system!

Execute the SQL scripts in the scripts folder in the following order:  
- create_tables.sql: Creates the necessary tables in the database.
- create_indexes.sql: Creates indexes for optimized querying and performance.
- create_constraints.sql: Sets up the necessary constraints for data integrity.
- create_views.sql: Defines views for easier data retrieval and reporting.
- create_procedures.sql: Creates stored procedures for various database operations.


The database is now set up and ready to be used by the School Management System application.

Or just restore the database from the .bak file.
Contributing

Contributions to the School Management System Database project are welcome. If you would like to contribute, please follow these guidelines:

   - Fork the repository and create your branch: git checkout -b your-branch-name
   - Make your changes and ensure they follow the project's coding conventions.
   - Test your changes thoroughly to ensure they don't introduce any issues.
   - Commit your changes: git commit -m "Your commit message"
   - Push to the branch: git push origin your-branch-name
   - Open a pull request, describing your changes and their purpose.

## License

The School Management System Database project is released under the MIT License. You are free to use, modify, and distribute the database schema and SQL scripts according to the terms of the license.
Contact

If you have any questions, suggestions, or feedback, please feel free to reach out. You can contact the project maintainers by opening an issue on the repository.

Thank you for your interest in the School Management System Database project. We hope it proves to be a valuable resource for implementing the database component of your school management system!




