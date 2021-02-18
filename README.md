# Kafka-Installation
This repo is about Kafka installation

[Kafka download Link](https://kafka.apache.org/quickstart)

## Steps:
- After downloading,extract it and Put the .tgz file in C:\.
- Un-tar it (using Bash) and change into the directory
```
tar -xzf <filename>
cd <folder>
```
- Set up the environment variables
``` 
KAFKA_HOME =  C:\kafka-version folder
```
- Set up the path 
```
%KAFKA_HOME%\bin
%KAFKA_HOME%\bin\windows
```
- Use a different PowerShell as Administrator window for each process.These assume execution of commands from your %KAFKA_HOME% folder (e.g., C:\kafka-version) adjust them as needed.

Window 1 - Run Zookeeper Service  (keep window open)
```
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```
Window 2 - Run Kafka Service (keep window open)
```
.\bin\windows\kafka-server-start.bat .\config\server.properties
```
Window 3 (temporary) - Execute One-Time Commands - create, list, delete topics 
```
.\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --create --topic bearcat-messages
.\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --list
```
Window 4 - Run Kafka Producer (will provide a > prompt for writing messages)
```
.\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic bearcat-messages
```
Window 5 - Run Kafka Consumer (to show messages from the beginning)
```
.\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic bearcat-messages --from-beginning
```





