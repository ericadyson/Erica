# Data Lineage with Ruby Active Record

![ruby on rails active record.png](ruby_on_rails_active_record.png)

# Introduction

[Active Record](https://www.notion.so/Data-Lineage-with-Ruby-Active-Record-2ad7474b9d8780b0b529fa61479d9533?pvs=21) is an Object-Relational Mapping (ORM) framework built into Ruby on Rails. It simplifies interaction between Ruby applications and databases. It allows developers to map Ruby classes to database tables and perform CRUD (Create, Read, Update, Delete) operations through Ruby methods rather than raw SQL. Active Record automates database interactions, so developers may focus on application logic while it manages the database layer. This abstraction supports cleaner and more maintainable code, integrates with the Rails ecosystem, and makes database management more intuitive.

---

# Why this framework matters in your data stack

Active Record often serves as the primary layer for interacting with operational databases in Rails applications, particularly in OLTP environments such as Postgres. These databases are commonly ingested into data warehouses like [Snowflake](https://docs.snowflake.com/en/user-guide-getting-started) or [BigQuery](https://cloud.google.com/bigquery/docs/introduction) using ETL tools such as [Stitch](https://www.stitchdata.com/) or [AirByte](https://docs.airbyte.com/using-airbyte/getting-started/).

Once in the warehouse, data is transformed using tools such as dbt or [Matillion](https://www.matillion.com/data-productivity-cloud/transform), and the results are consumed by BI tools such as [Looker](https://cloud.google.com/looker/docs/intro) or [Tableau](https://www.tableau.com/learn/get-started). Other downstream users include data science teams, machine-learning models, and reverse ETL processes.

Any change that developers make to upstream Active Record models may impact the entire data stack. These updates have the potential to break dashboards, downstream transformations, and machine-learning models. Teams that rely on this data need early visibility when model changes occur. This visibility helps them prepare and avoid data-quality issues.

---

# How Foundational analyzes this framework

The Foundational Code Engine automates schema and lineage extraction by analyzing Active Record models directly in the code. It detects schema changes during development or in pending Pull Requests (PRs) and allows teams to evaluate potential downstream impacts before they deploy updates.

---

# Advantages of Foundational’s approach

Many tools retrieve schema information directly from databases after deployment.
Foundational uses a different approach and has these benefits:

- It extracts schema definitions **directly from Active Record definitions in the code**, which gives customers visibility into schema changes earlier in the development cycle and
- Reduces the risk of breaking changes in production systems.

![**Example of Ruby Active Record model**](Example_of_Ruby_Active_Record_model.png)

**Example of Ruby Active Record model**

---


# Set up Active Record lineage in Foundational

Setting up Active Record schema and lineage extraction with Foundational is straightforward. Connect your repository that contains the Active Record models and the Code Engine automatically detects and extracts the schema.

Once connected, the Code Engine scans and processes the Active Record models, which provides visibility into schema and lineage without requiring database access.

## Introduction
N/A

## Why this framework matters in your data stack
N/A

## How Foundational analyzes this framework
N/A

## Foundational’s process to extract schema and lineage
N/A

## Advantages of Foundational’s approach
N/A

## Set up Active Record lineage in Foundational
N/A

## Additional information
N/A
