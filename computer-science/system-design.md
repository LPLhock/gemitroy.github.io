# System

## Micro Service 

* RPC 
* REST
* Docker 
* Service discovery 

## Cache

Consistent hashing 

## load balance 

### Implementation 

#### Transport layer \(hardware\) 

#### Nginx 

#### Application layer 

* round-robin 
* serverId=userId.hashcode\(\)%server.size\(\) 
* stateless 
* session persist 

## MQ

### Kafka

message storage \[topic-partition\_$\] 

* segment\_001.index \(an index\) 
* segment\_001.log \(message payload\)

producer-centric, log file 

### RabbitMQ/ActiveMQ

broker-centric

memory

## Distributed

Zookeeper 

Hadoop/Yarn 

Spark 

## CAP theorem

