## AWS Services for Batch Pipelines
### Batch Processing Overview
- **ETL Pipelines**: A common architecture for batch processing is an ETL (Extract, Transform, Load) pipeline, where data is ingested from a source, transformed, and then loaded into storage for analysis or machine learning.

### Source Systems
- **Amazon Relational Database Service (RDS)**: RDS is a typical source system for tabular data. It provides a managed database environment with engines like MySQL and PostgreSQL.

### Ingestion and Transformation Options
- **Amazon EC2**: You could write scripts and manage everything on your own using an EC2 instance, but this leads to managing servers, updates, and security. This is often considered undifferentiated heavy lifting, and may not be the best use of time.
    
- **Serverless Options**: The recommended approach for batch processing is to look at serverless services first, then move to containers or servers if needed.
    
    - **AWS Lambda**: A serverless function service that can be used to run code in response to events. However, Lambda has limitations like a 15-minute timeout and limited memory/CPU allocation, which can make it unsuitable for larger or long-running ETL tasks.
    - **Amazon Glue ETL**: A serverless ETL service that simplifies the process of extracting, transforming, and loading data. Glue provides features like crawlers that automatically detect and catalog data, and it includes a visual ETL tool to design pipelines with minimal code.
    - **Amazon EMR Serverless**: A more customizable, scalable option compared to Glue ETL. EMR supports frameworks like Apache Spark and Apache Hive, providing flexibility for large-scale analytics and custom components. It offers more control but requires more management compared to Glue ETL.

### Storage and Serving Options
- **Amazon RDS**: Suitable for serving structured data that has been normalized and transformed into a relational format. It’s an effective option for traditional analytics workflows.
- **Amazon Redshift**: A powerful data warehouse designed for complex analytical queries on massive datasets. While more expensive than RDS, it provides advanced features for data analysis at scale.
- **Amazon S3**: A flexible, cost-effective option for storing and serving data, especially for machine learning use cases. S3 is commonly used as a staging area in data pipelines due to its scalability and integration with other AWS services. Data is stored in buckets, which are containers for objects that can be used at various pipeline stages.

## AWS Services for Streaming Pipelines
When working with **streaming data** on AWS, you'll need to choose the right tools to handle real-time data ingestion, transformation, and storage. Here are some key AWS services for supporting streaming workloads:

#### AWS Streaming Services:
1. **Amazon Kinesis Data Streams**:
    
    - **Purpose**: Real-time data ingestion and streaming data processing.
    - **How it works**: Data producers send data (like logs, IoT data, or clickstreams) to Kinesis streams. The data can be pulled by consumers (such as applications or storage services) in real time.
    - **Key Features**: Data can be held for a configurable amount of time (minimum 24 hours), and multiple consumers can process the same stream for different use cases.
    - **Use Cases**: Real-time analytics, data storage, or event-driven processing.
2. **Amazon Managed Streaming for Apache Kafka (MSK)**:
    
    - **Purpose**: Managed service for Apache Kafka, a widely used open-source streaming platform.
    - **How it works**: MSK manages the underlying infrastructure for running Kafka, while users interact with Kafka topics to produce and consume data.
    - **Key Features**: MSK supports all Kafka-compatible tools and provides flexibility for users already familiar with or using Kafka.
    - **Use Cases**: For teams with existing Kafka infrastructure or those requiring more control over their streaming architecture.

#### Kinesis Data Streams vs MSK:
- **Kinesis**: Easier to use, requires less operational overhead, and is a good choice for those new to streaming architectures.
- **MSK**: Provides more control and is better suited for teams with Kafka experience or advanced customization needs.

#### AWS Data Firehose:
- **Purpose**: Simplifies the process of moving streaming data to destinations like Amazon S3, Redshift, HTTP endpoints, or third-party services like DataDog or Splunk.
- **How it works**: Firehose can integrate with Kinesis Data Streams or other AWS sources to automatically move data to the desired destination without needing custom code.
- **Use Cases**: Ideal for automatically storing data from streams in S3, Redshift, or other destinations without writing custom ingestion code.
