## Location
#### On-Premises Data Systems
- **Definition**: A company owns, provisions, maintains, and scales all hardware and software for its data stack on its premises.
- **Operational Responsibility**: The company is responsible for:
    - Provisioning hardware and storage.
    - Maintaining and updating systems.
    - Scaling infrastructure to meet growing demands.
#### Cloud Data Systems
- **Definition**: Cloud providers like AWS manage the hardware, infrastructure, and data centers, while companies rent compute and storage resources.
- **Advantages**:
    - **Scalability**: Easily scale up or down based on demand, optimizing costs.
    - **Flexibility**: Freedom to change tools and technologies without major infrastructure changes.
    - **No Hardware Maintenance**: Cloud providers handle infrastructure maintenance, freeing the company from this responsibility.
#### Hybrid Systems
- Some companies maintain a mix of on-premises and cloud-based systems, either by choice or necessity.
- Reasons for **on-premises** usage:
    - Regulatory requirements.
    - Security or privacy concerns.
    - Specialized business needs.
#### Industry Trends
- **Cloud Adoption**: The industry is increasingly moving toward cloud-based systems due to their flexibility and scalability.
- **Migration**: Many companies are transitioning from on-premises systems to the cloud for these benefits.
- **Learning Focus**: Given the momentum towards cloud solutions, it's beneficial for aspiring data engineers to focus on cloud technologies.

## Monolith vs Modular Systems
#### Monolithic Systems
- **Definition**: A self-contained architecture where components are tightly coupled and delivered as a single application.
- **Advantages**:
    - **Simplicity**: Easy to understand and manage as all functionality resides in one place.
    - **Technology Uniformity**: Typically involves only one primary programming language and technology stack.
- **Disadvantages**:
    - **Maintenance Challenges**: As the system grows, updating or fixing one component can impact others, often requiring significant rewrites or redeployment of the entire system.
    - **Rigid Structure**: Difficult to scale or modify without affecting the entire system, which can cause delays, errors, and downtime.
#### Modular Systems
- **Definition**: A system made of loosely coupled, independent components, often referred to as microservices in software development.
- **Advantages**:
    - **Flexibility**: Individual components can be developed, updated, and deployed independently, reducing the risk of failure affecting the entire system.
    - **Interoperability**: Tools and technologies can easily be integrated, providing the ability to swap out components as needed.
    - **Scalability**: Easier to scale specific parts of the system without affecting other components.
    - **Example**: Data stored in object storage (e.g., Parquet format) can be processed with any tool that supports the format, allowing for better integration and flexibility.

## Cost Optimization and Business Value
#### Total Cost of Ownership (TCO)
TCO refers to the total cost of a solution, project, or initiative over its entire lifecycle, including both direct and indirect costs:
- **Direct Costs**: Tangible costs directly associated with the development of a data product, such as team salaries, AWS bills, and software subscriptions.
- **Indirect Costs**: Overhead or expenses not directly attributed to the development, such as IT support or loss of productivity due to downtime.
##### Types of Expenses
- **Capital Expenses (CapEx)**: Long-term fixed asset investments, such as purchasing hardware and software, which were more common before cloud platforms.
- **Operational Expenses (OpEx)**: Recurring expenses for day-to-day operations, like cloud service fees, which are spread out over time.

With the rise of cloud platforms, most companies now adopt an **OpEx-first approach** to minimize upfront investments, opting for pay-as-you-go models.

#### Total Opportunity Cost of Ownership (TOCO)
TOCO refers to the cost of lost opportunities when choosing a specific tool or technology:
- **Effect of Choices**: Selecting one data stack (e.g., Stack A) excludes others (e.g., Stack B or C). The cost of being locked into Stack A is your opportunity cost.
- **Evolving Landscape**: Data engineering tools evolve rapidly. The best tool today may become obsolete, leading to costs when switching to more relevant tools.
To reduce TOCO, **flexible and loosely coupled systems** are recommended, as they allow for easier updates and adaptation to new technologies. It’s helpful to distinguish between:
- **Immutable Technologies**: Long-lasting technologies, such as SQL or object storage, that remain stable over time.
- **Transitory Technologies**: Technologies that are rapidly evolving, such as stream processing and AI tools.

