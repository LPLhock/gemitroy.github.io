# System Design

## 4S Principle

* Scienario
* * QPS: 100\(pc\) - 1k\(server/sql\) - 10k\(nosql\) - 1M\(mem\) 
* Service
* * Split 
* Storage
* * File/Sql/NoSql -&gt; Schema 
* Scale 

## News Feed system 

Pull: Timeline table More user Use cache Facebook/Twitter 

Push: NewsFeed table Less user Thundering Herd: pull\(is\_superstar\)+push 2-direction friendship pyq 

Pagination: Get the next 100 &lt;= previous timestamp 

Store Likes: Denormalize 

## Messaging system 

* Push: Socket 
* Pull
* poll

## Tiny Url system 

## User system 

DB + Cache 

Location based system 

## Google crawler / search

* web crawler service \(BFS\) 
* * robots
* web page storage 
* indexer 
* inverted index 
* query engine
* * goole suggestion / type ahead 

## Rate Limiter 

## Datadog

## GFS/HDFS 

Write once Read many times 

1 NameNode\(master\) + 1 Secondary NameNode\(helper/checkpoint\)+ DataNodes\(slave\) 

128M per block 

## BigTable 

## MapReduce 



