
--Database: SELECTsquad 



--Person
CREATE TABLE Person (
  EmployeeID INT PRIMARY KEY,
  Name NVARCHAR(100),
  Birthdate DATE,
  Race NVARCHAR(50),
  Gender NVARCHAR(10)
);
 
--Degree
CREATE TABLE Degree (
  DegreeID INT PRIMARY KEY,
  DegreeType NVARCHAR(100),
  FieldOfStudy NVARCHAR(100)
);

--Training
CREATE TABLE Training (
  TrainingID INT PRIMARY KEY,
  TrainingName NVARCHAR(100),
  TrainingType NVARCHAR(100)
);

--Occupation Category
CREATE TABLE OccupationCategory (
  OccupationID INT PRIMARY KEY,
  OccupationName NVARCHAR(100),
  OccupationCode NVARCHAR(20)  -- e.g. “11-1021”
);

--Employer
CREATE TABLE Employer (
  EmployerID INT PRIMARY KEY,
  EmployerName NVARCHAR(100),
  Industry NVARCHAR(100)
);

--Job
CREATE TABLE JobCategory (
  JobID NVARCHAR(20) PRIMARY KEY,
  JobTitle NVARCHAR(255),
  EmployedCount2023 INT,
  EmployedCount2033 INT,
  MarketDistribution2033 DECIMAL(5,2),    -- % share of market in 2033
  EmployDistribution2023 DECIMAL(5,2),    -- % distribution in 2023
  EmployDistribution2033 DECIMAL(5,2),    -- % distribution in 2033
  SelfEmployment2023 DECIMAL(5,2),        -- % self-employed in 2023
  OpeningsAvg INT,                        -- avg annual openings
  MedianSalary DECIMAL(10,2)              -- median annual wage
);

--PersonJob (links Person to Job)
CREATE TABLE PersonJob (
  JobID       NVARCHAR(20),
  EmployeeID  INT,
  YearsExp    INT,
  StartDate   DATE,
  PRIMARY KEY (JobID, EmployeeID),
  CONSTRAINT FK_PersonJob_Job
    FOREIGN KEY (JobID) REFERENCES JobCategory(JobID)
      ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT FK_PersonJob_Person
    FOREIGN KEY (EmployeeID) REFERENCES Person(EmployeeID)
      ON DELETE CASCADE ON UPDATE CASCADE
);

--PersonDegree (links Person to Degree)
CREATE TABLE PersonDegree (
  DegreeID    INT,
  EmployeeID  INT,
  GraduateDate DATE,
  DegreeAmt   NVARCHAR(100),
  PRIMARY KEY (DegreeID, EmployeeID),
  CONSTRAINT FK_PersonDegree_Degree
    FOREIGN KEY (DegreeID) REFERENCES Degree(DegreeID)
      ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT FK_PersonDegree_Person
    FOREIGN KEY (EmployeeID) REFERENCES Person(EmployeeID)
      ON DELETE CASCADE ON UPDATE CASCADE
);

--PersonTraining (links Person to Training)
CREATE TABLE PersonTraining (
  TrainingID      INT,
  EmployeeID      INT,
  TrainingDate    DATE,
  CompletionStatus NVARCHAR(50),
  PRIMARY KEY (TrainingID, EmployeeID),
  CONSTRAINT FK_PersonTraining_Training
    FOREIGN KEY (TrainingID) REFERENCES Training(TrainingID)
      ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT FK_PersonTraining_Person
    FOREIGN KEY (EmployeeID) REFERENCES Person(EmployeeID)
      ON DELETE CASCADE ON UPDATE CASCADE
);

--JobDegreeRequirement (links Job to Degree)
CREATE TABLE JobDegreeRequirement (
  JobID    NVARCHAR(20),
  DegreeID INT,
  PRIMARY KEY (JobID, DegreeID),
  CONSTRAINT FK_JobDegreeRequirement_Job
    FOREIGN KEY (JobID) REFERENCES JobCategory(JobID)
      ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT FK_JobDegreeRequirement_Degree
    FOREIGN KEY (DegreeID) REFERENCES Degree(DegreeID)
      ON DELETE CASCADE ON UPDATE CASCADE
);

