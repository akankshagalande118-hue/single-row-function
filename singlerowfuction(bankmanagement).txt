SQL> set pagesize 200;
SQL> set linesize 200;
SQL> --all customer names to uppercase in the Customers table
SQL> SELECT UPPER(Name) AS UppercaseName FROM Customers;

UPPERCASENAME                                                                                                                                                                                           
----------------------------------------------------------------------------------------------------                                                                                                    
JOHN DOE                                                                                                                                                                                                

SQL> --names of customers in lowercase from the table Customers
SQL> select lower(name)AS lowercaseName from Customers;

LOWERCASENAME                                                                                                                                                                                           
----------------------------------------------------------------------------------------------------                                                                                                    
john doe                                                                                                                                                                                                

SQL> --initial character of a customer name by extracting the first letter of the name
SQL> SELECT SUBSTRING(Name, 1, 1) AS Initial FROM Customers;
SELECT SUBSTRING(Name, 1, 1) AS Initial FROM Customers
                                *
ERROR at line 1:
ORA-00923: FROM keyword not found where expected 


SQL> SELECT SUBSTRING(Name, 1, 1) FROM Customers;
SELECT SUBSTRING(Name, 1, 1) FROM Customers
       *
ERROR at line 1:
ORA-00904: "SUBSTRING": invalid identifier 


SQL> SELECT SUBSTR(Name, 1, 1) AS Initial FROM Customers;
SELECT SUBSTR(Name, 1, 1) AS Initial FROM Customers
                             *
ERROR at line 1:
ORA-00923: FROM keyword not found where expected 


SQL> SELECT SUBSTR(Name, 1, 1)FROM Customers;

SUBS                                                                                                                                                                                                    
----                                                                                                                                                                                                    
J                                                                                                                                                                                                       

SQL> --Replace NULL values in the Phone column with the text "Not Available"
SQL> SELECT COALESCE(Phone, 'Not Available') AS Phone FROM Customers;

PHONE                                                                                                                                                                                                   
---------------                                                                                                                                                                                         
1234567890                                                                                                                                                                                              

SQL> --Round the Balance column in the Accounts table to two decimal places
SQL> SELECT ROUND(Balance, 2) AS RoundedBalance FROM Accounts;

ROUNDEDBALANCE                                                                                                                                                                                          
--------------                                                                                                                                                                                          
          1500                                                                                                                                                                                          

SQL> --Format account balances with commas for easier reading
SQL> SELECT TO_CHAR(Balance, '9,999,999.99') AS FormattedBalance FROM Accounts;

FORMATTEDBALA                                                                                                                                                                                           
-------------                                                                                                                                                                                           
     1,500.00                                                                                                                                                                                           

SQL> --Extract the year from the tDate column in the Transactions table
SQL> SELECT EXTRACT(MONTH FROM tDate) AS Month FROM Transactions;
SELECT EXTRACT(MONTH FROM tDate) AS Month FROM Transactions
                          *
ERROR at line 1:
ORA-00904: "TDATE": invalid identifier 


SQL> SELECT EXTRACT(MONTH FROM Date) AS Month FROM Transactions;
SELECT EXTRACT(MONTH FROM Date) AS Month FROM Transactions
                          *
ERROR at line 1:
ORA-00936: missing expression 


SQL> --Determine the length of customer names in the Customers table
SQL> SELECT LENGTH(Name) AS NameLength FROM Customers;

NAMELENGTH                                                                                                                                                                                              
----------                                                                                                                                                                                              
         8                                                                                                                                                                                              

SQL> --Add 7 days to the tDate in the Transactions table
SQL> SELECT tDate + INTERVAL '7' DAY AS NewDate FROM Transactions;
SELECT tDate + INTERVAL '7' DAY AS NewDate FROM Transactions
       *
ERROR at line 1:
ORA-00904: "TDATE": invalid identifier 


SQL> desc transactions;
 Name                                                                                                              Null?    Type
 ----------------------------------------------------------------------------------------------------------------- -------- ----------------------------------------------------------------------------
 TRANSACTION_ID                                                                                                    NOT NULL NUMBER
 ACCOUNT_ID                                                                                                                 NUMBER
 T_DATE                                                                                                            NOT NULL DATE
 AMOUNT                                                                                                            NOT NULL NUMBER
 TRANSACTION_TYPE                                                                                                  NOT NULL VARCHAR2(20)

SQL> SELECT T_DATE + INTERVAL '7' DAY AS NewDate FROM Transactions;

no rows selected

SQL> --Format transaction dates as DD-MM-YYYY
SQL> SELECT TO_CHAR(T_DATE, 'DD-MM-YYYY') AS FormattedDate FROM Transactions;

no rows selected

SQL> --Extract the username (string before @) from the Email column in the Customers table
SQL> SELECT CHARINDEX() FROM CUSTOMERS;
SELECT CHARINDEX() FROM CUSTOMERS
       *
ERROR at line 1:
ORA-00904: "CHARINDEX": invalid identifier 


