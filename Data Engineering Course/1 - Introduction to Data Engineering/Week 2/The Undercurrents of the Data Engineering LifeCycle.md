## Security
#### Key Security Principles:
1. **Principle of Least Privilege**:
    - Only provide access to data and resources that are necessary for a user or application to perform their job and only for as long as needed.
    - This principle applies not only to others but also to yourself—avoid using superuser or admin access unless absolutely necessary.
2. **Data Sensitivity**:
    - Limit visibility of sensitive data unless essential.
    - If you don't need to ingest or store sensitive data, avoid doing so, which reduces the risk of data leaks.
3. **Cloud-Centric Security**:
    - In the cloud, security involves understanding **Identity and Access Management (IAM)** roles, **encryption**, and **networking protocols**.
    - Data engineers must be cautious when handling cloud resources (e.g., ensuring S3 buckets are not unintentionally exposed to the public).
#### The Human Factor in Security:
- Security isn't just about protocols—it’s also about people. Many security breaches are caused by human error, such as sharing passwords insecurely or falling victim to phishing attacks.
- Adopting a **defensive mindset** is crucial—always be cautious when handling credentials or sensitive data, and think ahead about potential attack scenarios.
#### Organizational Security Culture:
- **Security theater** refers to organizations adhering to security regulations superficially, without fostering a true culture of security.
- A robust security culture requires that every individual in the organization, from top to bottom, understands their role in protecting data and takes security seriously.

## Data Management
Data management plays a crucial role in ensuring that data becomes a valuable business asset. As a data engineer, your work revolves around a subset of **data management tasks** that contribute to the **proper handling, security, and usability** of data.
#### DAMA and DMBOK:
- **DAMA**: The Data Management Association International provides resources for effective data management.
- **DMBOK (Data Management Book of Knowledge)**: A comprehensive reference guide that outlines 11 key **data knowledge areas**, including data governance, integration, modeling, security, and more. Data governance is central, as it connects and influences all other areas.
#### Data Governance:
Data governance ensures the **quality, integrity, security, and usability** of data throughout its lifecycle. It encompasses:
- **Data security and privacy**: Safeguarding sensitive information (discussed in the previous video).
- **Data quality**: Ensuring data is accurate, complete, and available when needed. High-quality data aligns with stakeholder expectations and facilitates better decision-making, while low-quality data leads to inefficiencies and poor business outcomes.