--JobTrainingRequirement (links Job to Training)
CREATE TABLE JobTrainingRequirement (
  JobID      NVARCHAR(20),
  TrainingID INT,
  PRIMARY KEY (JobID, TrainingID),
  CONSTRAINT FK_JobTrainingRequirement_Job
    FOREIGN KEY (JobID) REFERENCES JobCategory(JobID)
      ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT FK_JobTrainingRequirement_Training
    FOREIGN KEY (TrainingID) REFERENCES Training(TrainingID)
      ON DELETE CASCADE ON UPDATE CASCADE
);

--EmployerTraining (links Employer to Training)
CREATE TABLE EmployerTraining (
  TrainingID INT,
  EmployerID INT,
  PRIMARY KEY (TrainingID, EmployerID),
  CONSTRAINT FK_EmployerTraining_Training
    FOREIGN KEY (TrainingID) REFERENCES Training(TrainingID)
      ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT FK_EmployerTraining_Employer
    FOREIGN KEY (EmployerID) REFERENCES Employer(EmployerID)
      ON DELETE CASCADE ON UPDATE CASCADE
);

--JobPosting (links postings back to Job)
CREATE TABLE JobPosting (
  PostingID   INT PRIMARY KEY,
  JobID       NVARCHAR(20),
  Status      NVARCHAR(50),
  PostingDate DATE,
  CONSTRAINT FK_JobPosting_Job
    FOREIGN KEY (JobID) REFERENCES JobCategory(JobID)
      ON DELETE CASCADE ON UPDATE CASCADE
);

--OccupationCategoryTraining (links OccupationCategory to Training)
CREATE TABLE OccupationCategoryTraining (
  OccupationID INT,
  TrainingID   INT,
  PRIMARY KEY (OccupationID, TrainingID),
  CONSTRAINT FK_OccCatTraining_OccCategory
    FOREIGN KEY (OccupationID) REFERENCES OccupationCategory(OccupationID)
      ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT FK_OccCatTraining_Training
    FOREIGN KEY (TrainingID) REFERENCES Training(TrainingID)
      ON DELETE CASCADE ON UPDATE CASCADE
);
































-- Generative AI Insert Statements with Realistic Fake Data

-- 2.1) OccupationCategory (added 19–21)
INSERT INTO OccupationCategory (OccupationID, OccupationName, OccupationCode) VALUES
  (1,  'Registered Nurses',                         '29-1141'),
  (2,  'Software Developers',                       '15-1252'),
  (3,  'Elementary School Teachers',                '25-2021'),
  (4,  'Accountants and Auditors',                  '13-2011'),
  (5,  'Management Analysts',                       '13-1111'),
  (6,  'Dental Assistants',                         '31-9091'),
  (7,  'Marketing Managers',                        '11-2021'),
  (8,  'Data Scientists',                           '15-2041'),
  (9,  'Police and Sheriff''s Patrol Officers',     '33-3051'),
  (10, 'Civil Engineers',                           '17-2051'),
  (11, 'Chefs and Head Cooks',                      '35-1011'),
  (12, 'Graphic Designers',                         '27-1024'),
  (13, 'Human Resources Specialists',               '13-1071'),
  (14, 'Medical and Health Services Managers',      '11-9111'),
  (15, 'Market Research Analysts & Marketing Specialists','13-1161'),
  (16, 'Financial Managers',                        '11-3031'),
  (17, 'Construction Managers',                     '11-9021'),
  (18, 'Physicians and Surgeons',                   '29-1069'),
  (19, 'Software Quality Assurance Analysts',       '15-1253'),
  (20, 'Registered Dietitians & Nutritionists',     '29-1031'),
  (21, 'Physical Therapists',                       '29-1123');

