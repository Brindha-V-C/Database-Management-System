-- Create the User table
-- This table has no foreign keys, so it can be created first.
CREATE TABLE User (
    UserID INT PRIMARY KEY,
    FirstName VARCHAR(100),
    LastName VARCHAR(100),
    Email VARCHAR(255)
);

-- Create the Company table
-- Also has no foreign keys.
CREATE TABLE Company (
    CompanyID INT PRIMARY KEY,
    CompanyName VARCHAR(255),
    Industry VARCHAR(100)
);

-- Create the Skill table
-- This is our "dictionary" of skills, with no dependencies.
CREATE TABLE Skill (
    SkillID INT PRIMARY KEY,
    SkillName VARCHAR(100)
);

-- Create the Post table
-- This table has a foreign key that REFERENCES the User table.
CREATE TABLE Post (
    PostID INT PRIMARY KEY,
    PostContent TEXT,
    Timestamp DATETIME,
    UserID INT,
    FOREIGN KEY (UserID) REFERENCES User(UserID)
);

-- Create the Experience table
-- This links User and Company, so it has two foreign keys.
CREATE TABLE Experience (
    ExperienceID INT PRIMARY KEY,
    JobTitle VARCHAR(255),
    StartDate DATE,
    EndDate DATE,
    UserID INT,
    CompanyID INT,
    FOREIGN KEY (UserID) REFERENCES User(UserID),
    FOREIGN KEY (CompanyID) REFERENCES Company(CompanyID)
);

-- Create the User_Skill linking table
-- This table's only job is to connect Users and Skills, resolving our many-to-many relationship.
-- Its primary key is a combination of both foreign keys to ensure a user can't have the same skill twice.
CREATE TABLE User_Skill (
    UserID INT,
    SkillID INT,
    PRIMARY KEY (UserID, SkillID),
    FOREIGN KEY (UserID) REFERENCES User(UserID),
    FOREIGN KEY (SkillID) REFERENCES Skill(SkillID)
);

-- Create the Education table
-- This has a foreign key that REFERENCES the User table.
CREATE TABLE Education (
    EducationID INT PRIMARY KEY,
    SchoolName VARCHAR(255),
    Degree VARCHAR(150),
    StartDate DATE,
    EndDate DATE,
    UserID INT,
    FOREIGN KEY (UserID) REFERENCES User(UserID)
);

-- Create the Job table
-- This has a foreign key that REFERENCES the Company table.
CREATE TABLE Job (
    JobID INT PRIMARY KEY,
    JobTitle VARCHAR(255),
    JobDescription TEXT,
    CompanyID INT,
    FOREIGN KEY (CompanyID) REFERENCES Company(CompanyID)
);

-- Create the Message table
-- This is interesting because it REFERENCES the User table twice.
CREATE TABLE Message (
    MessageID INT PRIMARY KEY,
    MessageContent TEXT,
    Timestamp DATETIME,
    SenderID INT,
    RecipientID INT,
    FOREIGN KEY (SenderID) REFERENCES User(UserID),
    FOREIGN KEY (RecipientID) REFERENCES User(UserID)
);

-- Create the Comment table
-- A linking table that connects a User and a Post and also holds data (the comment text).
CREATE TABLE Comment (
    CommentID INT PRIMARY KEY,
    CommentText TEXT,
    Timestamp DATETIME,
    UserID INT,
    PostID INT,
    FOREIGN KEY (UserID) REFERENCES User(UserID),
    FOREIGN KEY (PostID) REFERENCES Post(PostID)
);

-- Create the Like table
-- Another linking table, but simpler since a 'like' has no extra data.
CREATE TABLE `Like` (
    LikeID INT PRIMARY KEY,
    Timestamp DATETIME,
    UserID INT,
    PostID INT,
    FOREIGN KEY (UserID) REFERENCES User(UserID),
    FOREIGN KEY (PostID) REFERENCES Post(PostID)
);
