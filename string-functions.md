# string-functions

run sql query from a file 
```sql
source first_file.sql
source testing/insert.sql
```

execute sql file from docker
```bash
docker exec -i mysql mysql -u root -ppassword cat_app < first_file.sql
docker exec -i mysql mysql -u root -ppassword cat_app < testing/insert.sql
```
> cat_app is the database 