-- 2.2) Employer (added 19–21)
INSERT INTO Employer (EmployerID, EmployerName, Industry) VALUES
  (1,  'General Hospital',             'Healthcare'),
  (2,  'TechSoft Inc.',                'Information Technology'),
  (3,  'Sunnyvale School District',    'Education'),
  (4,  'Greenwood Accounting LLC',     'Finance & Insurance'),
  (5,  'Metro Consulting Group',       'Management Consulting'),
  (6,  'Bright Smiles Dental',         'Healthcare'),
  (7,  'City Police Department',       'Public Safety'),
  (8,  'DataCorp Analytics',           'Information Technology'),
  (9,  'Sunnyvale City Government',    'Government'),
  (10, 'Culinary Delights Restaurant','Hospitality'),
  (11, 'Creative Studios LLC',         'Design Services'),
  (12, 'Washington State Hospital',    'Healthcare'),
  (13, 'HR Solutions Inc.',            'Human Resources'),
  (14, 'HealthWorks Management',       'Healthcare Administration'),
  (15, 'Market Insights LLC',          'Market Research'),
  (16, 'First Financial Bank',         'Banking & Finance'),
  (17, 'BuildRight Construction Co.',  'Construction'),
  (18, 'Metro Medical Center',         'Healthcare'),
  (19, 'Quality Assurance Inc.',       'Software'),
  (20, 'HealthyLife Nutrition Center', 'Healthcare'),
  (21, 'MotionWorks Physical Therapy', 'Healthcare');

-- 2.3) Degree (added 16–18)
INSERT INTO Degree (DegreeID, DegreeType, FieldOfStudy) VALUES
  (1,  'High School Diploma',    'General Education'),
  (2,  'Associate',              'Nursing'),
  (3,  'Bachelor',               'Nursing'),
  (4,  'Bachelor',               'Computer Science'),
  (5,  'Bachelor',               'Education'),
  (6,  'Master',                 'Business Administration'),
  (7,  'Bachelor',               'Accounting'),
  (8,  'Bachelor',               'Management'),
  (9,  'Diploma',                'Dental Assisting'),
  (10, 'Doctorate',              'Biological Sciences'),
  (11, 'Certificate',            'Information Security'),
  (12, 'Doctorate',              'Education'),
  (13, 'Bachelor',               'Marketing'),
  (14, 'Bachelor',               'Civil Engineering'),
  (15, 'Doctorate',              'Medicine'),
  (16, 'Bachelor',               'Psychology'),
  (17, 'Bachelor',               'Nutrition'),
  (18, 'Doctorate',              'Physical Therapy');

-- 2.4) Training (added 16–18)
INSERT INTO Training (TrainingID, TrainingName, TrainingType) VALUES
  (1,  'CPR Certification',                       'Healthcare Certification'),
  (2,  'Basic Life Support (BLS)',                'Healthcare Certification'),
  (3,  'AWS Cloud Practitioner',                  'IT Certification'),
  (4,  'Pediatric First Aid',                     'Healthcare Certification'),
  (5,  'Classroom Management 101',                'Education Workshop'),
  (6,  'QuickBooks Pro Training',                 'Finance Software'),
  (7,  'Lean Six Sigma Yellow Belt',              'Consulting Skill'),
  (8,  'Dental Radiography Course',               'Dental Certification'),
  (9,  'Pediatric Dentistry Basics',              'Dental Certification'),
  (10, 'Information Security Fundamentals',       'IT Certification'),
  (11, 'Civil Engineering Basics',                'Engineering Workshop'),
  (12, 'Marketing Analytics Workshop',            'Business Workshop'),
  (13, 'Human Resources Management Seminar',      'HR Workshop'),
  (14, 'Advanced Clinical Management',            'Healthcare Administration'),
  (15, 'Medical Ethics and Law',                  'Healthcare Workshop'),
  (16, 'Software Testing Fundamentals',           'IT Certification'),
  (17, 'Nutrition & Dietetics Certification',     'Healthcare Certification'),
  (18, 'Physical Therapy Techniques',             'Healthcare Certification');

