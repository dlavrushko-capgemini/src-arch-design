## Overview
The infrastructure is designed to handle data from multiple sources and transform it into a structured format for analysis. The data flow begins with updates from various data sources being exported to a staging area in Azure Data Lake Storage. Azure Data Factory then incrementally loads this data into staging tables in Azure Synapse Analytics, where it is cleansed and transformed. PolyBase is utilized to parallelize the process for large datasets. Once the data is loaded into the warehouse, an Azure Analysis Services tabular model is refreshed to simplify the analysis of business data and relationships. Business analysts use Microsoft Power BI to analyze the warehoused data via the Analysis Services semantic model.

## Components
The infrastructure includes several key components and their connections:

1. Data Sources:
   * SQL Server on-premises
   * Oracle on-premises
   * Azure SQL Database
   * Azure Table Storage
   * Azure Cosmos DB
2. Azure Data Lake Storage:
    * Stages source data before loading into Azure Synapse.
3. Azure Data Factory:
    * Orchestrates the transformation of staged data into a common structure in Azure Synapse.
    * Uses PolyBase to maximize throughput when loading data into Azure Synapse.
4. Azure Synapse Analytics:
    * Distributed system for storing and analyzing large datasets.
    * Utilizes massive parallel processing (MPP) for high-performance analytics.
    * Uses PolyBase to rapidly load data from Azure Data Lake Storage.
5. Azure Analysis Services:
    * Provides a semantic model for data.
    * Enhances system performance during data analysis.
6. Microsoft Power BI:
    * Suite of business analytics tools for data analysis and sharing insights.
    * Queries semantic models stored in Analysis Services or directly queries Azure Synapse.