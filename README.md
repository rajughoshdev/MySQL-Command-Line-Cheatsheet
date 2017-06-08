# MySQL Command Line Cheatsheet

* Access monitor:` mysql -u [username] -p;`
* Show all databases: `show databases;`
* Access database: `mysql -u [username] -p [database];` 
* Create new database: `create database [database];`
* Select database: `use [database];`
* Determine what database is in use:`select database();`
* Show all tables: `show tables;`
* Show table structure: `describe [table];`
* List all indexes on a table: `show index from [table];`
* Create new table with columns: `CREATE TABLE [table] ([column] VARCHAR(120), [another-column] DATETIME);`
* Adding a column: `ALTER TABLE [table] ADD COLUMN [column] VARCHAR(120);`
* Inserting a record: `INSERT INTO [table] ([column], [column]) VALUES ('[value]', [value]');`
* Selecting records: `SELECT * FROM [table];`
* Explain records: `EXPLAIN SELECT * FROM [table];`
* Selecting parts of records: `SELECT [column], [another-column] FROM [table];`
* Counting records: `SELECT COUNT([column]) FROM [table];`
* Delete *all records* from a table (without dropping the table itself): `DELETE FROM [table];`(This also resets the incrementing counter for auto generated columns like an id column.)
* Delete all records in a table: `truncate table [table];`
* Removing table columns: `ALTER TABLE [table] DROP COLUMN [column];`
* Deleting tables: `DROP TABLE [table];`
* Deleting databases: `DROP DATABASE [database];`
* Custom column output names: `SELECT [column] AS [custom-column] FROM [table];`
*  Logout: `exit;`
*  GRANT ALL ON `dbName`.* to `dbName`@`%.%.%.%`; 
*  CREATE USER `'newuser'@'localhost' IDENTIFIED BY 'password';`
*  CREATE USER `'newuser'@'%.%.%.%' IDENTIFIED BY 'password';`

**To export**

- If it's an entire DB, then:

`$ mysqldump -u [uname] -p[pass] db_name > db_backup.sql`
- If it's all DBs, then:

`$ mysqldump -u [uname] -p[pass] --all-databases > all_db_backup.sql`
- If it's specific tables within a DB, then:

`$ mysqldump -u [uname] -p[pass] db_name table1 table2 > table_backup.sql`
- You can even go as far as auto-compressing the output using gzip (if your DB is very big):

`$ mysqldump -u [uname] -p[pass] db_name | gzip > db_backup.sql.gz`
- If you want to do this remotely and you have the access to the server in question, then the following would work (presuming the MySQL server is on port 3306):

`$ mysqldump -P 3306 -h [ip_address] -u [uname] -p[pass] db_name > db_backup.sql`

**To import**

- Type the following command to import sql data file:

`$ mysql -u username -p -h localhost DATA-BASE-NAME < data.sql`
- In this example, import 'data.sql' file into 'blog' database using sat as username:

`$ mysql -u sat -p -h localhost blog < data.sql`
- If you have a dedicated database server, replace localhost hostname with with actual server name or IP address as follows:

`$ mysql -u username -p -h 202.54.1.10 databasename < data.sql`
- OR use hostname such as mysql.cyberciti.biz

`$ mysql -u username -p -h mysql.cyberciti.biz database-name < data.sql`
- If you do not know the database name or database name is included in sql dump you can try out something as follows:

`$ mysql -u username -p -h 202.54.1.10 < data.sql`