-- 2.6) Person (added 21–25)
INSERT INTO Person (EmployeeID, Name, Birthdate, Race, Gender) VALUES
  (1,  'Alice Johnson',    '1989-05-14', 'White',           'Female'),
  (2,  'Brian Martinez',   '1978-11-02', 'Hispanic',        'Male'),
  (3,  'Catherine Wu',     '1995-07-21', 'Asian',           'Female'),
  (4,  'Diego Lopez',      '1992-03-30', 'Hispanic',        'Male'),
  (5,  'Fatima Ahmed',     '1985-12-05', 'Middle Eastern',  'Female'),
  (6,  'Gregory Smith',    '2000-01-19', 'Black',           'Male'),
  (7,  'Hannah Thompson',  '1990-08-10', 'White',           'Female'),
  (8,  'Ian Patel',        '1993-04-27', 'Asian',           'Male'),
  (9,  'Julia Kim',        '1987-02-16', 'Asian',           'Female'),
  (10, 'Kevin O''Connor',  '1975-09-08', 'White',           'Male'),
  (11, 'Emma Brown',       '1998-11-23', 'White',           'Female'),
  (12, 'Michael Chen',     '1982-07-05', 'Asian',           'Male'),
  (13, 'Sara Davis',       '1990-02-14', 'Black',           'Female'),
  (14, 'Omar Hassan',      '1987-09-30', 'Middle Eastern',  'Male'),
  (15, 'Laura Lee',        '1995-12-11', 'Asian',           'Female'),
  (16, 'Kevin White',      '1991-04-18', 'White',           'Male'),
  (17, 'Olivia Green',     '1994-08-22', 'Hispanic',        'Female'),
  (18, 'Liam Scott',       '1988-12-02', 'Black',           'Male'),
  (19, 'Sophia Turner',    '1992-03-11', 'Asian',           'Female'),
  (20, 'Noah Martinez',    '1985-06-30', 'Hispanic',        'Male'),
  (21, 'Chloe Adams',      '1993-05-17', 'White',           'Female'),
  (22, 'Ethan Roberts',    '1986-08-04', 'Black',           'Male'),
  (23, 'Mia Wilson',       '1991-11-28', 'Asian',           'Female'),
  (24, 'Noah Scott',       '1989-02-21', 'White',           'Male'),
  (25, 'Ava Martinez',     '1996-07-30', 'Hispanic',        'Female');

-- 2.7) PersonDegree (added for 21–25)
INSERT INTO PersonDegree (DegreeID, EmployeeID, GraduateDate, DegreeAmt) VALUES
  (3,  1,  '2011-05-20', 'BSN, Cum. GPA 3.6'),
  (2,  2,  '2000-05-15', 'ADN, Cum. GPA 3.4'),
  (4,  3,  '2017-05-15', 'BSCS, Cum. GPA 3.9'),
  (5,  7,  '2012-05-20', 'BSEd, Cum. GPA 3.3'),
  (7,  4,  '2008-05-10', 'BBA (Accounting), Cum. GPA 3.5'),
  (8,  5,  '2010-05-25', 'BBA (Management), Cum. GPA 3.7'),
  (9,  9,  '2009-11-01', 'Dental Diploma, Score: 89%'),
  (10, 16, '2014-05-16', 'PhD in Biological Sciences, Cum. GPA 4.0'),
  (11, 17, '2016-06-20', 'Certificate in Cybersecurity, Score: 95%'),
  (14, 18, '2012-06-10', 'BS in Civil Engineering, Cum. GPA 3.6'),
  (15, 19, '2018-05-25', 'MD in General Medicine, Cum. GPA 3.7'),
  (6,  20, '2010-12-12', 'MBA, Cum. GPA 3.8'),
  (16, 21, '2015-05-22', 'BA in Psychology, Cum. GPA 3.5'),
  (17, 22, '2013-05-18', 'BA in Nutrition, Cum. GPA 3.7'),
  (18, 23, '2020-11-10', 'DPT in Physical Therapy, Cum. GPA 3.9'),
  (4,  24, '2015-05-16', 'BSCS, Cum. GPA 3.4'),
  (13, 25, '2019-05-22', 'BA in Marketing, Cum. GPA 3.6');

