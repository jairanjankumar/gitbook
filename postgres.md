# Postgres

connect to Postgres SQL shell

(generally you may find in location), /Applications/PostgreSQL 11/SQL Shell (psql).app

```
\h for help with SQL commands
```

```
\? for help with psql commands
```

```
\l -> this to list all databases.
```

```
\c db -> to connect with database caled db
```

```
\d -> to list all tables.
```

```
\dn -> list all schema
```

```
\dt lists tables for public schema. To show tables of all schemas use \dt *.* 
and for a particular schema use \dt schema_name.*
```

```
\q to quit
```

Copy from csv file to table:

```
COPY Emp(name, id) FROM '\tmp\test.csv' DELIMITER ',' HEADER ;
```
