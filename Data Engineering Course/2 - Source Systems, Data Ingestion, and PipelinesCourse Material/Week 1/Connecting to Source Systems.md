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

## Basics of IAM and Permissions

#### What is IAM?

AWS IAM is a web service that helps you manage and securely control access to your AWS resources and services. With IAM, you can centrally manage who is authenticated in your Account and what resource permissions they have. Using IAM, you can share your resources without sharing your credentials, and you can select specific actions people can access at a granular level. It’s a global service available at no additional cost, meaning you can see and use your IAM configurations from any region in the AWS Management Console.

#### Importance of IAM

- **Security**: Ensures sensitive client and business data is protected.
- **Principle of Least Privilege**: Grants only the necessary permissions to users and applications for their roles, reducing risks of unauthorized access and minimizing potential cloud costs.
- **Avoiding Breaches**: Prevents human errors like insecure credential storage, misconfigurations, or overly permissive access, which can lead to costly data breaches.

#### IAM Components

1. **Policies**:
    - Define permissions (what actions can be performed on which resources).
    - Represented as JSON documents specifying `Resource`, `Action`, and `Effect` (e.g., Allow/Deny).

2. **Identities**:
    - **Root User**:
        - Full control over all resources.
        - Reserved for account creation and critical administrative tasks.
    - **IAM Users**:
        - Individual accounts with specific permissions and credentials.
        - Credentials: Username/password or access keys for programmatic access.
    - **IAM Groups**:
        - Collections of users with common permissions.
        - Example: A "Data Engineers" group with access to shared resources like S3 buckets and Glue jobs.
    - **IAM Roles**:
        - Temporary permissions assigned to users or applications (e.g., EC2, Lambda).
        - Securely grants access without exposing long-term credentials.

### IAM Best Practices

1. **Adopt Least Privilege**:
    - Assign the minimum permissions required for a task.
    - Avoid granting broad permissions unnecessarily (e.g., `*:*`).
2. **Use Roles for Temporary Access**:
    - Example: An EC2 instance assuming a role with S3 permissions instead of embedding credentials.
3. **Enable Multi-Factor Authentication (MFA)**:
    - Adds an extra layer of security for user accounts.
4. **Rotate Credentials Regularly**:
    - Refresh long-term credentials like access keys to reduce the risk of unauthorized access.
5. **Monitor and Audit**:
    - Use AWS CloudTrail to track API calls and detect unusual activity.

### Troubleshooting IAM Issues

- **Access Denied Errors**:
    - Verify policy permissions.
    - Check for expired temporary credentials (e.g., roles assumed by applications like EC2).
- **Resource Inaccessibility**:
    - Confirm the correct policy is attached to the user, group, or role.
    - Ensure resource ARNs in the policy match the intended resources.