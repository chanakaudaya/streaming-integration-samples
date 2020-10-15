# Introduction
This sample demonstrates how to transform data with WSO2 SI with a custom function and log the transformed message to the console. It uses JSON data mapping to read the data and publish the same to the log event sink. 

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
INFO {io.siddhi.core.stream.output.sink.LogSink} - Current temperature: : Event{timestamp=1602757567123, data=[32-2, 45.0], isExpired=false}

```

