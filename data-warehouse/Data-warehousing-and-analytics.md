# Dataflow
The data flows through the solution as follows:

* For each data source, any updates are exported periodically into a staging area in Azure Data Lake Storage.
* Azure Data Factory incrementally loads the data from Azure Data Lake Storage into staging tables in Azure Synapse Analytics. The data is cleansed and transformed during this process. PolyBase can parallelize the process for large datasets.
* After loading a new batch of data into the warehouse, a previously created Azure Analysis Services tabular model is refreshed. This semantic model simplifies the analysis of business data and relationships.
* Business analysts use Microsoft Power BI to analyze warehoused data via the Analysis Services semantic model.

# Components
The company has data sources on many different platforms:

* SQL Server on-premises
* Oracle on-premises
* Azure SQL Database
* Azure table storage
* Azure Cosmos DB
  
Data is loaded from these different data sources using several Azure components:

* Azure Data Lake Storage is used to stage source data before it's loaded into Azure Synapse.
* Data Factory orchestrates the transformation of staged data into a common structure in Azure Synapse. Data Factory uses PolyBase when loading data into Azure Synapse to maximize throughput.
* Azure Synapse is a distributed system for storing and analyzing large datasets. Its use of massive parallel processing (MPP) makes it suitable for running high-performance analytics. Azure Synapse can use PolyBase to rapidly load data from Azure Data Lake Storage.
* Analysis Services provides a semantic model for your data. It can also increase system performance when analyzing your data.
* Power BI is a suite of business analytics tools to analyze data and share insights. Power BI can query a semantic model stored in Analysis Services, or it can query Azure Synapse directly.
* Microsoft Entra ID authenticates users who connect to the Analysis Services server through Power BI. Data Factory can also use Microsoft Entra ID to authenticate to Azure Synapse via a service principal or Managed identity for Azure resources.