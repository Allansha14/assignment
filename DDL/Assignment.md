# Q 1.
```
CREATE TABLE Department3(
Deptno int,
Deptname varchar(40),
Location varchar(40)
)

DESC Department3
```
![Alt text](../New%20folder/department1.png)

# -----------------------------------------------
```
CREATE TABLE Employee2(
Empno int,
ManagerID int,
FirstName varchar(40),
LastName Varchar(40),
UserID int,
DepNO int,
Salary int,
Commission int,
JoiningDate Date,
Designation varchar(40)
)
DESC Employee2
```
![Alt text](../New%20folder/emp2.png)

# ------------------------------------------------------
# Q 2.
```
ALTER TABLE Department3 ADD CONSTRAINT dep_ref Primary Key(Deptno)
ALTER TABLE Department3 ADD CONSTRAINT uniq_ref UNIQUE(Deptname)
ALTER TABLE Department3 ADD Floor number(2,0)
ALTER TABLE Department3 MODIFY Deptname VARCHAR(20)
ALTER TABLE Department3 MODIFY Location VARCHAR(20)
DESC Department3
```
![Alt text](../New%20folder/q2.png)


# -------------------------------------------
# Q 3.
```
ALTER TABLE Employee2 ADD CONSTRAINT emp_ref Primary Key(Empno)
ALTER TABLE Employee2 MODIFY ManagerID number(3,0)
ALTER TABLE Employee2 MODIFY FirstName VARCHAR(20) not null
ALTER TABLE Employee2 MODIFY LastName VARCHAR(20)
ALTER TABLE Employee2 MODIFY UserID VARCHAR(20)
ALTER TABLE Employee2 ADD CONSTRAINT emp_fk FOREIGN KEY (DepNO) REFERENCES Department3 (Deptno);
ALTER TABLE Employee2 MODIFY Commission number(3,0)
ALTER TABLE Employee2 MODIFY Designation VARCHAR(25)
ALTER TABLE Employee2 MODIFY Salary number(5,2)

DESC Employee2
```
![Alt text](../New%20folder/q3.png)

# ----------------------------------------------

# Q 4.

```
ALTER TABLE Employee2 ADD HRA NUMBER

ALTER TABLE Employee2 ADD PF  NUMBER
DESC Employee2
```
![Alt text](../New%20folder/Q4.png)


# --------------------------------------------

# Q 5. 

```
ALTER TABLE Employee2 MODIFY HRA number(5,2)
DESC Employee2

```
![Alt text](../New%20folder/q5.png)


# ---------------------------------------------------------

# Q 6.

ALTER TABLE Employee2 MODIFY PF number(5,2)
ALTER TABLE Employee2 ADD CONSTRAINT pf_ref CHECK (PF < 5000);
DESC Employee2

![Alt text](../New%20folder/Q6.png)

# --------------------------------------------------

# Q 7. 
```
CREATE TABLE Customer (
    Custno NUMBER(3),
    CustnoName VARCHAR2(20),
    Address VARCHAR2(40)
)
DESC Customer
```
![Alt text](../New%20folder/q7.png)

# ---------------------------------

# Q 7.
```
CREATE TABLE Orders (
    OrderNo NUMBER(3),
    Custno NUMBER(3),
    OrderDate DATE
)
DESC Orders
```
![Alt text](../New%20folder/8.png)

# ---------------------------------------------------

# Q 7.

CREATE TABLE OrderItem (
    ItemID NUMBER(3),
    OrderNo NUMBER(3),
    ItemName VARCHAR2(20),
    Quantity NUMBER(2)
)

![Alt text](../New%20folder/9.png)

# ---------------------------------------

# Q 8.
```
ALTER TABLE Customer ADD CONSTRAINT pk_cust PRIMARY KEY (Custno)

ALTER TABLE Customer MODIFY CustnoName VARCHAR2(20)

ALTER TABLE Customer MODIFY Address VARCHAR2(40)


DESC Customer
```
![Alt text](../New%20folder/Q8.png)

# -----------------------------------------------

# Q9.
```
ALTER TABLE Orders ADD CONSTRAINT pk_order PRIMARY KEY (OrderNo)

ALTER TABLE Orders ADD CONSTRAINT fk_order_customer FOREIGN KEY (Custno) REFERENCES Customer(Custno)

ALTER TABLE Orders MODIFY OrderDate DATE 
DESC Orders

```
![Alt text](../New%20folder/Q9.png)

# ---------------------------------------

# Q10.
```
ALTER TABLE OrderItem ADD CONSTRAINT pk_item PRIMARY KEY (ItemID)
ALTER TABLE OrderItem ADD CONSTRAINT fk_item_order FOREIGN KEY (OrderNo) REFERENCES Orders(OrderNo)
ALTER TABLE OrderItem MODIFY ItemName VARCHAR2(20)
ALTER TABLE OrderItem MODIFY Quantity NUMBER(2)
DESC OrderItem

```
![Alt text](../New%20folder/Q10.png)