SQL> --Make sure that each word in the Customer Name column is capitalized with the first letter
SQL> SELECT INITCAP(Name) AS CapitalizedName FROM Customers;

CAPITALIZEDNAME                                                                                                                                                                                         
----------------------------------------------------------------------------------------------------                                                                                                    
John Doe                                                                                                                                                                                                

SQL> --the absolute value of negative balances in the Accounts table
SQL> SELECT ABS(Balance) AS AbsoluteBalance FROM Accounts;

ABSOLUTEBALANCE                                                                                                                                                                                         
---------------                                                                                                                                                                                         
           1500                                                                                                                                                                                         

SQL> --the LPAD function to pad the AccountID column with leading zeros to a total of 10 digits
SQL> SELECT LPAD(AccountID, 10, '0') AS PaddedAccountID FROM Accounts;
SELECT LPAD(AccountID, 10, '0') AS PaddedAccountID FROM Accounts
            *
ERROR at line 1:
ORA-00904: "ACCOUNTID": invalid identifier 


SQL> SELECT LPAD(Account_ID, 10, '0') AS PaddedAccountID FROM Accounts;

PADDEDACCOUNTID                                                                                                                                                                                         
----------------------------------------                                                                                                                                                                
0000000001                                                                                                                                                                                              

SQL> --Remove leading and trailing spaces from customer names in the Customers table
SQL> SELECT NOW() AS CurrentDateTime;
SELECT NOW() AS CurrentDateTime
                              *
ERROR at line 1:
ORA-00923: FROM keyword not found where expected 


SQL> SELECT NOW() AS SYSDATE;
SELECT NOW() AS SYSDATE
                *
ERROR at line 1:
ORA-00923: FROM keyword not found where expected 


SQL> SELECT NOW() AS CurrentDateTime FROM CUSTOMERS;
SELECT NOW() AS CurrentDateTime FROM CUSTOMERS
       *
ERROR at line 1:
ORA-00904: "NOW": invalid identifier 


SQL> SELECT NOW() AS CurrentDateTime FROM TRANSACTIONS;
SELECT NOW() AS CurrentDateTime FROM TRANSACTIONS
       *
ERROR at line 1:
ORA-00904: "NOW": invalid identifier 


SQL> SELECT TRIM(Name) AS TrimmedName FROM Customers;

TRIMMEDNAME                                                                                                                                                                                             
----------------------------------------------------------------------------------------------------                                                                                                    
JOHN DOE                                                                                                                                                                                                

SQL> --Check if a customer's email contains the domain @gmail.com
SQL> SELECT CASE WHEN Email LIKE '%@gmail.com' THEN 'Gmail' ELSE 'Other' END AS EmailType FROM Customers;

EMAIL                                                                                                                                                                                                   
-----                                                                                                                                                                                                   
Other                                                                                                                                                                                                   

SQL> --last four digits of the phone number of a customer.
SQL> SELECT RIGHT(Phone, 4) AS Last4Digits FROM Customers;
SELECT RIGHT(Phone, 4) AS Last4Digits FROM Customers
       *
ERROR at line 1:
ORA-00904: "RIGHT": invalid identifier 


SQL> SELECT SUBSTR(Phone, -4) AS Last4Digits FROM Customers;

LAST4DIGITS                                                                                                                                                                                             
----------------                                                                                                                                                                                        
7890                                                                                                                                                                                                    

SQL> --today date using a one-row function.
SQL> SELECT SYS_DATE AS CurrentDate;
SELECT SYS_DATE AS CurrentDate
                             *
ERROR at line 1:
ORA-00923: FROM keyword not found where expected 


SQL> -- Convert the Balance column of the Accounts table to a string.
SQL> SELECT CAST(Balance AS CHAR) AS BalanceAsString FROM Accounts;
SELECT CAST(Balance AS CHAR) AS BalanceAsString FROM Accounts
            *
ERROR at line 1:
ORA-25137: Data value out of range 


SQL> --Generate a random number between 1 and 1000.
SQL> SELECT FLOOR(RAND() * 1000) AS RandomNumber;
SELECT FLOOR(RAND() * 1000) AS RandomNumber
                                          *
ERROR at line 1:
ORA-00923: FROM keyword not found where expected 


SQL> SELECT FLOOR(RAND() * 1000);
SELECT FLOOR(RAND() * 1000)
                          *
ERROR at line 1:
ORA-00923: FROM keyword not found where expected 


SQL> --Concatenate AccountType and Balance in to one formatted string of text.
SQL> SELECT CONCAT(Account_Type,' ',Balance) AS AccountDetails FROM Accounts;
SELECT CONCAT(Account_Type,' ',Balance) AS AccountDetails FROM Accounts
       *
ERROR at line 1:
ORA-00909: invalid number of arguments 


SQL> SELECT CONCATE(Account_Type,' ',Balance) AS AccountDetails FROM Accounts;
SELECT CONCATE(Account_Type,' ',Balance) AS AccountDetails FROM Accounts
       *
ERROR at line 1:
ORA-00904: "CONCATE": invalid identifier 


SQL> SPOOL OFF;
