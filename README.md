# Readings in Stream Processing

A list of articles that are essential to understand stream processing.

## Programming Models for Stream Processing 
- [The world beyond batch: Streaming 101](https://www.oreilly.com/ideas/the-world-beyond-batch-streaming-101). An article written by the author of Google Dataflow. Streaming is actually a superset of batch processing for unbounded data. This article explains what is unbounded data and how to manage late coming data. You can also learn what streaming systems can do and can't do, and the differences of event times and processing times, and varieties of time-window based processing. 
- [The Dataflow Model: A Practical Approach to Balancing Correctness, Latency, and Cost in Massive-Scale, Unbounded, Out-of-Order Data Processing. Akidau et al., (Google) VLDB 2015](http://www.vldb.org/pvldb/vol8/p1792-Akidau.pdf) The original paper of [Google Cloud Dataflow](https://cloud.google.com/dataflow/), which describes how we can cope with the delay of data arrival (late-coming data) and periodical data processing in a unified API for batch and stream processing. You can also find a summary of this paper at [the morning paper](https://blog.acolyer.org/2015/08/18/the-dataflow-model-a-practical-approach-to-balancing-correctness-latency-and-cost-in-massive-scale-unbounded-out-of-order-data-processing/)
- [Dataflow/Beam & Spark: A Programming Model Comparison](https://cloud.google.com/dataflow/blog/dataflow-beam-and-spark-comparison)
- [ReactiveX](http://reactivex.io/). Stream processing patterns for functional programming.
- [A Practical Guide to Selecting A Stream Processing Technology](http://www.slideshare.net/ConfluentInc/a-practical-guide-to-selecting-a-stream-processing-technology). A good explanation of stream processing

## Iterative Data Processing
- [Olston, C. et al. 2011. Nova: continuous Pig/Hadoop workflows. (Jun. 2011)](http://infolab.stanford.edu/~olston/publications/sigmod11.pdf)
- [Naiad: A Timely Dataflow system (SOSP13 best paper)](https://cs.stanford.edu/~matei/courses/2015/6.S897/readings/naiad.pdf) Differential data processing developed in Microsoft. [Niad Project Page](https://www.microsoft.com/en-us/research/project/naiad/)
- [Apache Flink: Spinning Fast Iterative Data Flows. PVLDB 2012](http://stratosphere.eu/assets/papers/spinningFastIterativeDataFlows_12.pdf)

## Incremental Processing with Materialized Views
- [DBToaster: Higher-order Delta Processing for Dynamic, Frequently Fresh Views (VLDB 2012)](http://vldb.org/pvldb/vol5/p968_yanifahmad_vldb2012.pdf). An approach for incremental view maintenance involving complex queries.
- [How to Win a Hot Dog Eating Contest: Distributed Incremental View Maintenance with Batch Updates M. Nicolik et al. (SIGMOD 2016)](https://www.cs.ox.ac.uk/files/9133/sigmod2016-dbtoaster-batching_divm.pdf) An efficient way for finding delta of delta queries for computing materialized views. For example, computing delta for select distinct x doesn't improve the query performance, so that we should avoid incremental processing for this kinds of queries.
- [Generalized Scale Independence Through Incremental Precomputation. M. Armbrust, et al. SIGMOD 2013](http://dl.acm.org/citation.cfm?id=2465333) An approach for guaranteeing response time of queries by classifying query types and preparing materialized views if necessary.
- [Comet: batched stream processing for data intensive distributed computing (SoCC 10)](https://www.microsoft.com/en-us/research/publication/comet-batched-stream-processing-for-data-intensive-distributed-computing/) A basic style of incremental processing
- [Continuous queries over append-only databases. SIGMOD 1992](http://www.cs.brandeis.edu/~cs227b/papers/pubsub/TGNO92-Continuous.pdf)

## Stream Log Collection
- [Questioning the Lambda Architecture](https://www.oreilly.com/ideas/questioning-the-lambda-architecture) A commonly used architecture for managing recent data and archived data. However combining two types of systems for batch and streaming is still painful because analysts need to understand both systems (e.g, Hadoop + Storm, Spark + Spark Streaming, Kafka + other data store)
- [Dataflow model](http://www.vldb.org/pvldb/vol8/p1792-Akidau.pdf) is a unified API for batch and streaming, but the stream data processing problem is fundamentally complex. Writing correct code is still difficult even for experts. 
- [The Unified Logging Infrastructure for Data Analytics at Twitter. VLDB 2012](http://vldb.org/pvldb/vol5/p1771_georgelee_vldb2012.pdf)
- [Uber Hoodie](https://github.com/uber/hoodie) Hybrid storage: Avro for streaming import, Parquet for analysis

## Stream SQL
- [Microsoft Azure Stream Analytics](https://azure.microsoft.com/en-us/services/stream-analytics/)
- [Norikra](http://norikra.github.io/) Schema-less Stream Processing with SQL
- [Esper](http://www.espertech.com/esper/)
- [KSQL](https://github.com/confluentinc/ksql) A Streaming SQL Engine for Apache Kafka

## Real-Time Stream Processing
Real-time stream processing usually means ultra-low latency applications to satisfy SLAs for returning results in a few seconds.
- [The 8 Requirements of Real-Time Stream Processing. M. Stonebraker, et al. SIGMOD Record 2005](http://cs.brown.edu/~ugur/8rulesSigRec.pdf). A summary is also available in [the morning paper](https://blog.acolyer.org/2014/12/03/the-8-requirements-of-real-time-stream-processing/)
- [The Stratosphere Platform for Big Data Analytics](http://stratosphere.eu/assets/papers/2014-VLDBJ_Stratosphere_Overview.pdf). Strasospher is a former name of [Apache Flink](https://flink.apache.org/).
- [Discretized Streams: Fault-Tolerant Streaming Computation at Scale. NSDI 2013](https://people.csail.mit.edu/matei/papers/2013/sosp_spark_streaming.pdf) An approacy for applying micro-batch style stream processing in Spark. This model has been redesigned in Spark 2.0 as [Structured Streaming](https://spark-summit.org/2017/events/easy-scalable-fault-tolerant-stream-processing-with-structured-streaming-in-apache-spark/). 
  - [Continuous Applications: Evolving Streaming in Apache Spark 2.0](https://databricks.com/blog/2016/07/28/continuous-applications-evolving-streaming-in-apache-spark-2-0.html)
- [Twitter Heron: Stream Processing at Scale. SIGMOD 2015](http://dl.acm.org/citation.cfm?id=2742788)

## GitHub Projects
- [Google Dataflow Open source API for Java](https://github.com/GoogleCloudPlatform/DataflowJavaSDK)
- [spotify/scio: A Scala API for Google Cloud Dataflow](https://github.com/spotify/scio)
- [twitter/heron](https://github.com/twitter/heron)
- [Microsoft Naiad](https://github.com/MicrosoftResearch/Naiad)
- [Norikra](http://norikra.github.io/)
- [KSQL](https://github.com/confluentinc/ksql)

## External Lists
- List of projects related to stream-processing: https://github.com/manuzhang/awesome-streaming
