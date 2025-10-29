# Analytics and Development Lifecyle

## Learning Objectives

- Explain the analytics development lifecycle
- Explain the roles on a data team
- Explain how dbt fits into the modern data stack
- Understand the structure of a dbt project.

## Table of Contents

- [ELT vs ETL](#elt-vs-etl)
- [Data Team Roles](#data-team-roles)
- [Building Data You Can Trust with dbt](#building-data-you-can-trust-with-dbt)
- [The ADLC](#the-adlc)
- [dbt - the Data Control Plane](#dbt---the-data-control-plane)

## ELT vs ETL

The battle between ETL (Extract, Transform, Load) and ELT (Extract, Load, Transform) is one of the most important conversations in modern data management. As data continues to expand in volume and complexity, organizations must decide which approach is best suited to their analytics needs.

When comparing ETL vs. ELT, the key difference lies in when and where the data transformation occurs. With ETL, data is transformed before loading, while, in ELT, data is transformed after loading into the data warehouse.

### What is ETL?

ETL stands for **Extract, Transform, and Load**. This method prepares data for analysis by extracting it from various sources, transforming it into a structured format, and loading it into a target system.

In ELT workflows, most meaningful data transformation occurs outside this primary pipeline in a downstream business intelligence (BI) platform.

![ETl Diagram](/02_analytics_development_lifecyle/images/etl_diagram.png)

#### The ETL Process

- **Extract**: Data is pulled from various sources, often in unstructured or semi-structured formats.
- **Transform**: The data undergoes a transformation process, cleaning, formatting, and structuring it for analysis.
- **Load**: Once transformed, the data is loaded into a target system, typically a data warehouse, where it becomes available for querying and reporting.

### What is ELT?

ELT stads for **Extract, Load, Transform** and has gained popularity in cloud-native environments. In this approach, data is extracted and loaded into a data warehouse first, allowing the data to be transformed using the warehouse's computing power.

ELT has emerged as a paradigm for how to manage information flows in a modern data warehouse. This represents a fundamental shift from how data previously was handled when ETL was the data workflow most companies implemented.

![ELT Diagram](/02_analytics_development_lifecyle/images/elt_diagram.png)

#### The ELT Process

- **Extract**: Data is collected from various sources, just as in ETL.
- **Load**: The raw data is loaded into a data warehouse without any transformations
- **Transform**: After the data is stored, transformations are performed within the warehouse, leveraging its computational power.

#### Making the Case for ELT

ELT aligns with the scalability and flexibility of modern data stacks, enabling organizations to work with large datasets more efficiently. While there are many benefits to using ELT, the primary benefits are:

- **Leverage Cloud Infrastrcture**
  - ELT takes advantage of the massive processing power of cloud-native warehouses like Snowflake, BigQuery, and RedShift.
  - By loading raw data into the warehouse first, ELT enables these systems to handle transformations at scale, which is particularly valuable when working with large volumes of data.
- **Faster Data Availability**
  - With ELT, raw data is loaded into the warehouse immediately, making it accessible for analysis more quickly.
  - This reduces the delay often seen in ETL processes, where daa must be transformed before it's available for querying.
- **Cost Efficiency**
  - ELT reduces the need for expensive on-premises hardware or complex ETL tools.
  - Instead, it capitalizes on the inherent processing capabilities of cloud data warehouses, optimizing both performance and cost.
  - In modern data stacks, offloading transformation tasks to cloud services can lead to significant cost savings.
- **Flexible, iterative transformation**
  - Since the raw data is already in the warehouse, analysts and data engineers can transform data iteratively, applying changes and optimizations without having to reload or reprocess the entire dataset.
  - This flexibility makes it easier to adapt to evolving business needs and ensures that teams can alway work with the latest data.
- **Data Democratization**
  - By loading raw data into the warehouse first, ELT supports a more self-service model.
    - Analysts and data teams can access and transform data as needed without being bottlenecked by upstream ETL processes.
    - This fosters greater agility and collaboration across teams.

### How dbt Fits into the ELT Workflow

dbt plays a crucial role in the ELT process by serving as the transformation layer within the data warehouse. While ELT relies on loading raw data into the warehouse, dbt empowers teams to manage and automate their transformations, ensuring the data is clean and analytics-ready.

**dbt features include:**

- **Version-Controlled Transformations**: dbt enables version control for all transformations, making it easy to track changes and collaborate across teams. This ensures data transformations are organized and consistent.
- **Automation and Scheduling**: With dbt, you can automate transformation processes, ensuring that the most up-to-date data is always available for analysis. This fits perfectly within an ELT workflow, where transformation happens after the data is alread in the warehouse.
- **Comprehensive Testing**: dbt offers built-in testing capabilities to validate transformations, ensuring data quality and integrity throughtout the ELT process.

## Data Team Roles

### Data Engineer

Data Engineers build systems to collect and process data. They create the foundation for all data work. Their expertise centers on building reliable pipelines.

Their role includes:

- Designing data infrastructure and architecture
- Creating and maintaining data pipelines
- Ensuring and maintaining data pipelines

Data engineers deliver value through technical solutions. They connect different data collection processes. Their work enables all downstream data activities.

### Analytics Engineer

Analytics engineering is a relatively recent data team role. Since then, the field has grown across industries. An analytics engineer is a valuable addition to the team.

Their role includes:

- Exploration: Exploring data already ingested into data platforms in response to stakeholder questions and needs.
- Preparation: Cleaning and preparing datasets for analytics use cases.
- Transformation: Transforming prepared datasets into objects that can serve organizational objectives, such as a super-table that can serve as a base for multiple applications.
- Documentation: Documenting the object they find and create in the data warehouse, ensuring that other users can also see, understand, and use them.

Analytics engineering provides value in several ways:

- Having someone focused on developing and documenting data objects sets up analytics teams for data self-service with an accessible and understandable catalog of data products.
- Improved data discoverability helps prevent dark data which sits in storage unused or unknown, from draggin on storage costs and potentially becoming a compliance liability. Analytics engineers stay engaged with the data warehouse, ensuring valuable data is not overlooked.
- Analytics engineers respond to stakeholders, relieving long queues for data engineering teams and opening up time for critical maintenance, infrastructure updates, etc. It also allows for faster feedback loops since analysts with stakeholder context can work directly on maintaining and changing data pipelines.

### Data Analyst

Data analysts transform raw data into business insights. They answer questions using data analysis methods. Their focus is on solving business problems.

Data analysts serve key functions on data teams:

- Interpreting data to find trends
- Creating reports and visualizations
- Working closely with business stakeholders

Data analysts provide value through actionable insights. They help businesses make informed decisions. They translate complex findings into clear recommendations. Their analyses drive strategic business outcomes.

## Building Data You Can Trust with dbt

![Where dbt sits](/02_analytics_development_lifecyle/images/struture.png)

## Review

- Traditional Data Teams
  - Data engineers are responsible for maintaining data infrastructure and the ETL process for creating tables and views.
  - Data analysts focus on querying tables and views to drive business insights for stakeholders.
- ETL and ELT
  - ETL (extract transform load) is the process of creating new database objects by extracting data from multiple data sources, transforming it on a local or third party machine, and loading the transformed data into a data warehouse.
  - ELT (extract load transform) is a more recent process of creating new database objects by first extracting and loading raw data into a data warehouse and then transforming that data directly in the warehouse.
  - The new ELT process is made possible by the introduction of cloud-based data warehouse technologies.
- dbt
  - dbt empowers data teams to leverage software engineering principles for transforming data.
  - The focus of this course is to build your analytics engineering mindset and dbt skills to give you more leverage in your work.
- The Analytics Development Lifecycle (ADLC)
  - Provides a structured process for building, testing, reviewing, and deploying analytics.
  - Encourages iteration and collaboration so teams can confidently move from idea to production.
  - Aligns data work with software engineering best practices—version control, testing, and continuous improvement.
- dbt as the Data Control Plane
  - dbt orchestrates and governs the ADLC across your data ecosystem.
  - It ensures consistency in how data is developed, tested, documented, and deployed.
  - By serving as the “control plane,” dbt integrates with the modern data stack to enforce trust, scalability, and readiness for AI-driven use cases.
