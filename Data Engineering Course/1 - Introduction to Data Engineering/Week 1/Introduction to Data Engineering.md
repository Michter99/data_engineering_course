## Definition of Data Engineering
Data Engineering is the development, implementation, and maintenance of systems and processes that take in raw data and produce high-quality, consistent information that supports downstream use cases, such as analysis and machine learning. Data Engineering is the intersection of security, data management, DataOps, data architecture, orchestration, and software engineering.

## [[The Data Engineering Lifecycle]]
![[Data Engineering Lifecycle.excalidraw|100%x200]]

- **Generation**: This represents the creation of raw data. This could come from a variety of sources like transactional databases, web services, sensor data, logs, and more. It's the initial point where data enters the pipeline.
- **Ingestion**: In this phase, data is collected from various sources and brought into a centralized storage system, often a data lake or data warehouse. Ingestion might involve streaming real-time data or batch processing for larger datasets.
- **Transformation**: Once ingested, the raw data needs to be cleaned, structured, and enriched to become usable. This phase is often handled using ETL (Extract, Transform, Load) or ELT (Extract, Load, Transform) processes, where data is manipulated into formats suitable for downstream analytics, machine learning, or other use cases.
- **Serving**: After the data is transformed, it is ready for use by different applications or teams. This could involve serving the data to dashboards, machine learning models, or operational systems. The serving layer makes the processed data available for real-time or batch consumption.
- **Analytics, Machine Learning, and Reverse ETL**: Once data is served, it can be analyzed for insights, used to train machine learning models, or re-integrated into other operational systems (Reverse ETL) to act on insights. This is where the value of the data is realized through data-driven decision-making.
- **Storage**: Supporting all these stages is a robust data storage layer. Data needs to be stored efficiently, securely, and in formats that support the various operations needed, from raw to transformed data.
**Supporting Infrastructure (Undercurrents):** Underpinning the entire lifecycle are essential components necessary for managing, orchestrating, and securing the data pipeline.

## Definition of Data Pipeline
The combination of architecture, systems, and processes that move data through the stages of the data engineering lifecycle.

## The Data Engineer Among Other Stakeholders
- **Stakeholder Collaboration**:
	- **Downstream Stakeholders**:
		- Understand the needs of those who consume the data, such as analysts, data scientists, or business teams.
		- Align on data requirements, definitions, and performance expectations.
		- Ensure the data provided supports their decision-making and adds value to their work.
	- **Upstream Stakeholders**:
		- Work with the teams responsible for the systems that generate raw data (e.g., software engineers or third-party providers).
		- Ensure clarity on data formats, volumes, and any potential disruptions that may affect data pipelines.
		- Influence how data is delivered to improve processing and reliability.
- **Alignment with Business Goals**:
	- Understand the overall strategy and objectives of the organization.
	- Ensure that the data engineering processes support business goals and create value for stakeholders.

## System Requirements
- **Understanding Stakeholder Needs**:
    - The first step to delivering value is understanding the goals and needs of stakeholders.
    - These needs can come in the form of **business requirements** (high-level business goals) and **stakeholder requirements** (individual needs to accomplish their work).
- **Translating Needs into System Requirements**:
    - Data engineers must translate business and stakeholder needs into **system requirements**.
    - **System requirements** are divided into:
        - **Functional Requirements** (What the system needs to do, e.g., providing regular updates, alerting anomalies).
        - **Non-functional Requirements** (How the system achieves its goals, e.g., technical specifications for performance, security, or storage).
- **Types of Requirements**:
    - **Business Requirements**: Broad goals such as increasing revenue or expanding the user base.
    - **Stakeholder Requirements**: Specific needs that help individuals perform their tasks effectively.
    - **System Requirements**: Both functional and non-functional aspects of what the system should achieve.
- **Requirement Gathering Process**:
    - Conversations with stakeholders are essential to understand their business goals.
    - Stakeholders may not communicate in concrete system requirements, so it's up to the engineer to interpret their goals and translate them into technical needs.
    - Tailor your approach based on the stakeholder’s technical understanding and role within the organization.

## Translate Stakeholder Needs into Specific Requirements
- **Identifying Existing Systems & Pain Points**:
	- Understand current solutions and their limitations.
	- Learn about problems or inefficiencies in the systems stakeholders use, such as data delays or schema changes.
- **Understanding Stakeholder Actions**:
	- Focus on what actions stakeholders plan to take with the data, rather than just their perceived needs.
	- Clarifying their goals helps you define accurate system requirements, both functional and non-functional.
- **Clarifying Requirements**:
	- Confirm your understanding of the stakeholders’ needs by repeating back what you’ve learned.
	- Ensure alignment on the technical and business requirements, such as latency expectations and data transformation needs.
- **Identifying Additional Stakeholders**:
	- Determine if further conversations are needed with other stakeholders (e.g., software engineers, marketing teams) to fully understand the system and data requirements.

## Thinking Like a Data Engineer
**Stage 1: Identify Business Goals and Stakeholder Needs**
- **Objective**: Understand the high-level business goals driving the project and the needs of all stakeholders involved:
	- Clarify the overall business goals.
	- Identify all relevant stakeholders and how their needs align with business objectives.
	- Understand current systems and their limitations.
	- Ask stakeholders about the actions they plan to take with the data products, helping to zero in on functional requirements.

**Stage 2: Define System Requirements**
- **Objective**: Translate stakeholder needs into clear system requirements.
	- **Functional Requirements**: Define what the system needs to do to meet the stakeholders’ goals.
	- **Non-Functional Requirements**: Describe the technical specifications (e.g., performance, security) of how the system will achieve those goals.
	- Document the requirements and confirm with stakeholders to ensure alignment.

**Stage 3: Select Tools and Technologies**
- **Objective**: Choose the right tools and technologies for building the system.
	- Identify various tools and technologies that meet the system requirements.
	- Conduct a cost-benefit analysis to evaluate trade-offs (e.g., costs, cloud resources, licensing).
	- Select the best tools and set up a prototype to test the system’s feasibility.

**Stage 4: Build, Evaluate, Iterate & Evolve**
- **Objective**: Prototype, evaluate, and finalize the system before moving to full deployment.
	- Build a prototype to test whether the system meets stakeholder expectations.
	- Iterate on the prototype based on stakeholder feedback.
	- Once validated, deploy the full system.
	- Continuously monitor and improve the system over time to meet evolving business and stakeholder needs.

**Ongoing Process:**
- This framework is cyclical and iterative. As business goals and stakeholder needs evolve, so will the data system.
- Regular communication with stakeholders is key to ensuring the system continues to deliver value.