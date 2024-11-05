## Different Types of Source Systems
#### Types of Data

-  **Structured Data**
	- Organized in tables with rows and columns.
	- Examples: relational databases, CSV files.

- **Semi-Structured Data**
	- Not tabular but still has some organizational structure.
	- Commonly in formats like JSON (key-value pairs) and XML.

- **Unstructured Data**
	- No predefined structure; includes free text, images, audio, and video.
	- Examples: documents, images, or any multimedia content.

#### Types of Source Systems

- **Databases**
    - Use CRUD operations (Create, Read, Update, Delete).
    - **Relational Databases**: Store data in tables, typically used for structured data.
    - **NoSQL Databases**: Non-tabular, handle semi-structured or unstructured data.

- **Files**
    - Store information in a sequence of bytes, suitable for structured, semi-structured, and unstructured data.
    - Common file formats include CSV (structured), JSON/XML (semi-structured), and multimedia files (unstructured).

- **Streaming Systems**
    - Provide continuous data flow as real-time messages/events.
    - Examples include message queues or platforms like **Amazon Kinesis** or **Apache Kafka**.
    - Often used with event-driven data from sources like IoT devices, user interactions, or system logs.

## Relational Databases

A relational database is a collection of information that organizes data in predefined relationships where data is stored in one or more tables (or "relations") of columns and rows.
#### Key Concepts

- **Normalization**:
    - Breaks data into multiple tables to **reduce redundancy** and **maintain integrity**.
    - Example: Customer, Product, and Order tables, each holding relevant information and linked by keys.
    - **Advantages**: Prevents data duplication and ensures consistency when data changes.

- **Keys**:
    - **Primary Key**: Unique identifier for each row in a table (e.g., `Customer ID` in `Customers` table).
    - **Foreign Key**: A reference to a primary key in another table to establish relationships (e.g., `Customer ID` in `Orders` table linking to `Customers` table).

- **Schema and Data Types**:
    - Each table follows a **fixed schema** with predefined column names and data types.
    - Ensures consistency in how data is stored across rows.

#### Performance and Optimization

- **Trade-offs**: While normalized databases reduce redundancy, they may **slow query performance** due to required joins across tables.
- **Alternatives**:
    - **One Big Table (OBT)**: Storing all data in a single table can improve speed for certain use cases, especially where quick access outweighs redundancy concerns.

#### Interacting with Databases

- **Relational Database Management Systems (RDBMS)**: Software that enables interactions with relational databases (e.g., MySQL, PostgreSQL, SQL Server).
- **SQL**:
    - Used to query and manipulate data within RDBMS.
    - SQL commands are fundamental to data engineering tasks in relational databases.

## NoSQL Databases
#### Background and Purpose of NoSQL Databases

- **Emergence**: In the early 2000s, companies like Google and Amazon developed NoSQL databases to handle high volumes of diverse data that didn’t fit well into the relational model.
- **Characteristics**:
    - Designed for **scalability** and **flexibility** by trading certain RDBMS features (e.g., joins, strong consistency) for improved performance and schema flexibility.
    - **Schema flexibility**: NoSQL databases don’t require predefined schemas, allowing you to store data without rigid tabular structures.

#### Core Properties

1. **Data Structure**:
    - **Non-tabular** formats: Key-value, document, wide-column, and graph structures.
2. **Horizontal Scaling**:
    - **Scalability** through distribution of data across multiple servers/nodes to handle large traffic.
3. **Consistency Model**:
    - **Eventual Consistency** (vs. strong consistency in RDBMS): Allows for faster reads, with the trade-off that data might not be immediately consistent across nodes.
4. **ACID Compliance**:
    - Not all NoSQL databases are **ACID compliant** (Atomicity, Consistency, Isolation, Durability), which may require additional steps to maintain data integrity.
    - Some, like **MongoDB**, do offer ACID compliance.
5. **Query Languages**:
    - Use specialized languages tailored to their structure, which are often different from SQL.

#### Types of NoSQL Databases

