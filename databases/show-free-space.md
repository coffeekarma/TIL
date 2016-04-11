# Show free database space 

###Mysql:
This statement is especially useful for mysql, since innodb tables do not release disk space for the operating system after deleting huge chunks of data. 
```SQL
SELECT table_schema "Data Base Name",
    sum( data_length + index_length ) / 1024 / 1024 "Data Base Size in MB",
    sum( data_free )/ 1024 / 1024 "Free Space in MB"
FROM information_schema.TABLES
GROUP BY table_schema ; 
```
