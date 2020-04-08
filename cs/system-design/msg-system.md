# Messaging System

## Kafka

message storage \[topic-partition\_$\] 

* segment\_001.index \(an index\) 
* segment\_001.log \(message payload\)

producer-centric, log file 

acks: 

```text
0: immediately acknowledge without any broker commit 
1: acknowledge after leader commit 
all: acknowledge after all in-sync replicas commit
```

default at-least-once

### Exactly once semantics

#### Producer:

```text
enable.idempotence: true
transactional.id: id-1
isolation.level: read_committed
```

How kafka achieve idempotent:  by send a sequence number together with message

#### Consumer:

To avoid msg duplicate: store topic offset in consumer side db or cache.

### Terms

* Consumer Group
  * A topic can be consumed by only 1 consumer in a Consumer Group
* Partition
  * Split of topic. Message of a topic split and send a partition 
* Replication
  * Duplication of each partition

## RabbitMQ/ActiveMQ

broker-centric

memory

## Kafka VS. RabbitMQ

#### Kafka: 

* Sequential IO
* High throughput with less node Multi consumer by design. And can read from different offset of the same partition
* Message ordering at partition level
* Message persistence can be forever, decided by retention period Stream processing Producer message acknowledgement Replication Exactly once delievery Pull model

#### RabbitMQ: 

* Flexiible routing to topic/queue, including wildcard and pattern 
* Message priority 
* Push model

