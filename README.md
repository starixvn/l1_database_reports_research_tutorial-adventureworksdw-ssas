# AdventureWorksSSAS

## Overview

This project contains a SQL Server Analysis Services (SSAS) Multidimensional model based on the AdventureWorksDW2022 data warehouse. It provides a comprehensive business intelligence solution for analyzing sales data across different dimensions including customers, products, geography, and time.

## Prerequisites

-   SQL Server 2022 or later
-   SQL Server Analysis Services (Multidimensional mode)
-   Visual Studio with SQL Server Data Tools (SSDT)
-   AdventureWorksDW2022 database (installed on your SQL Server instance)

## Getting Started

### Installation

1. Clone this repository to your local machine
2. Open the `AdventureWorksSSAS.sln` file in Visual Studio
3. Update the data source connection in the project:
    - Right-click on the `AdventureWorksDW2022.ds` file and select "Properties"
    - Update the connection string to point to your SQL Server instance
    - Default connection: `Provider=SQLOLEDB.1;Data Source=10.10.50.157;Integrated Security=SSPI;Initial Catalog=AdventureWorksDW2022`

### Deployment

1. Right-click on the project in Solution Explorer
2. Select "Deploy"
3. Verify the deployment server settings match your target SSAS instance

## Data Model Structure

### Dimensions

-   **Customer** - Customer information including demographics
-   **Date** - Calendar date dimension with various hierarchies
-   **Product** - Product information including categories and subcategories
-   **Employee** - Employee details with organizational hierarchy
-   **Geography** - Geographic hierarchies (Country, State, City)
-   **Promotion** - Marketing promotions information
-   **Reseller** - Business reseller information
-   **Sales Territory** - Sales territories for organizational analysis

### Fact Tables

-   **Internet Sales** - Direct to consumer sales transactions
-   **Reseller Sales** - Business to business sales transactions

### Hierarchies

-   **Geography**: Country > State > City
-   **Product**: Category > Subcategory > Product
-   **Date**: Year > Quarter > Month > Date
-   **Employee**: Organization hierarchy

## Usage Examples

### Basic MDX Queries

To retrieve total Internet Sales by Year:

```sql
SELECT
  [Measures].[Internet Sales Amount] ON COLUMNS,
  [Date].[Calendar Year].MEMBERS ON ROWS
FROM [AdventureWorksDW2022]
```

### Power BI Integration

1. Connect to Analysis Services in Power BI
2. Select this cube as your data source
3. Create reports using the pre-built dimensions and measures

## Development

### Adding New Measures

1. Open the cube designer
2. Navigate to the "Calculations" tab
3. Add new calculated measures using MDX expressions

### Processing the Cube

To update the cube with the latest data:

1. Right-click on the cube in SSMS
2. Select "Process"
3. Choose the appropriate processing option

## License

This project is based on Microsoft's AdventureWorks sample database and is intended for learning and demonstration purposes.

## Contributing

Contributions to improve the model are welcome. Please follow these steps:

1. Fork the repository
2. Create a feature branch
3. Submit a pull request