#### FinOps
FinOps aims to minimize costs (TCO and TOCO) while maximizing opportunities for revenue generation. To achieve this, data engineers should:
- **Opt for Cloud Services**: Cloud-based services with pay-as-you-go models allow for cost-efficient scaling.
- **Use Modular Systems**: Modular solutions enable continuous iteration and improvement without incurring heavy costs for restructuring or system changes.

## Build vs Buy
When it comes to tools and technologies, the decision between building from scratch and purchasing an existing solution depends on a few factors:

1. **Building from scratch**:
    - Best when attempting something novel that no existing tool supports.
    - Not recommended for most scenarios, as it can lead to "reinventing the wheel" and become a case of **undifferentiated heavy lifting**—hard work that doesn’t add direct value to the organization.
2. **Open-Source Options**:
    - Fully open-source solutions are available, and these are often free from licensing fees.
    - However, your team must have the **expertise and bandwidth** to implement and maintain the system.
    - While the open-source community can provide support, a small team may struggle with the complexities of deployment and management.
3. **Commercial Open-Source & Proprietary Solutions**:
    - **Commercial open-source**: Offers a managed version of open-source tools. These services come with support, freeing up your team to focus on higher-level tasks.
    - **Proprietary solutions**: Fully managed, often more expensive, but reduce the operational overhead of maintaining a system.
#### Key Considerations

- **Total Cost of Ownership (TCO)**: Building your own solution may seem cheaper due to avoiding licensing fees, but TCO includes the cost of development, maintenance, and ongoing support. Always weigh these long-term costs.
- **Team Capabilities**: Does your team have the necessary skills and time to manage an open-source system, or would a managed service save time and resources?
- **Value to Organization**: Does building or maintaining a custom solution add meaningful value, or is it simply additional work that doesn’t improve outcomes?

## Server, Container, and Serverless Compute Options
#### Server

- **Description**: Full control over infrastructure (e.g., Amazon EC2). You manage everything, including OS, scaling, and security.
- **Benefits**: Complete control, suited for complex or legacy systems.
- **Drawbacks**: High management overhead, less scalable, requires manual scaling and updates.

#### Containers
- **Description**: Packages code and dependencies into modular units (e.g., Docker), managed with orchestration tools like Kubernetes.
- **Benefits**: Portable, scalable, supports microservices, more flexible than traditional servers.
- **Drawbacks**: Requires configuration and management of infrastructure, including container orchestration.

#### Serverless
- **Description**: Abstracts server management (e.g., AWS Lambda). Automatically scales without managing infrastructure.
- **Benefits**: No infrastructure management, pay-as-you-go, ideal for event-driven and short-duration workloads.
- **Drawbacks**: Execution limits (time, concurrency), can be costly with high event rates, not suitable for large or continuous workloads.

### How the Undercurrents Impact Your Decisions

When building your data architecture, the six undercurrents of the data engineering lifecycle—security, data management, data ops, data architecture, orchestration, and software engineering—play a key role in how you choose tools and technologies.

#### 1. Security
- **Consideration**: Different tools come with varying security features. Ensure you use reputable and trusted tools, especially for open-source software.
- **Takeaway**: Check for security features like authentication, data protection, and adherence to best practices. Ensure tools don’t contain malicious components and review code when using open-source options.

#### 2. Data Management
- **Consideration**: It’s essential to understand how data governance practices are implemented.
- **Takeaway**: Ask how data is protected against breaches, compliance with regulations (like GDPR), and what methods the tool offers to ensure data quality.

#### 3. DataOps
- **Consideration**: Focus on automation and monitoring features.
- **Takeaway**: When choosing managed services, ensure you review the Service Level Agreement (SLA) to understand guarantees for reliability and availability.

#### 4. Data Architecture
- **Consideration**: Look for modularity and interoperability between tools.
- **Takeaway**: Ensure the tools allow flexible, loosely coupled integration, which is essential for adaptable, scalable systems.

#### 5. Orchestration
- **Consideration**: Apache Airflow dominates the space, but new players like Prefect, Dagster, and Mage are emerging.
- **Takeaway**: Understand your architectural goals and choose orchestration tools that align with your flexibility and scalability needs, considering the rapidly evolving landscape.

#### 6. Software Engineering
- **Consideration**: Balance between building your own solution and using pre-built options.
- **Takeaway**: Assess your team’s expertise and bandwidth. Avoid undifferentiated heavy lifting—focus on open-source or commercial tools first before opting for proprietary options.