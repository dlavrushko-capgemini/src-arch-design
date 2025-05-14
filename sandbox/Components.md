## Components
The Azure Sandbox includes several configurations and components, each with important connections to other components:

1. Shared Services Virtual Network
    * Azure Bastion: Provides secure and seamless RDP and SSH connectivity to VMs.
    * Azure Firewall: Protects the network with advanced threat protection.
    * Active Directory Domain Controller: Manages domain services and integrates with Azure private DNS zones and Azure Private Link private endpoints.
2. Application Virtual Network
    * Windows Server Jump Box: Acts as a developer workstation with preinstalled tools like Visual Studio Code, Azure Storage Explorer, AzCopy, Azure Data Studio, SQL Server Management Studio, and MySQL Workbench.
    * Linux Jump Box: Functions as a DevOps agent with preinstalled Azure CLI, PowerShell, Terraform, and dynamic CIFS mount to Azure Files.
    * Azure Files Share: Provides preconfigured file sharing capabilities.
3. SQL Server on Azure Virtual Machines (VMs)
    * Preconfigured SQL Server VM, domain joined to the local domain.
4. Azure SQL Database
    * Provides managed SQL database services.
5. Azure Database for MySQL Flexible Server
    * Offers managed MySQL database services through private endpoints.
6. Azure Virtual WAN and Point-to-Site VPN
    * Facilitates secure connectivity options, including internet-facing access via Azure Bastion and point-to-site VPN connectivity.