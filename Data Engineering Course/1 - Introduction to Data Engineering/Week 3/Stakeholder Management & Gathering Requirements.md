## Requirements
Requirements gathering involves understanding the business goals and stakeholder needs to design effective data systems. This process is organized as a **hierarchy of needs**:

1. **Business Goals and Objectives**: At the top level, these represent what success looks like for the business, such as increasing revenue, market share, or user base.
2. **Stakeholder Needs**: These are the tools, resources, and data systems that individual employees or departments need to meet the high-level business objectives.
3. **System Requirements**: These are the specific needs for data systems that support the stakeholders. They can be broken down into:
    - **Functional Requirements**: What the system does (e.g., detecting fraud in bank transactions).
    - **Non-functional Requirements**: Attributes that ensure proper system functioning, such as latency, scalability, reliability, and security (e.g., handling 10,000 simultaneous users on an e-commerce site).

The main takeaway is that **your role as a data engineer** is tightly connected to business objectives. You need to understand the **stakeholders' needs** and how your work contributes to the **overall goals** of the business. To effectively gather requirements, the recommendation is to engage directly with leadership, such as a **CTO** or **CDO**, to ensure alignment with business strategies.

## Requirements Gathering
Requirements gathering is essential to understanding how the data systems you build will add value to stakeholders and align with business goals. Key takeaways include:

- **Identify Stakeholders and Needs**: Before building or modifying data systems, you need to talk to various people in your organization, from leadership to colleagues like data scientists and software engineers, to fully understand their needs and how they relate to the business’s broader objectives.
    
- **Ask Open-Ended Questions**: Engage in conversations that explore the current systems, potential problems, and how stakeholders plan to use the data. These discussions will help you uncover the true needs behind the requests.
    
- **Document Findings**: Proper documentation is essential. It allows you to confirm with stakeholders that the system you plan to build will meet their needs and ensures that everyone is on the same page regarding system functionality.
    
- **Functional and Non-Functional Requirements**: Once you’ve gathered stakeholder input, break the requirements into functional (what the system should do) and non-functional (system attributes like scalability, reliability) categories to ensure comprehensive planning.
    
#### Iron Triangle
**Iron Triangle** concept highlights the inherent tension between **scope**, **timeline**, and **cost** in any project. You often have to make trade-offs between these factors, balancing the desire for quick, cost-effective, and high-quality outcomes.

![[Iron Triangle.excalidraw|100%x200]]

However, the lesson emphasizes that you can avoid the pitfalls of the Iron Triangle by applying good architectural principles like:

- Building loosely coupled systems
- Optimizing for reversible decisions
- Understanding stakeholder needs deeply