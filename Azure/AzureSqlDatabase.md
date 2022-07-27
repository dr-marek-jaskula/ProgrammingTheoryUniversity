## Azure SQL Database

To create an Azure SQL Database, we search for Azure SQL Database in a search bar.
We create an instance of Azure SQL Database, create an connection string name (important), connection user name and password.
Then, we can copy the connection string value.
We can save the connection string in:
- Azure App Settings
- Azure Key Vault

To connect to the Azure SQL Database (SQL Server database) from the local machine using for instance Azure Data Studio, we need to
firstly specify the firewall exception. To do this, we go to Azure, then to instance of our SQL server and then to:
"Firewalls and virtual networks" blade:
- We click on "Add client IP"
- Ensure that our IP is placed correctly
- Click "Save" button

Then, go to Azure Data Studio and connect to the server.