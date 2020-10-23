# Introduction
This sample demonstrates how to read a file by tailing it with WSO2 SI and do a simple transformation to that event and log the transformed message to the console.  

# How to run

1. Deploy the sample via Tooling or to the server
2. Replace the file url with a valid URL within your system (productions.csv)
3. Add the below line to the file at the end
```
Cup cake,300.0

```
4. You could observe the following log entry in the console
```
INFO {io.siddhi.core.stream.output.sink.LogSink} - ReceiveEventsFromFile : LogStream : Event{timestamp=1564490869579, data=[CUP CAKE, 300.0], isExpired=false}

```

