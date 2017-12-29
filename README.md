# Hive in Practice

## Learn How Hive Work in Simple Example

```shell
# Hive startup commande
hive
```

```shell
# show TABLES in Hive 
SHOW TABLES;
```

```shell
# Hive shutdown
exit
```

### Create Hive TABLE :  
The syntax to create TABLE :
```shell
# commande to create Hive TABLE
CREATE [TEMPORARY] [EXTERNAL] TABLE [IF NOT EXISTS] [db_name.] table_name

[(col_name data_type [COMMENT col_comment], ...)]
[COMMENT table_comment]
[ROW FORMAT row_format]
[STORED AS file_format]
```

```shell
# show Hive TABLE structure
DESCRIBE 'table_name'
```
hiking Table Structure :

      hiking(id, name, region, distance , Altitude, suiteHiking)

example : 
```shell
# create table with 2 family columns
CREATE TABLE IF NOT EXISTS hiking (
	id INT,
	name STRING,
	region STRING,
	distance FLOAT,
	Altitude INT,
	suiteHiking INT )
	ROW FORMAT DELIMITED
	FIELDS TERMINATED BY '\t'
	LINES TERMINATED BY '\n' ;
```
      
### LOAD DATA to 'hiking' TABLE :
The syntax for load data : 
```shell
LOAD DATA [LOCAL] INPATH 'filepath' [OVERWRITE] INTO TABLE tablename 
```
example :
```shell
LOAD DATA LOCAL INPATH '<repository Path>/input/hiking.txt' #LOAD DATA FROM File
OVERWRITE INTO TABLE hiking;
```

### Query :

hiking more than 20 km : 
```sql
SELECT * FROM hiking WHERE distance >=20;
```

The hiking that have a suite :
```sql
SELECT * FROM hiking WHERE suiteHiking IS NOT NULL;
```

The maximum / average distance by region : 
```sql
SELECT region ,max(distance) max FROM hiking GROUP BY region;
```
```sql
SELECT region ,avg(distance) moy FROM hiking GROUP BY region;
```
