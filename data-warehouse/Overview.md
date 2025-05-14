## Overview
The infrastructure is designed to handle data from multiple sources and transform it into a structured format for analysis.
The data flow begins with updates from various data sources being exported to a staging area in Azure Data Lake Storage.
Azure Data Factory then incrementally loads this data into staging tables in Azure Synapse Analytics, where it is cleansed and transformed.
PolyBase is utilized to parallelize the process for large datasets.
Once the data is loaded into the warehouse, an Azure Analysis Services tabular model is refreshed to simplify the analysis of business data and relationships.
Business analysts use Microsoft Power BI to analyze the warehoused data via the Analysis Services semantic model.
