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