1. **Key-Value Databases**
- **Structure**: Stores data as key-value pairs (similar to JSON files or Python dictionaries).
- **Usage**: Ideal for fast data retrieval scenarios, such as caching.
- **Example Use Case**: Storing user session data in web or mobile applications (e.g., session ID as a unique key to track actions).

2. **Document Stores**
- **Structure**: Stores data in JSON-like documents, each identified by a unique key and organized into collections.
- **Usage**: Great for content management, catalogs, or IoT sensor readings, where data may vary in structure.
- **Example Use Case**: User profile data stored in a `users` collection, where each user’s data (document) is easily retrievable by user ID.

#### Applications and Trade-offs

- **Relational Databases**: Suited for **OLTP systems** like banking and finance, where data integrity and real-time consistency are critical.
- **NoSQL Databases**: Preferred for applications prioritizing scalability and speed, like social media platforms, where data can be eventually consistent rather than immediately.

## Database ACID Compliance
ACID principles ensure transactions in relational databases are processed reliably and accurately. While most relational databases are **ACID compliant** by default, some NoSQL databases require configuration to achieve similar levels of compliance. Here’s a breakdown of each principle:

1. **Atomicity**:    
    - Ensures transactions are treated as a single, indivisible unit.
    - If any part of a transaction fails, the entire transaction is rolled back.
    - **Example**: If a network error interrupts a customer order, atomicity ensures the charge and inventory update either both complete or both roll back.
    
2. **Consistency**:
    - Guarantees that transactions follow database rules, maintaining the database in a valid state.
    - Any operation violating rules will fail and be rolled back.
    - **Example**: A transaction attempting to reduce stock below zero will fail, ensuring inventory integrity.
    
3. **Isolation**:
    - Allows concurrent transactions to execute independently without interference.
    - Transactions are processed sequentially, ensuring consistent results.
    - **Example**: Two simultaneous orders for an item will adjust stock accurately without overlapping, ensuring accurate inventory.

4. **Durability**:    
    - Ensures that once a transaction completes, its results are permanent and resilient to system failures.
    - Data remains accessible even after events like power outages or hardware failures.
    - **Example**: An update to an account balance remains intact even if a power failure occurs immediately afterward.

## Amazon DynamoDB
#### Key Features of Amazon DynamoDB

1. **Key-Value Database**:
    - DynamoDB is a key-value database where data is stored in **tables**.
    - Each item (or row) in the table is uniquely identified by a **primary key**.
    - Tables are **schema-less**, meaning items can have different sets of attributes.

2. **Primary Key**:
    - The primary key uniquely identifies each item in the table.
    - **Partition Key**: A simple primary key that consists of a single attribute (e.g., Person ID).
    - **Composite Key**: Consists of a **partition key** and a **sort key**, allowing for multiple items with the same partition key but unique sort keys (e.g., Order ID + Item Line Number).

3. **Partitioning**:
    - DynamoDB uses the partition key to determine in which physical storage partition the item will be saved.
    - The **sort key** is used to organize and sort items within a specific partition.

## Object Storage
#### Key Concepts in Object Storage

1. **Flat Structure**:
    - Unlike traditional file systems with folders and subfolders, Object Storage uses a **flat structure** with no inherent hierarchy.
    - While platforms like Amazon S3 offer a user interface that mimics folders, all files (objects) are actually stored at the top level for efficient access.
2. **Objects and Metadata**:
    - Each file, or **object**, has a unique **Universal Unique Identifier (UUID)** or key, which is essential for accessing and managing it.
    - Objects also come with **metadata**—additional details like creation date, file type, and owner information.
3. **Immutability**:
    - Once written, objects in Object Storage are **immutable**, meaning they can’t be partially modified or appended.
    - To make changes, you must overwrite the entire object with an updated version or enable **versioning** to retain multiple versions.
4. **Data Versatility**:
    - Object Storage can handle various file formats (CSV, JSON, video, audio, images, etc.), making it ideal for **semi-structured and unstructured data**.

#### Benefits of Object Storage

1. **Scalability**:
    - Object Storage can easily **scale** to accommodate large volumes of data without performance degradation, making it suitable for data-intensive tasks.
