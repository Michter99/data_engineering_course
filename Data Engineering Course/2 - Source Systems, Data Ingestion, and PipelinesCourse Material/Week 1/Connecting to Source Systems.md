## Connecting to Source Systems
Before ingesting data, you need to establish a connection to the source system and verify that you're authorized to access the data. Here's an overview of the key methods and tools used to connect to source systems:
### 1. AWS Console

- **Purpose**: Access and locate connection details for resources within your AWS account.

- **Steps**:
    - Navigate to the AWS Management Console.
    - Locate the resource (e.g., an RDS instance) to find connection details such as **endpoint** and **port number**.
    - Use the connection information to authenticate and connect to the resource.

- **Pros**:
    - User-friendly, graphical interface.
    - Quick for prototyping or one-time setups.

- **Cons**:
    - Not repeatable or easily traceable.
    - Changes in the AWS Console interface can make workflows inconsistent.

### 2. Command Line Interface (CLI)

- **Purpose**: Programmatically query and connect to AWS resources directly from the terminal.

- **Example**:

```
aws rds describe-db-instances
```
Returns details about your RDS instances, including endpoint and port.

- **Steps**:
    - Use CLI commands to retrieve connection details.
    - Connect to the database using commands specific to the DBMS (e.g., PostgreSQL, MySQL).

- **Pros**:
    - Lightweight and faster than using the console for repetitive tasks.
    - Enables precise control.

- **Cons**:
    - Requires manual input, making it less ideal for complex workflows.

### 3. SDKs (e.g., Boto3 for Python)

- **Purpose**: Automate connection processes by embedding them into scripts.
- **Example with Boto3**:
```python
import boto3
rds_client = boto3.client('rds')
response = rds_client.describe_db_instances()
print(response['DBInstances'][0]['Endpoint']['Address'])
```
    
- **Steps**:
    - Use SDKs to programmatically retrieve connection details or directly connect to the resource.
    - Ideal for integrating into ingestion pipelines and workflows.
- **Pros**:
    - Highly repeatable and traceable.
    - Suitable for complex workloads and automation.
- **Cons**:
    - Requires programming knowledge and setup effort.

### 4. API Connectors (e.g., JDBC/ODBC)

- **Purpose**: Establish a connection between your application and a database management system (DBMS).
- **Common APIs**:
    - **JDBC (Java Database Connectivity)**: Primarily for Java applications.
    - **ODBC (Open Database Connectivity)**: Language-agnostic, widely supported.
- **Steps**:
    - Use the respective API to connect to the DBMS.
    - Perform queries or ingestion operations.
- **Pros**:
    - Standardized and efficient for connecting to relational databases.
- **Cons**:
    - May require additional driver installation or configuration.