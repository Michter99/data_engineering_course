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