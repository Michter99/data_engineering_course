## Data Generation in Source Systems
#### Data Sources in Data Engineering
As a data engineer, your job begins with **consuming data** from various **source systems**. These sources could include:
- **Databases**: Both relational and NoSQL databases serve as key data sources.
- **Files**: Accessing and working with raw files is common for data engineers.
- **APIs**: These interfaces allow you to request data from web services.
- **Data Sharing Platforms**: Used to obtain data from internal or third-party platforms.
- **IoT Devices**: These devices stream real-time data that may require aggregation for downstream workflows.
#### Working with Source Systems
- **External Control**: These systems are often maintained by other teams or third parties (software engineers, vendors, etc.) and are largely out of your direct control.
- **Understanding Systems**: It’s crucial to understand how these source systems work because the pipelines you build depend on the data generated from them.
#### Unpredictability of Source Systems
Source systems can be **unpredictable**—they may experience outages, format changes, or data alterations without notice. For instance, the **schema** or structure of a database may change, potentially breaking your pipelines, as in the case of a database column reorganization.
#### Importance of Communication with Source Owners
To mitigate issues, it is essential to **work closely with the owners** of the source systems:
- Understand how they generate and manage data.
- Anticipate potential changes or disruptions.
- Maintain communication to stay informed about updates that may affect your pipelines.

## Data Ingestion
**Data ingestion** is the process of moving **raw data** from **source systems** into your **data pipeline** for further processing. It's a critical stage in the data engineering lifecycle and can often become a bottleneck. Working closely with source system owners to understand the systems' behaviors and data characteristics is crucial to avoid common pitfalls during ingestion.
#### Ingestion Patterns: Batch vs. Streaming
1. **Batch Ingestion:**
	- **Definition**: Data is collected and processed in chunks, typically at predefined intervals (e.g., hourly, daily) or when data reaches a certain size.
	- **Use Cases**: Batch processing is commonly used in analytics, reporting, and machine learning model training.
	- **Advantages**: Simpler and often more cost-effective for large-scale, periodic data needs.
	- **Trade-offs**: It may not be suitable for use cases that require real-time data or instant decision-making.
2. **Streaming Ingestion:**
	- **Definition**: Data is ingested continuously in near real-time, typically less than one second after it’s generated.
    - **Use Cases**: Streaming is ideal for applications like real-time anomaly detection, dynamic dashboards, and instant decision-making.
    - **Advantages**: Provides real-time access to data for fast response times.
    - **Trade-offs**: More complex, potentially higher costs in terms of infrastructure, maintenance, and potential downtime.
#### Coexistence of Batch and Streaming:
- **Hybrid Pipelines**: Most pipelines use a mix of batch and streaming. For example, while batch is used for model training, the data might be ingested via streaming for other purposes like real-time monitoring.
- **Boundary Decisions**: Data engineers often need to decide where batch and streaming components intersect within the pipeline.
#### Other Ingestion Considerations:
- **Change Data Capture (CDC)**: This method triggers ingestion processes based on changes in the source system's data.
- **Push vs. Pull**: Decide whether the source system will push data to your pipeline or if you'll actively pull it.

## Data Storage
As a data engineer, you work with storage solutions that impact the performance, cost, and scalability of your systems. Storage can be understood through a **three-layer hierarchy**:
1. **Raw Storage (Bottom Layer)**: This includes physical components like disks, SSDs, and RAM, along with non-physical aspects such as networking and compression. These provide the foundational infrastructure for storing data.
2. **Storage Systems (Middle Layer)**: These systems are built on top of raw storage and include databases, object storage (e.g., Amazon S3), and streaming storage systems. They manage how data is stored, retrieved, and processed in your pipelines.
3. **Storage Abstractions (Top Layer)**: High-level tools like data warehouses, data lakes, and data lakehouses combine storage systems to meet specific requirements, such as latency, scalability, and cost.
#### Importance of Understanding Storage:
While you often work at the **storage abstraction** level, understanding the entire hierarchy is critical for optimizing performance and costs. Mismanagement, like inefficient data ingestion methods, can lead to slow processes and higher expenses. A deep understanding of storage helps you design better data pipelines and avoid costly mistakes.

## Queries, Modeling, and Transformation
In the **transformation** stage, data engineers convert raw data into a useful format for downstream users, adding value to the data pipeline. This stage involves three key components: **queries**, **modeling**, and **transformation**.
#### 1. Queries:
- **Purpose**: Queries retrieve and manipulate data from databases or storage systems.
- **Tool**: SQL (Structured Query Language) is commonly used for querying and manipulating data.
- **Risks**: Poorly written queries can slow down systems, cause **row explosions** (unintended massive data outputs), and impact performance. Understanding how queries work is crucial for efficiency.
#### 2. Data Modeling:
- **Purpose**: Data modeling defines how data is structured to reflect real-world relationships.
- **Normalization vs. Denormalization**: For example, denormalizing data (combining related tables into simpler formats) can make querying more efficient for analysts.
- **Importance**: Good data models reflect business logic and processes. Collaboration with stakeholders is essential to align on key concepts, like defining what a "customer" means across departments.
#### 3. Data Transformation:
- **Purpose**: Transformations manipulate, enhance, and prepare data for use.
- **Multiple Stages**: Data can be transformed at various points in the pipeline, such as during ingestion (adding timestamps, mapping data types) or later for reporting (aggregating or featurizing for machine learning).
- **Examples**: Basic formatting, adding calculated fields, and schema transformations are common steps.

## Serving Data
The final stage of the data engineering lifecycle is **serving data**, where data is made accessible to stakeholders, allowing them to extract business value. The way data is served depends on the specific use case, such as analytics, machine learning, or reverse ETL. Serving data is about ensuring that the right data is available in the right format for end-users to leverage for decision-making and other actions.
#### Key Use Cases for Serving Data:
- **Analytics**:
	- **Business Intelligence (BI)**: Serving historical and current data for analysis through reports and dashboards. This helps teams like sales and marketing analyze trends, monitor engagement, and make strategic decisions.
	- **Operational Analytics**: Focuses on real-time data monitoring for immediate action, such as website performance metrics. The data engineer's role is to ensure real-time data is available for quick decision-making.
	- **Embedded Analytics**: User-facing applications that present data, such as bank dashboards or smart home apps. Here, the data engineer provides both real-time and historical data for customer-facing reports.
- **Machine Learning**:
    - Serving data for **model training**, feature stores, and **real-time inference**. Machine learning use cases require handling more complexity, such as ensuring proper data history and lineage.
- **Reverse ETL**:
    - Involves feeding transformed or analyzed data back into source systems (e.g., pushing lead scores from a data warehouse back into a CRM). This process ensures that enhanced data is available for further business use.