-- 2.8) PersonTraining (added for 21–25)
INSERT INTO PersonTraining (TrainingID, EmployeeID, TrainingDate, CompletionStatus) VALUES
  (1,  1,  '2022-03-10', 'Completed'),
  (2,  1,  '2023-07-10', 'Completed'),
  (3,  3,  '2021-09-05', 'Completed'),
  (5,  7,  '2013-02-20', 'Completed'),
  (6,  4,  '2009-04-12', 'Completed'),
  (8,  9,  '2010-09-15', 'Completed'),
  (9,  9,  '2011-01-05', 'Completed'),
  (7,  5,  '2011-10-10', 'Completed'),
  (3, 11,  '2021-08-01', 'Completed'),
  (6, 12,  '2006-02-14', 'Completed'),
  (7, 13,  '2016-07-30', 'Completed'),
  (5, 14,  '2010-03-18', 'Completed'),
  (9, 15,  '2017-01-10', 'Completed'),
  (10,16,  '2015-09-11', 'Completed'),
  (11,17,  '2018-04-22', 'Completed'),
  (13,18,  '2013-11-30', 'Completed'),
  (14,19,  '2019-08-05', 'Completed'),
  (15,20,  '2011-12-01', 'Completed'),
  (16,21,  '2016-06-10', 'Completed'),
  (17,22,  '2014-10-15', 'Completed'),
  (18,23,  '2021-02-20', 'Completed'),
  (4, 24,  '2017-05-12', 'Completed'),
  (13,25,  '2020-09-25', 'Completed');

-- 2.9) PersonJob (added for 21–25)
INSERT INTO PersonJob (JobID, EmployeeID, YearsExp, StartDate) VALUES
  ('29-1141',  1,  3,  '2021-01-15'),
  ('15-1252',  3,  1,  '2022-06-01'),
  ('25-2021',  7,  5,  '2018-08-10'),
  ('13-2011',  4, 10,  '2013-04-01'),
  ('13-1111',  5,  8,  '2015-03-20'),
  ('31-9091',  9,  2,  '2022-11-01'),
  ('15-1252',11,   2,  '2021-03-05'),
  ('13-2011',12,  12,  '2009-07-10'),
  ('13-1111',13,  4,  '2017-09-01'),
  ('25-2021',14,  9,  '2011-01-20'),
  ('31-9091',15,  3,  '2019-11-25'),
  ('11-2021',16,  5,  '2017-02-12'),
  ('15-2041',17,  3,  '2019-05-10'),
  ('33-3051',18,  7,  '2014-08-01'),
  ('17-2051',19,  12,  '2008-04-15'),
  ('35-1011',20,  4,  '2016-09-30'),
  ('15-1253',21,  2,  '2022-01-05'),
  ('29-1031',22,  6,  '2015-03-22'),
  ('29-1123',23,  8,  '2013-07-18'),
  ('13-1071',24,  4,  '2018-11-12'),
  ('15-2041',25,  1,  '2024-02-01');

-- 2.10) JobDegreeRequirement (same)
INSERT INTO JobDegreeRequirement (JobID, DegreeID) VALUES
  ('29-1141', 2), 
  ('29-1141', 3),
  ('15-1252', 4),
  ('25-2021', 5),
  ('13-2011', 7),
  ('13-1111', 6),
  ('31-9091', 9);

-- 2.11) JobTrainingRequirement (same)
INSERT INTO JobTrainingRequirement (JobID, TrainingID) VALUES
  ('29-1141', 1), 
  ('29-1141', 2),
  ('25-2021', 5),
  ('13-2011', 6),
  ('13-1111', 7),
  ('31-9091', 8), 
  ('31-9091', 9);

