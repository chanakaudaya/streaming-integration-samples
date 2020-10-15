# Introduction
This sample demonstrates how to enrich data with WSO2 SI by joining data stored in a database table with the event data and log the enriched message to the console. It uses JSON data mapping to read the data and publish the same to the log event sink. 

# Pre-requisites

- Download and install the MySQL Server.
- Download the MySQL JDBC driver.
- Unzip the downloaded MySQL driver zipped archive, and copy the MySQL JDBC driver JAR (mysql-connector-java-x.x.xx-bin.jar) into the <SI_HOME>/lib directory.
- Enter the following command in a terminal/command window, where username is the username you want to use to access the databases.
mysql -u username -p
- To create a database named UserDataDB with a table named UserTable issue the following commands from the terminal:
```
mysql> create database UserDataDB;
mysql> use UserDataDB;
```

- To create the UserTable table: 
```
create table UserTable ( userId LONG, firstname VARCHAR(255), lastname VARCHAR(255) )
```

- Insert data to the table
```
insert into UserTable (userId, firstname, lastname) values (1, "chanaka", "fernando");

```

# How to run

1. Deploy the sample via Tooling or to the server
2. Execute the following CURL command
```
curl -X POST \
  http://localhost:5005/TransactionEP \
  -H 'content-type: application/json' \
  -d @input1.json
```

3. Observe the following log entry in the server console output

```
INFO {io.siddhi.core.stream.output.sink.LogSink} - Transaction Details: : Event{timestamp=1602762122569, data=[1, chanaka fernando, 12.5, LK], isExpired=false}

```

