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