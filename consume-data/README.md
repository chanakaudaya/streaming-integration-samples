# Introduction
This sample demonstrates how to consume and event from an HTTP event source (client) and log the input message to the console. It uses JSON data mapping to read the data and publish the same to the log event sink. 

# How to run

1. Deploy the sample via Tooling or to the server
2. Execute the following CURL command
```
curl -X POST \
  http://localhost:5005/SalesTotalsEP \
  -H 'content-type: application/json' \
  -d @input1.json
```

3. Observe the following log entry in the server console output

```
INFO {io.siddhi.core.stream.output.sink.LogSink} - Sales Totals: : Event{timestamp=1602657048208, data=[2, DDwT, 12, 22, 112121], isExpired=false}

```