-- 2.12) EmployerTraining (same)
INSERT INTO EmployerTraining (TrainingID, EmployerID) VALUES
  (1,  1), 
  (2,  1),
  (8,  6), 
  (9,  6),
  (6,  4), 
  (5,  3),
  (7,  5);

-- 2.13) OccupationCategoryTraining (same)
INSERT INTO OccupationCategoryTraining (OccupationID, TrainingID) VALUES
  (1, 1), 
  (1, 2),
  (3, 5),
  (4, 6),
  (5, 7),
  (6, 8), 
  (6, 9);

-- 2.14) JobPosting (added 21–25)
INSERT INTO JobPosting (PostingID, JobID, Status, PostingDate) VALUES
  (1,  '29-1141', 'Open',    '2024-01-15'),
  (2,  '29-1141', 'Closed',  '2024-03-20'),
  (3,  '15-1252', 'Open',    '2024-02-10'),
  (4,  '25-2021', 'Open',    '2024-08-01'),
  (5,  '13-2011', 'Closed',  '2024-06-15'),
  (6,  '13-1111', 'Open',    '2024-11-05'),
  (7,  '31-9091', 'Open',    '2025-01-20'),
  (8,  '15-1252', 'Open',    '2025-03-01'),
  (9,  '25-2021', 'Closed',  '2025-05-12'),
  (10, '13-1111', 'Open',    '2025-06-18'),
  (11, '29-1141', 'Open',    '2025-07-01'),
  (12, '15-1252', 'Closed',  '2025-07-15'),
  (13, '25-2021', 'Open',    '2025-08-01'),
  (14, '13-2011', 'Open',    '2025-09-10'),
  (15, '31-9091', 'Closed',  '2025-10-05'),
  (16, '11-2021', 'Open',    '2025-11-01'),
  (17, '15-2041', 'Closed',  '2025-11-15'),
  (18, '33-3051', 'Open',    '2025-12-01'),
  (19, '17-2051', 'Open',    '2026-01-10'),
  (20, '35-1011', 'Closed',  '2026-02-05'),
  (21, '15-1253', 'Open',    '2026-03-12'),
  (22, '29-1031', 'Closed',  '2026-04-20'),
  (23, '29-1123', 'Open',    '2026-05-15'),
  (24, '13-1071', 'Open',    '2026-06-30'),
  (25, '15-2041', 'Closed',  '2026-07-08');


