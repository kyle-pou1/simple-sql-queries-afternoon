# simple-sql-queries

For today we will be practicing inserting and querying data using SQL.

Here is a website that will let us write queries to interact with some data.  [http://jxs.me/chinook-web/](http://jxs.me/chinook-web/)

On the left are the Tables with their fields.  The right is where we will be writing our queries.  The bottom is where we will see our results.  

Any new tables or records that we add into the database will be removed after you refresh the page.  So if you're wondering where you data went, that may be why.

Use [www.sqlteaching.com](http://www.sqlteaching.com/) or [sqlbolt.com](http://sqlbolt.com/) as resources for the missing keywords you'll need.

## PERSON
1. Create a table called Person that records a person's Name, Age, Height, City, FavoriteColor, and Id.  Id should be an auto-incrementing id/primary key.

CREATE TABLE person
(
  Name VARCHAR(255),
  Age   INTEGER,
  Height VARCHAR(255),
  City VARCHAR(255),
  FavoriteColor VARCHAR(255),
  Id INTEGER PRIMARY KEY AUTOINCREMENT
  )

2. Add 5 different people into the Person database.  Remember to not include the Id because it should auto-increment.

INSERT INTO person (Name, Age, Height, City, FavoriteColor)
Values ('Tony', 23, 200, 'Houston', 'Blue'),
('Sara', 23, 120, 'Provo', 'Yellow'),
('Henry', 45, 180, 'Chicago', 'Gray'),
('Jessica', 30, 125, 'Miami', 'Blue'),
('Bob', 78, 300, 'New York', 'Brown')


3. List the people in the Person table by Height from tallest to shortest (descending)

SELECT * FROM person ORDER BY Height desc,

(For this database to create an auto incrementing field set it's type to INTEGER PRIMARY KEY AUTOINCREMENT)

  * List the people in the Person table by Height from shortest to tallest (ascending)

    SELECT * FROM person ORDER BY height;

  * List all the people in the Person table by oldest first

    SELECT * FROM person ORDER BY age desc;

  * List all the people in the Person table older than age 20.

    SELECT * FROM person WHERE age > 20;

  * List all the people in the Person table that are exactly 18.

    SELECT * FROM person WHERE age = 18;

  * List all Person that are less than 20 and older than 30.

    SELECT * FROM person WHERE age < 20 OR age > 30;

  * List all Person that are not 27 (Use not equals)

    SELECT * FROM person WHERE age != 27;

  * List all Person where their favorite color is not red

    SELECT * FROM person WHERE favoriteColor != 'red';

  * List all Person where their favorite color is not red or blue

    SELECT * FROM person WHERE favoriteColor != 'red' AND favoriteColor != 'blue';

  * List all Person where their favorite color is orange or green

    SELECT * FROM person WHERE favoriteColor = 'orange' OR favoriteColor = 'green';

  * List all Person where their favorite color is orange or green blue (use IN)

    SELECT * FROM person WHERE favoriteColor IN ('orange', 'green', 'blue');

  * List all Person where their favorite color is yellow or purple

  SELECT * FROM person WHERE favoriteColor IN ('yellow', 'purple');


## ORDER
4. Create a table called Orders that records the productName, productPrice, Quantity, and personId  
     CREATE TABLE Orders
     (
       productName VARCHAR(255),
       productPrice FLOAT,
       Quantity INTEGER,  
       personId INTEGER
      )
5. Add 5 Orders to Order table

    INSERT INTO Orders (productName, productPrice, quantity, personId)
    VALUES('Human', $23, 200, 1),
    ('Homoerectus', $23, 120, 2),
    ('Man', $46, 240, 3),
    ('Woman', $48, 100, 4),
    ('Child', $120, 6000, 5)

6. Select all the records from the Order table

    SELECT * FROM orders;

  * Calculate the total number of products Ordered

    SELECT sum(quantity) as products_ordered FROM orders;

  * Calculate the total Order Price

    SELECT sum(productPrice) as order_total FROM orders

  * Calculate the total Order Price By personId (If you only made orders for 1 person, go add more for the other people)

    SELECT personId, sum(productPrice) as order_total FROM orders GROUP BY personId;

## Artists
7. Add 3 new Artists to the Artist table
    INSERT INTO artist (name)
    VALUES ('Mello Yellow'), ('Taco Ted'), ('Beef Force')

 * Select the top 10 artists in reverse alphabetical order

    SELECT * FROM artist ORDER BY artistid desc LIMIT 10;

 * Select the top 5 artists in alphabetical order

    SELECT * FROM artist ORDER BY artistid LIMIT 5;

 * Select all artists that start with the word Black

    SELECT * FROM artist WHERE name LIKE "black%"

 * Select all artists that contain the word Black

    SELECT * FROM artist WHERE name is like "%black%"

## Employee
8. Add 2 new Employees to the Employee table

    INSERT INTO Employee (lastName, firstName)
    VALUES ('Poulsen', Kyle),
    ('Poop', 'Breath')

* List all Employee first and last names only that live in Calgary

    SELECT firstName, lastname FROM employee WHERE city = 'Calgary'

* Find the first and last name for the youngest employee

    SELECT firstname, lastname FROM employee ORDER BY birthdate desc LIMIT 1

* Find the first and last name for the oldest employee

    SELECT firstname, lastname FROM employee ORDER BY birthdate  LIMIT 1

* Find everyone that reports to Nancy Edwards (Use the ReportsTo column)

    SELECT * FROM employee where reportsto = 2

* Count how many people live in Lethbridge
    SELECT count(*) FROM employee Where city = 'Lethbridge';

## Invoice
9. Use the Invoice table for the following

* Count how many orders were made from the USA

    SELECT count(*) FROM invoice WHERE billingcountry = "USA"

* Find the largest order total amount

    SELECT max(total) FROM invoice;

* Find the smallest order total amount

    SELECT max(total) FROM invoice;

* Find all orders bigger than $5

    SELECT * FROM invoice WHERE total > 5;

* Count how many orders were smaller than $5

    SELECT count(total) FROM invoice WHERE total < 5;

* Count how many orders were in CA, TX, or AZ (use IN)

    SELECT count(total) FROM invoice WHERE billingstate IN ('CA', 'TX', 'AZ');

* Get the average total of the orders

    Select round(avg(total)) FROM invoice; //rap in round so you don't get a decimal.

* Get the total sum of the orders

    SELECT sum(total) FROM invoice

## Copyright

© DevMountain LLC, 2016. Unauthorized use and/or duplication of this material without express and written permission from DevMountain, LLC is strictly prohibited. Excerpts and links may be used, provided that full and clear credit is given to DevMountain with appropriate and specific direction to the original content.
