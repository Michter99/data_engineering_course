## Introduction to AWS Cloud
1. **Cloud Definition & Benefits:**
	• **Cloud as On-Demand IT Resources**: AWS provides IT resources such as compute, storage, and networking on an as-needed basis with pay-as-you-go pricing. You use resources when required and shut them down when they’re no longer needed.
	• **Comparison to On-Premises**: Unlike traditional on-premises data centers that involve long-term commitments and fixed resources, AWS offers flexibility, scalability, and cost-efficiency, only charging for the resources you use at the end of each month.
2. **Core AWS Resources:**
	• **Compute Resources**: For running code, such as virtual machines (EC2), containers (ECS/EKS), or serverless functions (Lambda).
	• **Storage Resources**: Services like Amazon S3 for object storage, Elastic Block Store (EBS) for block storage, and various database services (relational, NoSQL, graph databases).
	• **Networking Resources**: Virtual networks like Amazon Virtual Private Cloud (VPC), allowing you to connect resources securely.
3. **Scalability and Elasticity:**
	• **Automatic Scaling**: AWS services, like S3, automatically adjust to your storage needs as data grows or shrinks, eliminating the need to predict capacity in advance.
	• **Elasticity**: Resources scale up and down as needed, ensuring you only pay for what you use while being prepared for demand spikes.

## AWS Regions and Availability Zones
#### AWS Regions:
AWS hosts data centers across **33 regions** worldwide, each with its own **geographical name** and **region code** (e.g., Northern Virginia is us-east-1). Regions operate independently, meaning data isn’t replicated across them without user authorization.

When selecting a region, consider factors like **latency** (proximity to end users), **cost** (pricing varies by region), **compliance** (regulatory requirements may dictate where data is stored), and **service availability** (not all services are available in every region).
#### Availability Zones (AZs):
Each region is subdivided into **Availability Zones (AZs)**, which are physically separated data centers within the same region, spaced up to 100 km apart. AZs are named using the region code followed by a letter (e.g., us-east-1a). They ensure **high availability** and **fault tolerance**, allowing workloads to continue running even if one AZ fails.

AWS regions and AZs are interconnected with low-latency links, ensuring resilience and enabling businesses to build scalable and reliable data systems.

## Intro to AWS Core Services
##### Compute:
- **Amazon EC2**: Provides virtual machines (VMs) or EC2 instances, giving full control over the operating system and applications. These instances can be scaled horizontally to meet demand.
- **AWS Lambda**: Serverless compute where code runs in response to events.
- **Amazon ECS/EKS**: For containerized workloads with Elastic Container Service (ECS) or Elastic Kubernetes Service (EKS).
##### Networking:
- **Amazon VPC**: A private network in the cloud, isolated from other AWS networks. You can create subnets, control IP ranges, and deploy resources within this network.
- AWS resources are region-bound, meaning they do not leave the selected region unless explicitly configured.
##### Storage:
- **Amazon S3**: Object storage for unstructured data like documents, logs, and media files.
- **Amazon EBS**: Block storage for low-latency, high-performance applications like databases or virtual machines.
- **Amazon EFS**: Scalable file storage for organizing data in a hierarchical structure, accessible across multiple systems.
##### Databases:
- **Amazon RDS**: Relational Database Service for managing structured, tabular data.
- **Amazon Redshift**: A data warehouse service designed for storing, transforming, and querying large datasets.
##### Security:
- **Shared Responsibility Model**: AWS manages the security **of the cloud** (physical hardware, facilities, hypervisor), while users are responsible for security **in the cloud** (OS, patches, firewalls, encryption).
- This shared model ensures both AWS and users contribute to maintaining secure cloud environments.

## Compute - Amazon Elastic Compute Cloud (EC2)
##### What is a Server and a Virtual Server?
A **server** is a computer or set of computers that hosts and runs applications, consisting of hardware (CPU, RAM, storage, networking), an operating system (OS), and applications on top of the OS. A **virtual server** differs in that it interacts with **virtual hardware**, which is a software representation of actual hardware, allowing multiple virtual machines (VMs) to share the same physical resources. This virtualization is managed by a **hypervisor**, which allocates physical resources (CPU, memory) to individual VMs. **Elasticity** means users can easily scale compute resources up or down, only paying for what is used.
##### Amazon EC2
In AWS, these virtual machines or virtual servers are called Amazon Elastic Compute Cloud or Amazon EC2. EC2 is one of the primary building blocks that you may directly use to run your applications or indirectly use by interacting with other services built on top of EC2 instances.

EC2 provides scalable, customizable virtual machines that can be tailored to fit various computing needs. Its elasticity allows users to manage resources efficiently, paying only for what they use, with several pricing models and instance types to fit different workloads.

![[Virtualization.excalidraw|100%]]

## Networking - Virtual Private Cloud (VPC) & Subnets
##### What is a Network?
A **network** is a collection of devices connected together, exchanging requests and responses. In cloud computing, resources need to communicate with each other and, in some cases, with the outside internet. Understanding networking concepts like **IP addresses** and **VPCs** is essential for enabling this communication.
##### What is an IP Address?
An **IP address** is a unique identifier assigned to each device within a network, ensuring that data is sent to the correct destination. The most commonly used version is **IPv4**, represented as four numbers separated by periods (e.g., 192.101.0.2), where each number ranges from 0 to 255.

**CIDR Notation** (Classless Inter-Domain Routing) specifies a range of IP addresses, such as `192.101.0.0/24`, meaning the first 24 bits are fixed, and the last 8 bits can vary, allowing for a range of addresses (e.g., `192.101.0.0` to `192.101.0.255`).
##### What is a VPC?
A **Virtual Private Cloud (VPC)** is an isolated, private network within AWS that allows you to launch and organize resources. It spans multiple **availability zones** within a region. Resources inside a VPC can communicate with each other, but they are isolated from the outside world and other VPCs unless you configure connections. When creating a VPC, you must specify the IP address range using **CIDR notation**.
##### What is a Subnet?
A **subnet** is a smaller network inside a VPC that allows for finer control over resource access. You can create:
- **Public subnets**: For resources that need access to the internet.
- **Private subnets**: For resources that should remain isolated.
Subnets are created within **availability zones**, and resources in different subnets within the same VPC can still communicate with each other.

## Security - AWS Shared Responsibility Model
When using AWS, security is shared between AWS and the customer, known as the **Shared Responsibility Model**.
##### AWS’s Responsibility (Security of the Cloud):
AWS handles the security of the physical infrastructure, including:
- **Physical facilities**: The data centers where AWS services are hosted.
- **Global infrastructure**: The hardware, software, and networking components, including the cables connecting regions.
##### Your Responsibility (Security in the Cloud):
As a customer, you are responsible for:
- **Data security**: Protecting your data at rest and in transit.
- **Access management**: Controlling who has access to your data and resources, including defining roles, permissions, and access duration.
- **Service configurations**: Depending on the AWS services used, you may need to manage additional security settings like encryption, firewalls, and backups.