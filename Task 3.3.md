# Introduction
This document provides an overview of the model-based Time Series Management System (TSMS) ModelarDB which will be used for managing data in 6G-XCEL as described in the task description of Task 3.3. In addition, links to additional information about ModelarDB are provided.

# Task Description
The full task description is copied verbatim from 6G-XCEL Part B to the section below to make this document self-contained. In summary, Task 3.3 will be led by data management researchers at the Department of Computer Science at Aalborg University. The task will implement data management functionality in the Decentralised Multi-party, Multi-network AI (DMMAI) framework using ModelarDB. How ModelarDB will be extended for and integrated with DMMAI depends on the requirements specified in WP2. Thus, the work in Task 3.3 will be driven by the requirements of the other tasks in the 6G-XCEL project.

### *T3.3 Data abstraction and curation (M6-M24) Lead: AAU (CS), Contribution: HHI, DIENEKES*
*The data abstraction and curation tools within the DMMAI framework will be developed to consider different data types and needs for various controllers and their location in the network as well as the type of network. Requirements from WP2 will inform the development of these tools and the application to compressed extreme-scale time series will form an initial basis for these modules. This work will build on the MORE project platform to curate compressed time series data the model-based time series management system ModelarDB from AAU and the Incremental Machine Learning and Analytics (IMLA) platform from IBM.*

*One part of this topic concerns improving ModelarDB for the hard real-time stream processing requirements and domain specifics of 6G communication networks. ModelarDB is based on the concept of model-based lossy compression where mathematical functions (models), e.g., constants or lines, are fitted to time series data points within a specified maximum error bound. This compression is combined with a scalable distributed query processing engine to yield a unique combination of high compression, fast data ingestion, and scalable aggregate query processing. ModelarDB already spans edge and cloud but needs a tighter integration with the sensor and the wireless access. It also supports advanced compression, e.g., joint compression of correlated time series, but lacks models specifically aimed for communication data, which will be developed in this task.*

# ModelarDB History and Overview
The name ModelarDB has been used for two different open-source model-based TSMSs.

### ModelarDB Legacy
The first is a modular TSMS that interfaces existing query engines and data stores with a library with functionality for model-based time series management. The library is interfaced with Apache Spark, Apache Cassandra, Apache HDFS, and H2. The TSMS is implemented in a combination of Java and Scala. The name *ModelarDB Legacy* will be used for this TSMS as development of it stopped in 2022 and the last paper describing new functionality was published in 2023.

### ModelarDB
The second TSMS is an efficient TSMS designed for managing high-frequency time series across the edge and cloud using the lessons learned from *ModelarDB Legacy*. It is implemented in Rust and provides state-of-the-art lossless compression, lossy compression, and query performance by efficiently compressing time series using multiple different types of models such as constant and linear functions. As a result, high-frequency time series can be efficiently transferred over connections with limited bandwidth and stored at a low cost. The compressed time series can be efficiently queried using a relational interface and SQL without any knowledge about the model-based representation. A query optimizer automatically rewrites the queries to exploit the model-based representation. The TSMS also supports normal relational tables, e.g., for stoing metadata about the time series. The name *ModelarDB* will be used for this TSMS as it is currently under development and it will be used in 6G-XCEL.

# ModelarDB Repositories
ModelarData is a spin-out company from Aalborg University that focuses on making the open-source ModelarDB mature enough for real-world deployment and providing commercial support for it. Thus, while all of the ModelarDB code is open-source and released under version 2.0 of the Apache License, all of the repositories for ModelarDB and related libraries and tools are in the ModelarData GitHub organization.

### Source Code
- **[ModelarDB Legacy](https://github.com/ModelarData/ModelarDB):** Source code for ModelarDB Legacy which is no longer being developed.
- **[ModelarDB](https://github.com/ModelarData/ModelarDB-RS):** Source code for ModelarDB which is currently being developed and will be used in 6G-XCEL.
- **[Utilities](https://github.com/ModelarData/Utilities):** Utilities for simplifying development and testing of ModelarDB.
- **[PyModelarDB](https://github.com/ModelarData/PyModelarDB):** Python PEP 249 client for ModelarDB Legacy and ModelarDB.
- **[Telegraf-Output-Apache-Arrow-Flight](https://github.com/ModelarData/Telegraf-Output-Apache-Arrow-Flight):** Plugin for [Telegraf](https://www.influxdata.com/time-series-platform/telegraf/) so it can write data to ModelarDB.

### Documentation
- **[ModelarDB Installation Instruction](https://github.com/ModelarData/ModelarDB-RS/blob/main/docs/user/README.md#installation):** Installation instruction for FreeBSD, Linux, macOS, Windows.
- **[ModelarDB User Instruction](https://github.com/ModelarData/ModelarDB-RS/blob/main/docs/user/README.md):** Documentation for how to install and use ModelarDB.
- **[ModelarDB Development Instruction](https://github.com/ModelarData/ModelarDB-RS/blob/main/docs/dev/README.md):** Documentation for how to contribute to ModelarDB.
- **[ModelarDB Legacy and ModelarDB Papers](https://github.com/skejserjensen/ModelarDB#papers):** Links to published papers about ModelarDB Legacy and ModelarDB.
- **[ModelarDB Legacy and ModelarDB Presentations](https://github.com/skejserjensen/ModelarDB#presentations):** Links to presentations about about ModelarDB Legacy and ModelarDB.