INSERT INTO JobCategory (JobID, JobTitle, EmployedCount2023, EmployedCount2033, MarketDistribution2033, EmployDistribution2023, EmployDistribution2033, SelfEmployment2023, OpeningsAvg, MedianSalary) VALUES
  ('11-1011', 'Chief executives', 313900, 331100, 0.20, 0.20, 0.20, 28.10, 23, 206420.00),
  ('11-1021', 'General and operations managers', 3630100, 3840500, 2.20, 2.20, 2.20, 0.50, 320, 102950.00),
  ('11-1031', 'Legislators', 33700, 35000, 0.00, 0.00, 0.00, NULL, 2, 44810.00),
  ('11-2011', 'Advertising and promotions managers', 22200, 21700, 0.00, 0.00, 0.00, 6.20, 1, 126960.00),
  ('11-2021', 'Marketing managers', 389100, 420800, 0.20, 0.20, 0.20, 3.20, 34, 161030.00),
  ('11-2022', 'Sales managers', 584800, 619100, 0.40, 0.30, 0.40, 0.10, 48, 138060.00),
  ('11-2032', 'Public relations managers', 78400, 83800, 0.00, 0.00, 0.00, NULL, 6, 138520.00),
  ('11-2033', 'Fundraising managers', 38200, 40500, 0.00, 0.00, 0.00, NULL, 2, 123480.00),
  ('11-3012', 'Administrative services managers', 256800, 272800, 0.20, 0.20, 0.20, NULL, 22, 108390.00),
  ('11-3013', 'Facilities managers', 140500, 147900, 0.10, 0.10, 0.10, 0.70, 12, 104690.00),
  ('11-3021', 'Computer and information systems managers', 613500, 720400, 0.40, 0.40, 0.40, 1.00, 54, 171200.00),
  ('11-3031', 'Financial managers', 837100, 975300, 0.60, 0.50, 0.60, 2.40, 75, 161700.00),
  ('11-3051', 'Industrial production managers', 230100, 236700, 0.10, 0.10, 0.10, 1.40, 17, 121440.00),
  ('11-3061', 'Purchasing managers', 81300, 85400, 0.00, 0.00, 0.00, 3.80, 6, 139510.00),
  ('11-3071', 'Transportation, storage, and distribution managers', 211800, 230800, 0.10, 0.10, 0.10, 3.70, 19, 102010.00),
  ('11-3111', 'Compensation and benefits managers', 19100, 19500, 0.00, 0.00, 0.00, NULL, 1, 140360.00),
  ('11-3121', 'Human resources managers', 208900, 222500, 0.10, 0.10, 0.10, 1.10, 17, 140030.00),
  ('11-3131', 'Training and development managers', 43200, 46400, 0.00, 0.00, 0.00, NULL, 3, 127090.00),
  ('11-9013', 'Farmers, ranchers, and other agricultural managers', 856600, 842900, 0.50, 0.50, 0.50, 65.20, 88, 87980.00),
  ('11-9021', 'Construction managers', 520900, 568500, 0.30, 0.30, 0.30, 35.80, 45, 106980.00),
  ('11-9031', 'Education and childcare administrators, preschool and daycare', 80900, 79200, 0.00, 0.00, 0.00, 5.90, 5, 56270.00),
  ('11-9032', 'Education administrators, kindergarten through secondary', 316600, 315000, 0.20, 0.20, 0.20, 1.40, 20, 104070.00),
  ('11-9033', 'Education administrators, postsecondary', 216400, 222700, 0.10, 0.10, 0.10, 2.70, 15, 103960.00),
  ('11-9039', 'Education administrators, all other', 57700, 59100, 0.00, 0.00, 0.00, 4.30, 4, 89040.00),
  ('11-9041', 'Architectural and engineering managers', 210200, 221800, 0.10, 0.10, 0.10, NULL, 15, 167740.00),
  ('11-9051', 'Food service managers', 393600, 399500, 0.20, 0.20, 0.20, 36.40, 44, 65310.00),
  ('11-9071', 'Gambling managers', 5300, 5500, 0.00, 0.00, 0.00, 9.50, 0, 85580.00),
  ('11-9072', 'Entertainment and recreation managers, except gambling', 35800, 39700, 0.00, 0.00, 0.00, 11.40, 4, 77180.00),
  ('11-9081', 'Lodging managers', 53300, 58600, 0.00, 0.00, 0.00, 18.70, 6, 68130.00),
  ('11-9111', 'Medical and health services managers', 562700, 723300, 0.40, 0.30, 0.40, 5.10, 61, 117960.00);




SELECT * FROM [dbo].[Table1.2]


-- Q1: What are the top 5 jobs with the highest self-employment rate? (Job Seeker)
WITH RankedSelfEmployed AS (
  SELECT JobID, JobTitle, SelfEmployment2023,
         RANK() OVER (ORDER BY SelfEmployment2023 DESC) AS Rank
  FROM JobCategory
  WHERE SelfEmployment2023 IS NOT NULL
)
SELECT Rank, JobID, JobTitle, SelfEmployment2023
FROM RankedSelfEmployed
WHERE Rank <= 5;

-- Q2:  What is the median salary in 2024 based on the education level necessary for the position? (Analyst)
SELECT d.DegreeType,
       PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY jc.MedianSalary)
       OVER (PARTITION BY d.DegreeType) AS Median_Salary_By_Education
FROM JobDegreeRequirement jdr
JOIN Degree d ON jdr.DegreeID = d.DegreeID
JOIN JobCategory jc ON jdr.JobID = jc.JobID
WHERE jc.MedianSalary IS NOT NULL;

