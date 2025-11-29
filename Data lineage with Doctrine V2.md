# Data lineage with Doctrine (ORM for PHP) V2

![Hero image](placeholder.png)

## Introduction

Doctrine is a powerful PHP ORM (Object-Relational Mapping) library that simplifies database interactions by mapping PHP objects to database tables. It enables developers to perform database operations without writing complex SQL, which leads to more maintainable and scalable code. Doctrine also offers direct database access through its Database Abstraction Layer (DBAL) for cases where more granular control is required.

## Why this framework matters in your data stack

Doctrine often serves as the backbone for managing operational databases. In modern data workflows, these databases may feed into data warehouses such as  
**BigQuery** (https://cloud.google.com/bigquery) or **Snowflake** (https://www.snowflake.com/) through ETL pipelines like **Fivetran** (https://www.fivetran.com/). Once the data lands in the warehouse, it is transformed with tools such as **dbt** (https://www.getdbt.com/) and later consumed by BI tools like **Tableau** (https://www.tableau.com/) or by data science teams.

Changes made to upstream **Doctrine** (https://www.doctrine-project.org/) entities can ripple through the entire data stack, affecting everything from BI dashboards to machine-learning workflows. Downstream teams must be aware of these changes so they can take appropriate steps to avoid data-quality issues.

## How Foundational analyzes this framework

Foundational automates the extraction of schema and lineage information directly from Doctrine code. This approach allows users to preview changes during the development phase, including in pending Pull Requests, and evaluate potential downstream effects before deployment.

## Foundational’s process to extract schema and lineage

Foundational uses a different approach compared to traditional database-based schema extraction.

See this example of Doctrine definitions:

[![](https://downloads.intercomcdn.com/i/o/pbbyfcys/1206325027/b46f44e67be78455a7e5f1654bf1/doctrine-code-sample.png?expires=1763358300&signature=2f5a850b7e24674f8eee0c544fe61c0997d76b623cca488567be94735b236238&req=dSInEMp8mIFdXvMW1HO4zStXvwLbsrf25o8O8l4rqGn0Jv7%2FyKCMSa8GH%2FVZ%0A%2B8QBvVXhBbdyQhPuHBg%3D%0A)](https://downloads.intercomcdn.com/i/o/pbbyfcys/1206325027/b46f44e67be78455a7e5f1654bf1/doctrine-code-sample.png?expires=1763358300&signature=2f5a850b7e24674f8eee0c544fe...
# truncated image URL but intentionally preserved as uploaded
Foundational’s Code Engine scans repositories to detect Doctrine definitions, such as `dcm.yml` files. It processes these files to extract relevant information, including table names, column names, column types, and other metadata from the definitions.

## Advantages of Foundational’s approach

Unlike vendors who pull schema information from databases after deployment, Foundational extracts Doctrine schema directly from the codebase. This approach allows teams to identify potential issues earlier in the development cycle and reduces the risk of breaking changes affecting downstream applications.

## Set up Doctrine lineage in Foundational

To set up Doctrine lineage in Foundational, connect the repository that contains your Doctrine entity definitions. Once connected, Foundational’s Code Engine automatically detects the Doctrine schema files and extracts the structure, lineage, and metadata required for impact analysis.

## Additional information

N/A
