# ETL Project

This project demonstrates an ETL (Extract, Transform, Load) process using **Talend** as the ETL tool and **SQL Server** as the database, running in a Dockerized environment.

## Features

• **Extract**: Retrieve data from various sources.

• **Transform**: Process, clean, and prepare the data.

• **Load**: Store the processed data into a SQL Server database.

## Tools and Technologies

• **Talend**: ETL tool for designing and managing data workflows.

• **SQL Server**: Relational database for storing transformed data.

• **Docker**: Container platform for running SQL Server.

## Prerequisites

Ensure the following are installed on your system:

• Docker

• Talend (Open Studio or licensed version)

• Git (optional, for version control)

## Screenshots

## 1. Transform data from csv into database
![Flow_ETL](https://github.com/user-attachments/assets/f8b3c2cf-cd62-4102-bf7d-b0d6768cdd90)

# 2. Data Transforming Workflow
![ETL_Flow_2](https://github.com/user-attachments/assets/286eb9c3-a9b6-4ba6-a4ed-3a12f1fefc3d)

## 3. Integrating 2 Databases
![ETL_Integrate_DB](https://github.com/user-attachments/assets/beba0022-bda1-42a3-8671-671272283df3)




## Project Structure

• **joblets/**: Contains reusable Talend components.

• **metadata/**: Includes metadata definitions for connections, schemas, and other project-specific settings.

• **process/**: Houses the primary ETL workflows created in Talend.

• **sqlPatterns/**: Contains SQL templates or patterns used in the project.

• **.git/**: Git version control repository.

## Setup Instructions

### 1. Clone the Repository

```
bash
git clone <repository_url>
cd ETL
```

## 2. Set Up SQL Server with Docker

```
docker pull mcr.microsoft.com/mssql/server:latest
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=YourPassword123' \
   -p 1433:1433 --name sqlserver -d mcr.microsoft.com/mssql/server:latest
Replace YourPassword123 with a strong password for the sa user.
```
## 3. Configure Talend

1. Open Talend.
2. Import the job files from the TalendJobs/ directory.
3. Configure database connections:
   Host: localhost
   Port: 1433
   User: sa
   Password: YourPassword123

## 4. Initialize the Database

Use the scripts in the SQLScripts/ directory to set up the database schema and initial data:

```
docker exec -it sqlserver /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U sa -P 'YourPassword123' -i /path/to/SQLScripts/init.sql
```

## 5. Execute the ETL Process

Run the Talend jobs to extract, transform, and load the data into the SQL Server database.

## Troubleshooting

Docker Issues: Ensure Docker is running, and the container is healthy.
Database Connectivity: Verify connection settings in Talend.
ETL Errors: Check Talend logs for detailed error messages.

## License
This project is licensed under the MIT License.

## Contributing
Contributions are welcome! Please submit a pull request or open an issue for any improvements or suggestions.

Let me know if you'd like additional enhancements! 🚀
