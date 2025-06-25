# Readings in Stream Processing

A list of essential articles to understand stream processing, including continuously querying and maintaining time-series data.

## Books 

- [Designing Data Intensive Applications. The Big Ideas Behind Reliable, Scalable, and Maintainable Systems. Martine Kleppmann](https://www.oreilly.com/library/view/designing-data-intensive-applications/9781491903063/) This is a book we've been waiting for 10 years. A definitive guide for entering the field of distirbuted systems and stream data processing. This book covers fundamental concepts, techniques, and challenges in keep processing large volumes of data continously. 
   -  Japanese translation of the book 「[データ指向アプリケーションデザイン](https://amzn.to/3I40Pkk)」 is also available
- [Streaming Systems: The What, Where, When, and How of Large-Scale Data Processing](https://www.amazon.co.jp/Streaming-Systems-Large-Scale-Processing-English-ebook/dp/B07FMDY5CC/) A book by the authors of Streaming 101, Spark Streaming. This book introduces how we can unify batch processing and stream processing within a single system and covers the basic ideas of Stream SQL. 

## Programming Models for Stream Processing 

- [One SQL to Rule Them All. Edmon Begoli, Tyler Akidau, Fabian Hueske, Julian Hyde, Kathryn Knight, Kenneth Knowles SIGMOD 2019](https://arxiv.org/abs/1905.12133) A proposal to extend the current SQL semantics to support both batch and stream processing by adding time-varying relations (TVR), event time, and materialization control.
- [DryadLINQ: A System for General-Purpose Distributed Data-Parallel Computing Using a High-Level Language. Y. Yu, et al. OSDI08](https://www.usenix.org/legacy/event/osdi08/tech/full_papers/yu_y/yu_y.pdf) The origin of declarative data processing operators (e.g., map, filter, groupBy, etc.) in modern programming languages. 
- [OpenMessaging:Common Use Cases](https://github.com/openmessaging/specification/blob/master/usecase.md) Illustrations of typical stream processing patterns from OpenMessaging.
- [The world beyond batch: Streaming 101](https://www.oreilly.com/ideas/the-world-beyond-batch-streaming-101). An article written by the author of Google Dataflow. Streaming is actually a superset of batch processing for unbounded data. This article explains what is unbounded data and how to manage late coming data. You can also learn what streaming systems can do and can't do, and the differences of event times and processing times, and varieties of time-window based processing. 
- [Structured Streaming: A Declarative API for Real-Time Applications in Apache Spark. SIGMOD2018](https://cs.stanford.edu/~matei/papers/2018/sigmod_structured_streaming.pdf). A good summary of challenges around continous stream processing and unifying APIs for batch and stream processing. 
  - [Discretized Streams: Fault-Tolerant Streaming Computation at Scale. NSDI 2013](https://people.csail.mit.edu/matei/papers/2013/sosp_spark_streaming.pdf) An approacy for applying micro-batch style stream processing in Spark. This model has been redesigned in Spark 2.0 as [Structured Streaming](https://spark-summit.org/2017/events/easy-scalable-fault-tolerant-stream-processing-with-structured-streaming-in-apache-spark/). 
  - [Continuous Applications: Evolving Streaming in Apache Spark 2.0](https://databricks.com/blog/2016/07/28/continuous-applications-evolving-streaming-in-apache-spark-2-0.html)
- [Drizzle: Fast and Adaptable Stream Processing at Scale. SOSP 2017](http://shivaram.org/publications/drizzle-sosp17.pdf) An approach for reducing the overhead of the coordination between stream processing tasks. 
- [Dataflow/Beam & Spark: A Programming Model Comparison](https://cloud.google.com/dataflow/blog/dataflow-beam-and-spark-comparison)
- [ReactiveX](http://reactivex.io/). Stream processing patterns for functional programming.
- [Akka Stream](https://doc.akka.io/docs/akka/2.5/stream/index.html) Stream processing DSL for Akka 
- [A Practical Guide to Selecting A Stream Processing Technology](http://www.slideshare.net/ConfluentInc/a-practical-guide-to-selecting-a-stream-processing-technology). A good explanation of stream processing
- [Trill: A High-Performance Incremental Query Processor for Diverse Analytics. B. Chandramouli, et al. VLDB 2014](https://www.microsoft.com/en-us/research/publication/trill-a-high-performance-incremental-query-processor-for-diverse-analytics/)

## Table Catalog for Stream Processing

- [Delta Lake: High-Performance ACID Table Storage over Cloud Object Stores](https://www.databricks.com/jp/wp-content/uploads/2020/08/p975-armbrust.pdf) Utilizing scalable object strage on the cloud (e.g., S3), [Delta Lake](https://github.com/delta-io/delta) provides a single table format with versioning (time-travel) and transaction support.
- [Iceberg](https://iceberg.apache.org/) 
- [Big Metadata: When Metadata is Big Data. (VLDB 2021)](http://vldb.org/pvldb/vol14/p3083-edara.pdf) Columnar table catalog with partition statistics used in Google's BigQuery. 
- [Unity Catalog: Open and Universal Governance for the Lakehouse and Beyond (SIGMOD Companion 2025)](https://dl.acm.org/doi/10.1145/3722212.3724459)
- [Apache Hudi](https://hudi.apache.org/) Apach Hudi provides [a file layout](https://hudi.apache.org/tech-specs) for placing both streaming and batch data processing with a transaction support. You can merge fragmented partition data or use it as is for faster real-time data processing. Previously, it was called [Uber Hoodie](https://github.com/uber/hoodie)


## Watermark Management for Stream Processing

- [The Dataflow Model: A Practical Approach to Balancing Correctness, Latency, and Cost in Massive-Scale, Unbounded, Out-of-Order Data Processing. Akidau et al., (Google) VLDB 2015](http://www.vldb.org/pvldb/vol8/p1792-Akidau.pdf) The original paper of [Google Cloud Dataflow](https://cloud.google.com/dataflow/), which describes how we can cope with the delay of data arrival (late-coming data) and periodical data processing in a unified API for batch and stream processing. You can also find a summary of this paper at [the morning paper](https://blog.acolyer.org/2015/08/18/the-dataflow-model-a-practical-approach-to-balancing-correctness-latency-and-cost-in-massive-scale-unbounded-out-of-order-data-processing/)
- [Watermarks in Stream Processing Systems: Semantics and Comparative Analysis of Apache Flink and Google Cloud Dataflow. VLDB 2021](http://vldb.org/pvldb/vol14/p3135-begoli.pdf). Describes basic definitions of watermarks and shows challenges and trade-offs in managing watermarks. 
- [Watermarking in stream processing | Course in Spark Structured Streaming 3.0 | Lesson 7](https://www.youtube.com/watch?v=XjlKGvUt2dY) A good tutorial explaining the notions of stream processing and watermark management.

## Workload Optimization

- [Towards a Learning Optimizer for Shared Clouds (VLDB 2019)](http://www.vldb.org/pvldb/vol12/p210-wu.pdf). Estimate cardinality models from the previous job executions in order to optimize the overall workloads. This work uses the multi-layer perceptron (MLP) neural network for learning models from query exeuction features (e.g., job name, input cardinality, average row length, input dataset names, etc.)
- [CrocodileDB: Efficient Database Execution through Intelligent Deferment (CIDR 2020)](http://cidrdb.org/cidr2020/papers/p14-shang-cidr20.pdf) This paper introduces Intermittent Query Processing (IQP) approach for utilizing the knowledge about new data, query semantics, and users' expectation together to reduce the overall processing cost. It uses Deep Q-Materialization (DQM) to make a tradeoff under a certain resource constraint (e.g., memory, CPUs, storage) to decide how much data will be cached, pre-computed, pre-loaded, etc.
- [Peregrine: Workload Optimization for Cloud Query Engines (SOCC 2019)](https://dl.acm.org/doi/10.1145/3357223.3362726) Analyzing the workload of historical queries and optimize recurrring queries, similar queries, and coordinating queries by extracing common subexpressions that can be materialized. To support various query engines including Spark, Microsoft has creaetd a common intermediate representation (IR) of workloads.
- [Computation reuse via fusion in Amazon Athena (ICDE 2022)](https://www.amazon.science/publications/computation-reuse-via-fusion-in-amazon-athena) Query-rewrite optimization to merge multiple table scans between subqueries into a single table scan, which is available in Amazon Athena. Support for Trino is also coming [trino#15690](https://github.com/trinodb/trino/issues/15690)

## Iterative Data Processing
- [Olston, C. et al. 2011. Nova: continuous Pig/Hadoop workflows. (Jun. 2011)](http://infolab.stanford.edu/~olston/publications/sigmod11.pdf)
- [Naiad: A Timely Dataflow system (SOSP13 best paper)](https://www.microsoft.com/en-us/research/wp-content/uploads/2013/11/naiad_sosp2013.pdf) Differential data processing developed in Microsoft. [Niad Project Page](https://www.microsoft.com/en-us/research/project/naiad/) The proposed approach is now implemented in Rust [Timely Dataflow](https://github.com/timelydataflow/timely-dataflow)
- [Apache Flink: Spinning Fast Iterative Data Flows. PVLDB 2012](http://stratosphere.eu/assets/papers/spinningFastIterativeDataFlows_12.pdf)

## Incremental Processing

- [DBSP: Automatic Incremental View Maintenance for Rich Query Languages (VLDB 2023 Best Paper)](https://arxiv.org/abs/2203.16684) By introducing Integration (I) and Differentiation (D) operators, DBSP allows the composition of complex incremental SQL queries, including joins, aggregations, recursive loops, etc. 
- [Keep Your Distributed Data Warehouse Consistent at a Minimal Cost (PACMMOD 2023)](https://dl.acm.org/doi/10.1145/3589770) Proposes a method for maintaining consistency in large data warehouses while minimizing updates. It solves a dynamic programming problem to balance computational cost and data freshness. Implemented at the YouTube Data Warehouse, the method has cut update requests by 25% by removing non-trivial duplicates, significantly saving computing resources. 
- [What’s the Difference? Incremental Processing with Change Queries in Snowflake (ACM Management of Data 2023)](https://dl.acm.org/doi/10.1145/3589776) Snowflake introduces CHANGE queries and STREAM table objects to subscribe changes in the table. 
- [dbt: Incremental Models](https://docs.getdbt.com/docs/build/incremental-models) dbt, a tool for compiling a sequence of queries from SQL templates, supports a simple incremental processing with conditional switch of SQL queries. 

### Incremental Processing with Materialized Views
- [DBToaster: Higher-order Delta Processing for Dynamic, Frequently Fresh Views (VLDB 2012)](http://vldb.org/pvldb/vol5/p968_yanifahmad_vldb2012.pdf). An efficient way for finding the delta of delta queries (higher-order delta) for computing materialized views as we receive a new update record. A demo source code written in OCaml and Scala can be found in https://github.com/dbtoaster
- [How to Win a Hot Dog Eating Contest: Distributed Incremental View Maintenance with Batch Updates M. Nicolik et al. (SIGMOD 2016)](https://www.cs.ox.ac.uk/files/9133/sigmod2016-dbtoaster-batching_divm.pdf) Extending DBToaster for batch and distributed incremental view maintenance setting. 
- [Generalized Scale Independence Through Incremental Precomputation. M. Armbrust, et al. SIGMOD 2013](http://dl.acm.org/citation.cfm?id=2465333) An approach for guaranteeing the response time of queries by classifying query types and preparing materialized views if necessary.
- [Comet: batched stream processing for data intensive distributed computing (SoCC 10)](https://www.microsoft.com/en-us/research/publication/comet-batched-stream-processing-for-data-intensive-distributed-computing/) A basic style of incremental processing
- [Continuous queries over append-only databases. SIGMOD 1992](http://www.cs.brandeis.edu/~cs227b/papers/pubsub/TGNO92-Continuous.pdf)
- [Selecting Subexpressions to Materialize at Datacenter Scale. PVLDB 2018](http://www.vldb.org/pvldb/vol11/p800-jindal.pdf) Microsoftr SCOPE - Automatically finding common sub-expressions among queries and materializing their results for reducing the overhead of recurrent queries.
- [Tempura: A General Cost-Based Optimizer Framework for Incremental Data Processing (VLDB 2020)](https://arxiv.org/abs/2009.13631) A cost-based optimizer for choosing the right incremental processing methods. A demo [source code](https://github.com/alibaba/cost-based-incremental-optimizer) extending Apache Calcite is available. 
- [Napa: Powering Scalable Data Warehousing with Robust Query Performance at Google. VLDB 2021](http://vldb.org/pvldb/vol14/p2986-sankaranarayanan.pdf) Control the timing of eager materialization of queries based on the user's requirements (Favor freshness or performance)
- [Amazon Redshift: Automatic Query Rewriting with Materialized Views](https://docs.aws.amazon.com/redshift/latest/dg/materialized-view-auto-rewrite.html) 
- [Big Query: Smart tuning](https://cloud.google.com/bigquery/docs/materialized-views-use) BigQuery automatically rewrites queries to use materialized views whenever possible. Automatic rewriting improves query performance and cost, and does not change query results.
- [OpenIVM: a SQL-to-SQL Compiler for Incremental Computations (SIGMOD-Companion 2024)](https://dl.acm.org/doi/10.1145/3626246.3654743) Implements incremental view maintenance (IVM) at the SQL level, implemented as a DuckDB extension ([source code]( https://github.com/ila/duckdb/tree/rdda/extension/openivm))
- [Incremental Refresh for Materialized Views (Databricks)](https://docs.databricks.com/en/optimizations/incremental-refresh.html)

## Stream Log Collection Systems
- [Fluentd](https://www.fluentd.org/) A unified logging layer from various data sources.
- [Kafka](https://kafka.apache.org/) is often used for providing _replayable_ streaming data sources.
- [Apache Pulsar](https://pulsar.incubator.apache.org/) A distributed pub-sub messaging system originally
created at Yahoo!
- [OpenMessaging](https://github.com/openmessaging) Cloud-oriented, simple, flexible, vendor-neutral and language-independent standards for messaging
- [Uber Hoodie](https://github.com/uber/hoodie) Hybrid storage: Avro for streaming import, Parquet for analysis. This project has been moved to [Apache Hudi](https://hudi.apache.org/)
- [MQTT](http://mqtt.org/) A machine-to-machine (M2M)/"Internet of Things" connectivity protocol.
- [Robust, Scalable, Real-Time Event Time Series Aggregation at Twitter. SIGMOD2018](https://cs.uwaterloo.ca/~jimmylin/publications/Yang_etal_SIGMOD2018.pdf)
  - [Twitter Heron: Stream Processing at Scale. SIGMOD 2015](http://dl.acm.org/citation.cfm?id=2742788)
  - [The Unified Logging Infrastructure for Data Analytics at Twitter. VLDB 2012](http://vldb.org/pvldb/vol5/p1771_georgelee_vldb2012.pdf)
- [Questioning the Lambda Architecture](https://www.oreilly.com/ideas/questioning-the-lambda-architecture) A commonly used architecture for managing recent data and archived data. However combining two types of systems for batch and streaming is still painful because analysts need to understand both systems (e.g, Hadoop + Storm, Spark + Spark Streaming, Kafka + other data store)

## Real-Time Stream Processing
Real-time stream processing usually means ultra-low latency applications to satisfy SLAs for returning results in a few seconds.

- [The Stratosphere Platform for Big Data Analytics](http://stratosphere.eu/assets/papers/2014-VLDBJ_Stratosphere_Overview.pdf). Stratospher is a former name of [Apache Flink](https://flink.apache.org/).
- [The 8 Requirements of Real-Time Stream Processing. M. Stonebraker, et al. SIGMOD Record 2005](http://cs.brown.edu/~ugur/8rulesSigRec.pdf). A summary is also available in [the morning paper](https://blog.acolyer.org/2014/12/03/the-8-requirements-of-real-time-stream-processing/)
- [MacroBase: Prioritizing Attention in Fast Data. P. Bailis, et al. SIGMOD 2017](http://www.bailis.org/papers/macrobase-sigmod2017.pdf). A data analytics engine that prioritizes end-user attention in high-volume fast data streams.
  - A prototype implementation on [GitHub](https://github.com/stanford-futuredata/macrobase)
 
## Stream SQL
- [Foundations of Streaming SQL](http://s.apache.org/streaming-sql-strata-nyc) by Tyler Akidau. Good illustrations for understanding how regular table-based SQL and streaming SQL are different.
- [Microsoft Azure Stream Analytics](https://azure.microsoft.com/en-us/services/stream-analytics/)
- [Norikra](http://norikra.github.io/) Schema-less Stream Processing with SQL
- [Esper](http://www.espertech.com/esper/)
- [KSQL](https://github.com/confluentinc/ksql) A Streaming SQL Engine for Apache Kafka

## GitHub Projects
- [OpenMessaging](https://github.com/openmessaging)
- [Apache Beam](https://github.com/apache/beam) A unified model for defining both batch and streaming data-parallel processing pipelines.
  - It was [Google Dataflow Open source API for Java](https://github.com/GoogleCloudPlatform/DataflowJavaSDK)
- [spotify/scio: A Scala API for Google Cloud Dataflow](https://github.com/spotify/scio)
- [twitter/heron](https://github.com/twitter/heron)
- [Microsoft Naiad](https://github.com/MicrosoftResearch/Naiad)
- [Norikra](http://norikra.github.io/)
- [KSQL](https://github.com/confluentinc/ksql)
- [Apache Apex](https://apex.apache.org/) Unified stream and batch processing engine.

## Commercial Services
### Stream Ingestion
- [Azure Event Hubs](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-what-is-event-hubs)
- [AWS Kinesis Streams](https://aws.amazon.com/kinesis/data-streams/)
- [Google Cloud Pub/Sub](https://cloud.google.com/pubsub/)

## External Lists
- List of projects related to stream-processing: https://github.com/manuzhang/awesome-streaming
