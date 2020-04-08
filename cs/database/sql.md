# SQL

## SQL tuning 

* execution plan 
* index invalidity 
* data skew

#### general principle

* 索引的列是出现在where子句中的列，或者连接子句中指定的列
* 更新频繁字段不适合创建索引
* 这些会抛弃使用索引：&gt;、&lt;、between、like、null、in、not in
* 多列索引，最左前缀匹配原则

