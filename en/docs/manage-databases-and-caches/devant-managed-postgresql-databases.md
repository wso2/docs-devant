---
title: Devant Managed PostgreSQL Databases and Vector Databases
description: Learn how to create and manage PostgreSQL databases and vector databases on Devant.
---

# Devant-Managed PostgreSQL Databases and Vector Databases

PostgreSQL on Devant offers fully Devant-managed, efficient object-relational databases on AWS, Azure, GCP, and Digital Ocean. Additionally, Devant allows you to create fully-managed PostgreSQL vector databases if you want to perform efficient vector similarity search.

## Create a Devant-managed PostgreSQL database

Follow the steps below to create a Devant-managed PostgreSQL database:

1. Sign in to the Devant Console at [https://console.devant.dev/](https://console.devant.dev/).
2. In the header, click the **Organization** list. This opens the organization home page.
3. In the left navigation menu, click **Dependencies** and then **Databases**.
4. Click **Create** and select **PostgreSQL** as the database type. Provide a display name for this server and follow the instructions.
5. Select your preferred cloud provider from AWS, Azure, GCP, or Digital Ocean.
    - The cloud provider is used to provision the compute and storage infrastructure for your database.
    - There is no functional difference between databases created on different cloud providers, apart from changes to service plans (and associated costs).
6. Choose the region for your database.
    - Available regions will depend on the selected cloud provider. Devant currently supports US and EU regions across all providers.
7. Select the service plan.
    - Service plans vary in the dedicated CPU, memory (RAM), storage space allocated for your database, the backup retention periods, and high-availability configurations for production use cases.

## Create a Devant-managed PostgreSQL vector database

Follow the steps below to create a Devant-managed PostgreSQL vector database:

1. Sign in to the Devant Console at [https://console.devant.dev/](https://console.devant.dev/).
2. In the header, click the **Organization** list. This opens the organization home page.
3. In the left navigation menu, click **Dependencies** and then **Vector Databases**.
4. Follow steps 4 onwards in the [Create a Devant-managed PostgreSQL database](#create-a-devant-managed-postgresql-database) section.

## Connecting to your Devant-managed PostgreSQL database

To connect to your Devant-managed PostgreSQL database, consider the following guidelines:

- You can use any PostgreSQL driver, ORM, or supported generic SQL library (may depend on the programming language) to connect to the database.
- The connection parameters can be found in the **Overview** section in the Devant Console under the relevant database.
- PostgreSQL databases accept traffic from the internet by default. You can restrict access to specific IP addresses and CIDR blocks under **Advanced Settings**.


## High Availability and Automatic Backups

The high availability characteristics and the automatic backup retention periods for Devant-managed PostgreSQL databases vary based on the selected service plan as shown below.

| Service Plan | High Availability                                                  | Backup Retention Time |
|--------------|--------------------------------------------------------------------|-----------------------|
| Hobbyist     | Single-node with limited availability                              | None                  |
| Startup      | Single-node with limited availability                              | 2 days                |
| Business     | Two-node (primary + standby) with higher availability              | 14 days               |
| Premium      | Three-node (primary + standby + standby) with highest availability | 30 days               |

Service plans with standby nodes are generally recommended for production scenarios for multiple reasons:
- Provides another physical copy of the data in case of hardware, software, or network failures.
- Typically reduces the data loss window in disaster scenarios.
- Provides a quicker time to restore with a controlled failover in case of failures, as the standby is already installed and running.

### Automatic Backups


- Devant runs full backups daily to automatically back up Devant-managed PostgreSQL databases and copies the write-ahead logs (WAL)  at 5-minute intervals or for every new file generated.
  Devant encrypts all backups at rest.

- Devant automatically handles outages and software failures by replacing broken nodes with new ones that resume correctly from the point of failure. The impact of a failure will depend on the number of available standby nodes in the database.

### Failure Recovery

- **Minor failures**: Devant automatically handles minor failures such as service process crashes or temporary loss of network access in all plans without requiring significant changes to the service deployment. Devant automatically restores the service to normal operation once Devant automatically restarts the crashed process or when Devant restores the network access.

- **Severe failures**: To handle severe failures such as losing a node entirely in case of hardware or severe software problems, requires more drastic recovery measures. The monitoring infrastructure automatically detects a failing node, both when the node starts reporting issues in the self-diagnostics or when it stops communicating. In such cases, the monitoring infrastructure automatically schedules a new replacement node to be created.
> - In the event of database failover, the Service URI of your service remains the same; only the IP address will change to point to the new primary node.
> - Hobbyist and Startup plan provide a single node, and in case of failure, a new node starts up, restores its state from the latest available backup, and resumes serving traffic.
    In this plan, as there is just a single node providing the service, the service will become unavailable for the duration of the restoration. In addition, any write operations made since the backup of the latest WAL file will be lost. Typically, this time window is limited to either five minutes of time or one WAL file.

## Connection limits

The following connection limits apply to Devant-managed PostgreSQL databases based on the selected service plan.

| Service Plan               | Max Connections |
|----------------------------|-----------------|
| Hobbyist                   | 25              |
| Startup/Business/Premium-4 | 100             |
| Business-16                | 400             |
| Premium-8                  | 200             |
