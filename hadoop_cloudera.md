## Tracking Drug Reactions on Hadoop, Marty Lurie Senior Systems Engineer at Cloudera ##
Slides

### Why Hadoop? ###

* HUE: GUI to view HDFS
* Data Mining: Spark, MAHOUT
* NoSQL: HBASE
* Solr Search
* Data integration: Apache Flume, Kafka
* Security: Kerberos, NavEncrypt
* APIs: HIVE, PIG, Impala, MapReduce
* Coordination/Scheduling* : Apache  OOZIE, Zookeeper
* Spark works better than MapReduce

Reduce -> Shuffle/Sort Mapper output -> Mapper -> HDFS

## HDFS ##

* 100 petabyte
* Fault tolerant
* Write once-read many
* Works with MapReduce, HBase, Impala, Cloudera, Search/Solr, Spark
* Directed acyclic graph - Spark, Tez

** Kudu **

* Insert/update/delete for hadoop
* Relational data model(SQL)
* Low latency(1ms read/write on SSD)
* High throughput(2x of Parquet)
* 90% speed of HBASE

** MapReduce **

* Reducer gets all keys in sorted order
* Reducer: Compare keys, if keys are same, add values.

** Spark **

* Spark: flatmap(), map(), reduceByKey()
* takeOrdered() - spits results out in sorted 
* Lazy evaluation - take(), collect()
* Python talks to Spark talks to Hadoop

## Drug Reactions use case ##

* Kafka(Apache Kafka is an open-source stream processing platform developed by the Apache Software Foundation written in Scala and Java. The project aims to provide a unified, high-throughput, low-latency platform for handling real-time data feeds.) producer - acts as the hospita
* chi square - check if the population samples are the same
