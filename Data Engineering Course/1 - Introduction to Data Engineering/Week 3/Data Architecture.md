## What is Data Architecture?
The concept of **enterprise architecture** involves designing systems that enable organizations to adapt to change through flexible and reversible decisions, achieved by carefully evaluating trade-offs. This definition closely aligns with **data architecture**, which focuses on supporting the evolving data needs of an organization. Enterprise architecture includes four main areas:
1. **Business architecture** – Focuses on the product, service strategy, and business model.
2. **Application architecture** – Describes the structure and interaction of key applications.
3. **Technical architecture** – Relates to the software and hardware components supporting business systems.
4. **Data architecture** – Supports the organization’s evolving data needs.

Data architecture is a key component of enterprise architecture, linking your work as a data engineer to organizational goals.

A critical concept within this framework is **change management**, as data needs will continuously evolve. Jeff Bezos introduced the idea of **one-way** and **two-way doors** to describe decision-making:

- A **one-way door** is a decision that is hard to reverse.
- A **two-way door** is easily reversible.

The goal is to aim for two-way door decisions in architecture to allow flexibility and rapid iteration, which helps manage change. If you encounter a one-way door decision, break it into smaller, reversible steps.

## Principles of Good Data Architecture
In data architecture, there are nine key principles that guide how you design and manage systems. These principles can be grouped based on their focus.
#### Impact Other Teams and Individuals
1. **Choose Common Components Wisely**

One of the key roles of a data architect or data engineer is to select common components that can be widely used across the organization. These components might include storage systems, version control tools, monitoring systems, or data processing engines.

The goal is to choose components that promote collaboration and efficiency across teams. However, it’s important not to force a "one-size-fits-all" solution. Instead, focus on identifying the right tools and practices that fit multiple use cases without hindering productivity. Effective selection of these components can break down silos and help teams work together more seamlessly.

2. **Architecture is Leadership**

Data architecture also represents leadership. As a data engineer, you play a key role in identifying the right components for your organization, and as you grow, you may also guide others in understanding and using these systems. Over time, your role may evolve into mentoring colleagues and helping them understand the architectural decisions you've made. Practicing leadership through architecture means that you're not just solving technical problems but also enabling teams to achieve their goals.

#### On Going Process
1. **Make Reversible Decisions**

Reversible decisions are like **two-way doors**—they’re easy to undo if the outcome isn’t what you anticipated. This concept allows you to iterate and improve your systems without getting stuck with choices that are hard or impossible to change later on. It gives your data architecture the agility to adapt as needs and technologies evolve.

2. **Build Loosely Coupled Systems**

Loosely coupled systems consist of components that are independent and modular, meaning that changing or swapping one part doesn’t require redesigning the entire system. This is crucial because it ensures that your architecture remains flexible and resilient to change, making updates and enhancements easier.

3. **Always Be Architecting**

The principle of **always be architecting** recognizes that data architecture is not a one-time task but an ongoing process. As your organization’s data needs evolve, your architecture must also evolve. By consistently revisiting and refining your architecture, you ensure that your systems remain relevant and effective as business requirements and technologies change.
#### When Your System Fails
1. **Plan for Failure**

No system is immune to failure, so it’s essential to anticipate and plan for it. Key metrics to consider are **availability**, **reliability**, and **durability**. Availability refers to how often a service is operational (like 99.99% uptime), reliability ensures the system performs its function within a given time, and durability refers to how well your data storage systems resist data loss. Two important metrics here are:
- **RTO (Recovery Time Objective)**: the maximum acceptable time a system can be offline.
- **RPO (Recovery Point Objective)**: the maximum acceptable data loss during an outage.

2. **Prioritize Security**

Security is crucial, especially when considering the principle of **Zero Trust Security**. Unlike traditional perimeter security, zero trust assumes that no one inside or outside the network is automatically trusted. Instead, every action and user must be authenticated, minimizing the chances of a security breach.

3. **Architect for Scalability**

Systems must scale up during periods of high demand and scale down to save costs when demand is low. This involves anticipating load spikes to prevent system crashes and missed revenue opportunities due to inadequate capacity planning.

4. **Embrace FinOps**

Cloud systems operate on a pay-as-you-go model, which can lead to unexpected costs if not managed properly. **FinOps** encourages a balanced approach, ensuring cost-effective resource use while maintaining performance. As a data engineer, you’ll need to manage budgets by optimizing cloud costs and choosing the right mix of on-demand and spot instances, among other strategies.

## Batch Architectures
Batch architectures are a traditional approach to data processing, where data is ingested, transformed, and stored in fixed intervals, typically for use cases where real-time processing is not necessary. The key concept revolves around **batch processing**, where data is collected over a period (e.g., daily sales data) and processed at regular intervals.

#### Key Batch Architecture Patterns:
- **ETL (Extract, Transform, Load)**:
    - **Extract** data from source systems into a staging area.
    - **Transform** the data by cleaning and standardizing it.
    - **Load** the transformed data into a data warehouse for analysis or storage.
- **ELT (Extract, Load, Transform)**:
    - Data is **extracted** and **loaded** directly into the data warehouse, and transformations are applied within the warehouse itself. This is increasingly popular due to the powerful computational capabilities of modern cloud data warehouses.
- **Data Mart**:
    - A specialized subset of a data warehouse designed for a specific department or business area (e.g., sales or marketing). It provides additional transformations, optimizing query performance and simplifying data access for specific use cases.

#### Considerations in Batch Architectures:
- **Choosing Common Components**: Selecting shared components (e.g., data warehouses) to facilitate collaboration and reduce silos across teams.
- **Planning for Failure**: Preparing for issues like system downtime or changes in data schema by engaging with source system owners and ensuring that systems can handle unexpected changes.
- **Scalability**: Designing systems that can handle variations in batch sizes and changes in data volume over time.
- **Cost Optimization (FinOps)**: Performing a cost-benefit analysis to balance system performance and business value while managing operational costs.