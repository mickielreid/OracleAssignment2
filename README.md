# Oracle Assignment 2
**Question 1**

*CREATE TABLE called supplier  with the following fields . 
supplier_id numeric(10)  - > Primary key with constraint name 
supplier_name varchar2(50) - >unique name 
contact_name varchar2(50)
phone_no varchar2(10)- >unique name
city varchar2(10) 
Region –> should accept only  ('N', 'NW', 'NE', 'S', 'SE', 'SW', 'W', 'E')

1.	Insert 5 records
2.	Display the details of the supplier who comes from Florida and their supplier id 500;
3.	Add phone number in the supplier table using DDL command
4.	Delete the unused column in the supplier table 
5.	Write a sql command to delete supplier table. 
6.	Create a view named supplier_contact . Include supplier_id,supplier_name,phone_no*

```
CREATE TABLE SUPPLIER
( supplier_id NUMBER(10) PRIMARY KEY,
  supplier_name  VARCHAR2(50) UNIQUE,
  contact_name varchar2(50),
  phone_no varchar2(10) UNIQUE,
  city varchar2(10),
  Region VARCHAR2(3)
  
  CONSTRAINT check_region
    CHECK (Region IN  ('N', 'NW', 'NE', 'S', 'SE', 'SW', 'W', 'E') )
  
);


Result Image:
Q1:  create table 
 

Q1-1: add five results
 

Q1-2: Display the details of the supplier who comes from Florida and their supplier id 500
select * from supplier where REGION = 'Florida' AND SUPPLIER_ID = 500;


Q1-3 : Add phone number in the supplier table using DDL command
ALTER TABLE supplier ADD (phone_number  number(10));

 
Q1-4: Delete the unused column in the supplier table 
ALTER TABLE supplier DROP COLUMN PHONE_NUMBER;

Q1-5: drop supplier table
Code: drop table supplier;
Q1-6:
Code: 
CREATE VIEW  supplier_contact AS
SELECT SUPPLIER_ID, SUPPLIER_NAME,PHONE_NO
FROM supplier;
[The code would not run because I dropped the table in the table in the previous question


```

**2. Question:**

*Ecommerce site determines shipping cost based on the products ordered and membership. The valid rates are displayed in the following table:

  QUANTITY	REGULAR SHIPPING COST	MEMBERS SHIPPING COST 
> Up to 3	$ 8.00	$ 4.00
>4-6	$7.00	$ 3.50
>7-10	$10.00	$5.00
>10	$15.00	$7.50

1.	Create a flowchart to outline the processing steps in order to handle this calculation. 
2.	Create a pl/sql block to complete the above task. Include variable that holds Y OR N to include membership status and a variable to denote the number of items purchased. Verify with different values* 


Q2-1: Create flow chart

Q2-2 : Create a pl/sql block to complete the above task. Include variable that holds Y OR N to include membership status and a variable to denote the number of items purchased. Verify with different values *

```
DECLARE 
MEMB_STAT CHAR(1):='N';
NUM_ITEMS NUMBER(9):='16';
SHIPPING_COST NUMBER(10,2);
TOTAL_COST NUMBER(10,2);
BEGIN 

    IF MEMB_STAT = 'Y' THEN  

        IF NUM_ITEMS >10 THEN
            SHIPPING_COST := '7.50'; 
        ELSIF NUM_ITEMS BETWEEN 7 AND 10 THEN
            SHIPPING_COST := '5.00'; 
        ELSIF NUM_ITEMS BETWEEN 4 AND 6 THEN
            SHIPPING_COST := '3.50';
        ELSE 
             SHIPPING_COST := '4.00';
         END IF;

        TOTAL_COST := SHIPPING_COST * NUM_ITEMS;
              DBMS_OUTPUT.PUT_LINE('SHIPING COST FOR THIS MEMEBR IS $'|| SHIPPING_COST);  
              DBMS_OUTPUT.PUT_LINE('Total Shipping cost is $'||  TOTAL_COST);  

    ELSE

        IF NUM_ITEMS >10 THEN
                SHIPPING_COST := '15.00'; 
            ELSIF NUM_ITEMS BETWEEN 7 AND 10 THEN
                SHIPPING_COST := '10.00'; 
            ELSIF NUM_ITEMS BETWEEN 4 AND 6 THEN
                SHIPPING_COST := '7.00';
            ELSE 
                 SHIPPING_COST := '8.00';
         END IF;
    END IF;

       TOTAL_COST := SHIPPING_COST * NUM_ITEMS;
    DBMS_OUTPUT.PUT_LINE('SHIPING COST FOR NON MEMEBR IS $'|| SHIPPING_COST);  
     DBMS_OUTPUT.PUT_LINE('Total Shipping cost is $'||  TOTAL_COST);  
    
END;




```
**3 - Question:**

*Run below script to create the table
DROP TABLE messages;
CREATE TABLE messages (results NUMBER(3));

a) Insert the numbers 1 through 10, excluding 6 and 8. 
b) Commit before the end of the block. 
c) Execute a SELECT statement to verify that your PL/SQL block worked.*

```
Create  table 
 

Q3-B : plsql code
DECLARE

U_TOTAL NUMBER(7);

BEGIN 

FOR LP IN 1..10 LOOP

IF LP = 6 OR LP = 8 THEN
CONTINUE;
END IF;

INSERT INTO messages
VALUES (LP);

END LOOP;
 
END;

Results

```
