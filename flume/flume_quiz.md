## flume configure

# Name the components on this agent
agent1.sources = s1
agent1.sinks = k1
agent1.channels = c1

# Describe/configure the source
agent1.sources.s1.type = Netcat
agent1.sources.s1.bind = localhost
agent1.sources.s1.port = 44444

# Describe the sink
agent1.sinks.k1.type = logger

# Use a channel which buffers events in memory
agent1.channels.c1.type = memory
agent1.channels.c1.capacity = 1000
agent1.channels.c1.transactionCapacity = 100

agent1.sources.s1.channels = c1
agent1.sinks.k1.channel = c1



## telnet 실행
[training@localhost flume]$ telnet localhost 44444
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

OK

OK
dkdh
OK
ya
OK
hahahaha
OK
hi   
OK
my name is seong ho
OK
 d d f d f sd f sd f sd f sd f  
OK





## 실행화면 logging
2019-03-11 18:19:11,353 (SinkRunner-PollingRunner-DefaultSinkProcessor) [INFO - org.apache.flume.sink.LoggerSink.process(LoggerSink.java:94)] Event: { headers:{} body: 0D                                              . }
2019-03-11 18:19:11,476 (SinkRunner-PollingRunner-DefaultSinkProcessor) [INFO - org.apache.flume.sink.LoggerSink.process(LoggerSink.java:94)] Event: { headers:{} body: 0D                                              . }
2019-03-11 18:19:20,484 (SinkRunner-PollingRunner-DefaultSinkProcessor) [INFO - org.apache.flume.sink.LoggerSink.process(LoggerSink.java:94)] Event: { headers:{} body: 64 6B 64 68 0D                                  dkdh. }
2019-03-11 18:19:21,755 (SinkRunner-PollingRunner-DefaultSinkProcessor) [INFO - org.apache.flume.sink.LoggerSink.process(LoggerSink.java:94)] Event: { headers:{} body: 79 61 0D                                        ya. }
2019-03-11 18:19:26,276 (SinkRunner-PollingRunner-DefaultSinkProcessor) [INFO - org.apache.flume.sink.LoggerSink.process(LoggerSink.java:94)] Event: { headers:{} body: 68 61 68 61 68 61 68 61 0D                      hahahaha. }
2019-03-11 18:23:40,370 (SinkRunner-PollingRunner-DefaultSinkProcessor) [INFO - org.apache.flume.sink.LoggerSink.process(LoggerSink.java:94)] Event: { headers:{} body: 68 69 0D                                        hi. }
2019-03-11 18:23:47,152 (SinkRunner-PollingRunner-DefaultSinkProcessor) [INFO - org.apache.flume.sink.LoggerSink.process(LoggerSink.java:94)] Event: { headers:{} body: 6D 79 20 6E 61 6D 65 20 69 73 20 73 65 6F 6E 67 my name is seong }
2019-03-11 18:24:02,165 (SinkRunner-PollingRunner-DefaultSinkProcessor) [INFO - org.apache.flume.sink.LoggerSink.process(LoggerSink.java:94)] Event: { headers:{} body: 20 64 20 64 20 66 20 64 20 66 20 73 64 20 66 20  d d f d f sd f  }



