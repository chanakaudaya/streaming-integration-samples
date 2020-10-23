# Introduction
This sample demonstrates how to read a file content (tailing) using a regular expression pattern with WSO2 SI and do a simple transformation to that event and log the transformed message to the console.  

# How to run

1. Deploy the sample via Tooling or to the server
2. Replace the file url with a valid URL within your system (noisy_data.txt)
3. Add the below line to the file at the end
```
Oracle Corporation <orcl 95 volume 200> 500 Oracle Parkway. 
Redwood Shores CA, 94065. 
Corporate Phone: 650.506.7000. 
HQ-Security: 650.506.5555

```
4. You could observe the following log entry in the console
```
INFO {io.siddhi.core.stream.output.sink.LogSink} - TailFileRegex : LogStream : Event{timestamp=1603454169338, data=[ORCL, 95.0, 200], isExpired=false}

```