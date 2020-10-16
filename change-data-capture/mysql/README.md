# Introduction
This sample demonstrates how to implement change data capture with mysql database on WSO2 SI. It shows 3 samples where each of the insert, delete and update operations are captured by WSO2 SI and log the changed event details in the console. 

# Pre-requisites
- Enable binary logging in the mysql server by editing the ~/.my.cnf (on Mac) file with the below content.
```
[mysqld]
log-bin=bin.log
log-bin-index=bin-log.index
max_binlog_size=100M
binlog_format=row
```
- Then create a user and provide the necessary permissions to access the mysql database.
```
CREATE USER 'wso2si'@'localhost' IDENTIFIED BY 'wso2';
GRANT ALL PRIVILEGES ON *.* TO 'wso2si'@'localhost';
alter user 'wso2si'@'localhost' identified with mysql_native_password by 'wso2';
flush privileges;

CREATE SCHEMA production;
use production;
CREATE TABLE SweetProductionTable (name VARCHAR(20),amount double(10,2));
```
- Make sure you add the mysql connector to /lib directory of the server. 
- Install the cdc-mysql extension by executing the below command from the /bin directory of the SI server
```
./extension-installer.sh install cdc-mysql
./extension-installer.sh install rdbms-mysql
```


# How to run (Insert)

1. Deploy the sample ```CDCListenForInserts.siddhi``` via Tooling or to the server
2. Execute the following SQL command
```
insert into SweetProductionTable values('chocolate',100.0);
```

3. Observe the following log entry in the server console output

```
INFO {io.siddhi.core.stream.output.sink.LogSink} - CDCListenForInserts : LogStream : Event{timestamp=1602848181175, data=[chocolate, 100.0], isExpired=false}

```

# How to run (Update)

1. Deploy the sample ```CDCListenForUpdates.siddhi``` via Tooling or to the server
2. Execute the following SQL command
```
update SweetProductionTable SET name = 'Almond cookie' where name = 'chocolate';
```

3. Observe the following log entry in the server console output

```
INFO {io.siddhi.core.stream.output.sink.LogSink} - CDCListenForUpdates : LogStream : Event{timestamp=1602849852263, data=[chocolate, Almond cookie, 100.0, 100.0], isExpired=false}
```

