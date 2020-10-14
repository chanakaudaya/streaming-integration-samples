# Introduction
This sample demonstrates how to transform data with WSO2 SI and log the transformed message to the console. It uses JSON data mapping to read the data and publish the same to the log event sink. 

# How to run

1. Deploy the sample via Tooling or to the server
2. Execute the following CURL command
```
curl -X POST \
  http://localhost:5005/TempEP \
  -H 'content-type: application/json' \
  -d @input1.json
```

3. Observe the following log entry in the server console output

```
INFO {io.siddhi.core.stream.output.sink.LogSink} - Room temperature: : Event{timestamp=1602660809897, data=[12, 2, 22.0], isExpired=false}

```

4. Change the "temp" value in the input1.json file to "25.0" and execute the curl command (above) again. Now you should observe the below log which prints the average value of temperature (23.5) similar to below output.

```
INFO {io.siddhi.core.stream.output.sink.LogSink} - Room temperature: : Event{timestamp=1602660830013, data=[12, 2, 23.5], isExpired=false}
```