2. **Availability and Durability**:
    - In cloud environments, data is typically **replicated across multiple availability zones** to ensure high durability and availability, even in case of data center failures.
    - For example, Amazon S3 offers **11 nines (99.999999999%) of durability** by replicating data across multiple zones.
3. **Cost-Effectiveness**:
    - Object Storage is often **cheaper** than other storage types, especially for infrequently accessed data, making it a cost-effective solution for long-term storage.
4. **Compatibility with Modern Architectures**:
    - Object Storage is fundamental to **data lakes** and **data lakehouse** architectures, which require flexible, scalable, and durable storage solutions.

## Logs
#### What Are Logs?
- Logs are **records of events** or activities within a system or application.
- They capture a time-ordered sequence of events and are often used to **monitor** system health, **troubleshoot errors**, and **analyze performance**.
- Historically considered as “exhaust” data by developers, logs now serve as valuable data sources for downstream applications.

#### Structure and Components of a Log
1. **User/System Information**: Logs typically include **user IDs** or **system identifiers**, such as IP addresses, to associate events with a specific entity.
2. **Event Details and Metadata**: Describe the action, such as a user logging in or adding an item to a cart, along with **status updates** on the event.
3. **Timestamp**: Records the **exact time** an event occurs, which is critical for analysis and troubleshooting.
4. **Log Levels**: Tags that categorize the significance of each log record:
    - **Info**: Routine information or basic activity.
    - **Debug**: Detailed technical information useful for debugging.
    - **Warn**: Indications of potential issues that aren’t critical.
    - **Error**: Records of errors in the system that require attention.
    - **Fatal**: Critical failures in the system needing immediate resolution.

#### Common Use Cases for Logs in Data Engineering
- **System Monitoring and Alerts**: Used to trigger alerts and monitor system health.
- **Data Analysis**: Analyzing user behavior patterns, especially in e-commerce or web applications.
- **Change Data Capture (CDC)**: Tracking database changes to trigger ingestion or transformations in data pipelines.
- **Machine Learning**: Training models for **anomaly detection** and other analytical purposes.
- **Automation**: Driving automated processes based on specific events or changes recorded in logs.

## Streaming Systems

#### Key Concepts
- **Event**: An occurrence or change in the system, like a user clicking a button or a sensor capturing a reading.
- **Message**: A record containing information about an event, including details, metadata, and a timestamp.
- **Stream**: A continuous sequence of messages generated from events, forming streaming data.

#### Components of a Streaming System
1. **Event Producer**: Generates messages for the stream. Examples include IoT devices, apps, websites, and APIs.
2. **Event Consumer**: Processes messages from the stream. Multiple consumers may exist, each handling messages differently (e.g., a payment service and an inventory service for an e-commerce order).
3. **Event Router (Streaming Broker)**: Routes messages from the producer to the appropriate consumer, ensuring asynchronous communication. Examples include Apache Kafka and Amazon Kinesis.

#### Two Main Types of Streaming Systems
1. **Message Queues**: Events are stored in a queue (first-in-first-out). Once a consumer processes a message and confirms receipt, it is deleted.
    - **Use Case**: Great for ensuring each message is processed once in a specific sequence.
    - **Example**: Amazon SQS (Simple Queue Service), commonly used in microservices and serverless applications.
2. **Streaming Platforms**: Events are stored in an **append-only log**. Consumers read messages as read-only, so the messages are **persistent** and can be re-read or reprocessed.
    - **Use Case**: Useful for reprocessing or replaying data from a specific point in time.
    - **Examples**: Apache Kafka, Amazon Kinesis Data Streams.

#### Message Queues vs. Streaming Platforms
- **Message Queue**: The router acts as a temporary queue. Once a message is read by the consumer, it’s deleted, ideal for one-time, sequential processing.
- **Streaming Platform**: The router maintains a persistent log. Messages are not deleted, allowing replaying or reprocessing data.

#### Applications in Data Engineering
- **Source Systems**: Streaming systems can be a primary data source, providing real-time data ingestion.
- **Pipeline Stages**: They can be integrated into ingestion, transformation, or serving stages, handling real-time data for continuous analysis and processing.