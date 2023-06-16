# Apache Flink® SQL 

* Flink JobManager and Taskmanager with flink client sql
* MySQL

### Metastore Catalog

* A Metastore catalog is configured and can be used.

```
USE CATALOG hcat;
```

Switch back to the default catalog:

```
use catalog default_catalog;
```

* Start Hive CLI client

```
docker-compose exec metastore /opt/apache-hive-2.3.6-bin/bin/hive
```


### MySQL

* Start MySQL CLI client (to create tables, insert data, ...)

```
docker-compose exec mysql mysql -Dsql-demo -usql-demo -pdemo-sql
```

* Create a MySQL table that also works as LookupTableSource

```
CREATE TABLE ExchangeRates (
  currency STRING,
  rate DOUBLE
) WITH (
  'connector.type' = 'jdbc',
  'connector.url' = 'jdbc:mysql://mysql:3306/sql-demo',
  'connector.table' = 'ExchangeRates',
  'connector.driver' = 'com.mysql.jdbc.Driver',
  'connector.username' = 'sql-demo',
  'connector.password' = 'demo-sql',
  'connector.lookup.cache.max-rows' = '1',
  'connector.lookup.cache.ttl' = '0s'
);
```

* Add data to MySQL table either using the MySQL CLI client (see above). Writing from Flink CLI client with `INSERT INTO` works as well! :-)