-- Q3: Which 5 jobs have the most open positions listed in 2024? (Employer)
	WITH RankedOpenings AS (
   		SELECT JobID, JobTitle, OpeningsAvg,
          		RANK() OVER (ORDER BY OpeningsAvg DESC) AS Rank
   		FROM JobCategory
)
SELECT Rank, JobID, JobTitle, OpeningsAvg
FROM RankedOpenings
WHERE Rank <= 5;

-- Q4: What are the top 5 jobs by median salary in 2024?
	WITH RankedSalary AS (
   		SELECT JobID, JobTitle, MedianSalary,
          RANK() OVER (ORDER BY MedianSalary DESC) AS Rank
  	FROM JobCategory
)
SELECT Rank, JobID, JobTitle, MedianSalary
FROM RankedSalary
WHERE Rank <= 5;

-- Q5: Which jobs require a bachelor’s degree
SELECT DISTINCT jc.JobID, jc.JobTitle
FROM JobCategory jc
JOIN JobDegreeRequirement jdr ON jc.JobID = jdr.JobID
JOIN Degree d ON jdr.DegreeID = d.DegreeID
WHERE d.DegreeType = 'Bachelor';



-- Q6:Which jobs have no on-the-job training requirements, and which of those has the highest median salary?
SELECT jc.JobID, jc.JobTitle, jc.MedianSalary
FROM JobCategory jc
LEFT JOIN JobTrainingRequirement jtr ON jc.JobID = jtr.JobID
WHERE jtr.JobID IS NULL
ORDER BY jc.MedianSalary DESC;


-- Q7: Top 5 jobs by numeric increase in openings (2033 – 2023)
WITH RankedJobsDiff AS (
   SELECT
       JobID, JobTitle,
       (EmployedCount2033 - EmployedCount2023) AS NewPositionOpenings,
       RANK() OVER (ORDER BY (EmployedCount2033 - EmployedCount2023) DESC) AS Rank
   FROM JobCategory
)
SELECT Rank, JobID, JobTitle, NewPositionOpenings
FROM RankedJobsDiff
WHERE Rank <= 5;



--Q8: Which 5 jobs show the lowest percentage increase in employment from 2023 to 2033?
WITH RankedJobDiffPercent AS (
   SELECT
   JobID, JobTitle, ROUND(((CAST(EmployedCount2033 - EmployedCount2023 AS FLOAT)) / EmployedCount2023) * 100.0, 2) AS EmployedCountPercentDiff,
   RANK() OVER (ORDER BY ((CAST(EmployedCount2033 - EmployedCount2023 AS FLOAT)) / EmployedCount2023) * 100.0 ASC) AS Rank
   FROM JobCategory
)
SELECT Rank, JobID, JobTitle, EmployedCountPercentDiff
FROM RankedJobDiffPercent
WHERE Rank <= 5;


-- Q9: Total average annual openings for all jobs whose SOC code starts with '11-'
WITH Soc11 AS (
  SELECT jc.JobID, jc.JobTitle, jc.OpeningsAvg
  FROM JobCategory jc
  JOIN OccupationCategory oc
  ON jc.JobID = jc.JobID  
  WHERE jc.JobID LIKE '11-%'
)
SELECT ROUND(AVG(OpeningsAvg), 2) AS AvgAnnualOpenings_Soc11
FROM Soc11;

-- Q10: Which employers provide more than one distinct training?
WITH EmTrCo AS (
  SELECT et.EmployerID, e.EmployerName, COUNT(DISTINCT et.TrainingID) AS DistinctTrainings
  FROM EmployerTraining et
  JOIN Employer e
  ON et.EmployerID = e.EmployerID
  GROUP BY et.EmployerID, e.EmployerName
)
SELECT EmployerID, EmployerName, DistinctTrainings
FROM EmTrCo
WHERE DistinctTrainings > 1;
