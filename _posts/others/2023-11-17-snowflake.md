---
layout: post
title: Snowflake 
categories: others
sitemap: false
hide_last_modified: true
published: true
---

## [Snowflake] The Complete Masterclass

## Snowflake
Hybrid Columnar Storage (Partition Attributes Across - PAX)
- Horizontal and vertical partitioning
- Automatic column level and partition level compression
- Natural (built-in) data clustering based on ingestion date(order)

## Data warehouse
- is a database that combines different data from different data sources in one consumable database that we can use for reporting and data analysis
- ETL(Extract, Transform, Load) is the process of creating a data warehouse
- raw data -> data integration -> access layer -> report or data science or other apps
- Raw data(staging area) : can be internal or external
- Data integration(data transformation)

## Snowflake
- AccountAdmin > SysAdmin > (Custome Role 1)
- AccountAdmin > SecurityAdmin > UserAdmin > Public

## Loading data
- bulk loading: most frequent method, uses warehouses, loading from stages, COPY command, transformations possible
- continuous loading: designed to load small volumnes of data, automatically once they are added to stages, lates results for analysis, Snowpipe(serverless feature)
- Stages: location of data files where data can be loaded from
- external stage: external cloud provider, database object created in schema, CREATE STAGE(URL, access settings)
- internal stage: local storage maintained by Snowflake
- file format object: to store information like file type, field delimiter etc. will overide properety of Stage object




