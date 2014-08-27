# mysql-mirror-database
## project board

_Intent_: Create an app to mirror a remote database with only SELECT grant

Logic:
1. Attempt to connect to remote database
2. Get a list of remote database tables
3. Compare list of remote database tables to local database tables
4. Create local database tables if needed
5. Get max event num from each local database table
6. Select and instert records from each remote database table into local database tables where remote event num > local event num
7. Repeat every <interval>

Interface:
	* Object that contains custom connection object with connection information for remote database and local database
	* Name of column that will be used as __event num__