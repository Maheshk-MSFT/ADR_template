# **PBD - ADR001 - Title**

- Status: PROPOSED
- Deciders: `<name>`
- Last updated on: `<date>`

Technical Story: `<link story>`

- [Context and Problem Statement](#context-and-problem-statement)
- [Decision Drivers](#decision-drivers)
- [Considered Options](#considered-options)
- [Decision Outcome](#decision-outcome)
  - [Positive Consequences](#positive-consequences)
  - [Negative Consequences](#negative-consequences)
- [Pros and Cons of the Options](#pros-and-cons-of-the-options)
  - [Lambda architecture](#lambda-architecture)
  - [Kappa architecture](#kappa-architecture)
  - [Liquid](#liquid)
  - [SMACK](#smack)
  - [No up-front architectural pattern](#no-up-front-architectural-pattern)
- [Links](#links)

## **Context and Problem Statement**

Your current platform to ingest company data and provide refined data to Data Analysts and Data Scientists was born as a proof of concept that became early adopted in production by Data Engineers. Apart of different operational issues, it lacks an envisioned architecture to drive implementation decisions.

In order to provide a better platform to the company, which fits its needs in terms of reliability, scalability, security and ease to use, we need to consider all possible architecture archetypes of a big data ingestion and processing platforms.

## **Decision Drivers**

- Enable fast data ingestion
- Enable fast data access
- Enable different strategies for data processing and aggregating
- Ease to extend
- Minimize costs
- Enable data anonymization, when required
- Allow re-processing and re-creation of analytical layers
- Ease to implement
- Allow different data sources

## **Considered Options**

Following the conventions described in [1], we’ll consider the following options:

- Lambda architecture
- Kappa architecture
- Liquid
- SMACK
- No up-front architectural pattern

## **Decision Outcome**

- Chosen option: **Kappa architecture**

We understand Kappa architecture might fit best our need based on the movement towards restricting direct access to product teams databases, ruling out Lambda as a viable option. The new architecture should follow design rules of an evolutionary architecture but we understand it’s important to have a well defined direction for it instead of open the possibility of ad hoc decisions provided by no up-front architectural pattern.

Also, this architectural pattern doesn’t change much of the abstractions users are currently using and could ingest and serve data in near-real time fashion, regardless of the data sources since data would be treated as events and there’s good options in the wild to fast process and distribute these.

Liquid architecture might be an option in the future but that would require a twist in your current mindset in the data teams which we cannot afford at this moment. We also are not facing strict real time data access requirements to justify its complexity.

Although SMACK provide us a starting point in terms of implementation, we don’t need its stack is the best one to fit our needs. Also, we’re considering the data analysis as part of our data consumers concerns and outside on our data platform scope.

### **Positive Consequences**

- Moving the company towards an event-driven architecture
- Centralizing data input
  - Enabling pipeline for automatic data anonymization
- Reducing the time ingested data lands into our Data Lake for those currently using batch jobs
- Keeping the same high level abstractions used for those jobs using streaming
- Delimiting the platform scope behind the boundaries of a data hub
- Enabling data product teams to focus on the processing routines needed to extract value from data rather than spend time on data ingest processes

### **Negative Consequences**

- Product teams might require help on develop change data capture strategies to publish their data into our new platform
- Platform should support all different data sources
- We might need to reconsider estimates around usages on our event hub cluster since throughput will increase
  - Or even consider a different product
- Batch jobs might need to be refactored or rewritten

## **Pros and Cons of the Options**

### **Lambda architecture**

The Lambda architecture is organized into three different layers: batch, speed and serving layers.

- Good, because it doesn’t change much the abstractions our users already have
- Good, because it put less effort in terms of changes for our platform users in their own domain
- Good, because there’s lots of JDBC libraries for our existent requirements, leading to less time to market extraction pipelines
- Bad, because it breaks the bounded contexts for transactional (micro)services to access directly the database
- Bad, because it implies on keep multiple codebases for data ingestion
- Bad, because adds complexity to have the batch and streaming data persisted into the same database into the Data Lake
- Bad, because it might require to merge data in the Data Lake if batch and streaming processing put data into different databases
- Bad, because it might lead to more costs, if batch and streaming data needs to be stored into different databases in the Data Lake

### **Kappa architecture**

The Kappa architecture merges the batch and speed layers into a single one.

- Good, because there’s a single source of data into the platform as every scenario is treated as stream of events, leading to less complexity
- Good, because there’s no need to keep multiple codebases since data ingestion is standardized
- Good, because it abstracts all data sources and keep its resources into a bounded context
- Good, because there are solid (open source) technologies to read and process streaming events with high performance
- Bad, because it might require changes on the transaction systems, as they need to publish events
- Bad, because the overall architecture is more complex dealing with asynchronous events

### **Liquid**

The Liquid architecture uses two layers - processing and messaging - using the messaging layer for both ingest data from sources and providing data for the Big Data applications.

- Good, because there’s a single source of data into the platform as every scenario is treated as stream of events, leading to less complexity
- Good, because there’s no need to keep multiple codebases since data ingestion is standardized
- Good, because it abstracts all data sources and keep its resources into a bounded context
- Good, because there are solid (open source) technologies to read and process streaming events with high performance
- Good, because it’s designed for low latency data access
- Bad, because it might require changes on the transaction systems, as they need to publish events
- Bad, because the overall architecture is more complex dealing with asynchronous events
- Bad, because it forces all big data applications to use streaming as their data input mechanism
- Bad, because it might uses more storage space, since it doesn’t relies in a single copy of the data (every data is moved around in different topics, depending on the use cases)

### **SMACK**

"The acronym SMACK stands for the frameworks Apache Spark, Apache Mesos, Akka, Apache Cassandra and Apache Kafka" [1]

- Good, because process data in real time
- Good, because it’s thought with high availability principles
- Good, because it uses layers to define responsibilities
- Bad, because it doesn’t enforce a strict architectural patterns; it’s rather a technology stack
- Bad, because it requires knowledge on tools we don’t currently uses like Mesos or Akka
- Bad, because can introduce more complexity in terms on using the platform which heavily relies in advanced concurrency concepts

### **No up-front architectural pattern**

- Good, because it’s the simplest solution at this moment
- Good, because it permits postpone the discussion and evolve the architecture as we learn more about requirements
- Bad, because it doesn’t enforce a clear path for all users of our platform
- Bad, because it can lead to several strategies to ingest and process data, requiring major refactors on teams without bandwidth to absorb that effort

## **Links**

1. Big Data architecture patterns
   [HORGAS, Tim. ”Benchmarking of Big Data Architecture Trade-Offs”. 2016.](https://users.informatik.haw-hamburg.de/~ubicomp/projekte/master2016-hsem/horgas/bericht.pdf)
1. <https://www.oreilly.com/radar/questioning-the-lambda-architecture/>
1. <https://databricks.com/blog/2020/01/30/what-is-a-data-lakehouse.html>