# ------------------------------------------

# Q 11 .
```

CREATE TABLE Course (
    CourseID INT PRIMARY KEY,      
    StreamID INT,                  
    Description VARCHAR(255),      
    Fees DECIMAL(10, 2)             
)
DESC OrderItem
```
![Alt text](../New%20folder/Q11.png)
```
CREATE TABLE Batch (
    BatchID INT PRIMARY KEY,        
    CourseID INT,                   
    BatchName VARCHAR(100),         
    FOREIGN KEY (CourseID) REFERENCES Course(CourseID)  
)

DESC Batch
```
![Alt text](../New%20folder/11.png)
```
CREATE TABLE Student2 (
    StudID INT PRIMARY KEY,          
    LastName VARCHAR(50),            
    MiddleName VARCHAR(50),          
    FirstName VARCHAR(50),           
    BatchID INT,                     
    Grade CHAR(2),                   
    FOREIGN KEY (BatchID) REFERENCES Batch(BatchID)  
)
DESC Student2
```
![Alt text](../New%20folder/q.11.png)



```
CREATE TABLE Customer (
    Custno NUMBER(3),
    CustnoName VARCHAR2(20),
    Address VARCHAR2(40)
)
DESC Customer
```
```
CREATE TABLE Orders (
    OrderNo NUMBER(3),
    Custno NUMBER(3),
    OrderDate DATE
)
DESC Orders
```
```
CREATE TABLE OrderItem (
    ItemID NUMBER(3),
    OrderNo NUMBER(3),
    ItemName VARCHAR2(20),
    Quantity NUMBER(2)
)
DESC OrderItem
```
```
ALTER TABLE Customer ADD CONSTRAINT pk_cust PRIMARY KEY (Custno)

ALTER TABLE Customer MODIFY CustnoName VARCHAR2(20)

ALTER TABLE Customer MODIFY Address VARCHAR2(40)


DESC Customer
```
```
ALTER TABLE Orders ADD CONSTRAINT pk_order PRIMARY KEY (OrderNo)

ALTER TABLE Orders ADD CONSTRAINT fk_order_customer FOREIGN KEY (Custno) REFERENCES Customer(Custno)

ALTER TABLE Orders MODIFY OrderDate DATE 
DESC Orders
```
```
ALTER TABLE OrderItem ADD CONSTRAINT pk_item PRIMARY KEY (ItemID)
ALTER TABLE OrderItem ADD CONSTRAINT fk_item_order FOREIGN KEY (OrderNo) REFERENCES Orders(OrderNo)
ALTER TABLE OrderItem MODIFY ItemName VARCHAR2(20)
ALTER TABLE OrderItem MODIFY Quantity NUMBER(2)
DESC OrderItem
```
```
ALTER TABLE Customer MODIFY Address VARCHAR(100);
```
```
CREATE TABLE Course (
    CourseId VARCHAR(25),
    StreamId VARCHAR(20),
    Title VARCHAR(40),
    Description VARCHAR(200),
    Fees NUMBER,
    Deptno NUMBER(2),
    CONSTRAINT fk_course FOREIGN KEY (Deptno) REFERENCES Department3(Deptno),
    PRIMARY KEY (CourseId, Deptno)
);
DESC Course
```
```
CREATE TABLE Batch (
    BatchId VARCHAR(30),
    CourseId VARCHAR(5),
    Deptno NUMBER(2),
    CONSTRAINT fk_batch FOREIGN KEY (CourseId, Deptno) REFERENCES Course(CourseId, Deptno),
    BatchName CHAR(1)
);
DESC Batch;
```

```
CREATE TABLE Student (
    StudId VARCHAR(20) PRIMARY KEY,
    LastName VARCHAR(25),
    MiddleName VARCHAR(30),
    FirstName VARCHAR(20),
    Dob DATE,
    Address VARCHAR(50),
    City VARCHAR(20),
    State VARCHAR(20),
    Zipcode VARCHAR(9),
    Telephone VARCHAR(10),
    Fax VARCHAR(10),
    Email VARCHAR(30),
    Grade CHAR(1),
    CONSTRAINT check_grade CHECK (Grade IN ('A', 'A+', 'A-', 'B', 'B+', 'B-', 'C', 'C+', 'C-', 'D', 'D+', 'D-', 'F', 'F+', 'F-'))
);
DESC Student;
```
![Alt text](../New%20folder/Q15.png)

```
ALTER TABLE Student DROP COLUMN MiddleName;
ALTER TABLE Student RENAME TO Participant;

DESC Participant;
```
![alt text](../New%20folder/17.png)


