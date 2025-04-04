# Create a Connection

Using Connections, you can connect the integration with other APIs on Devant or external services. It also allows you to create connections to any Devant-managed database.

To create a connection to an API or a database, follow the step-by-step instructions in the respective tab:

=== "Create a connection to an API"

    <h2>Create a connection to a Devant service</h2>

    Follow these steps to create a connection to an API deployed in Devant:

    1. In the Devant Console, go to the top navigation menu and set the visibility level as project or integration as follows: 

        - **Project Connection**: Select an organization and a project in that organization. 
        - **Integration Connection**: Select an organization, a project in that organization, and an integration in the selected project. 

    2. In the left navigation menu, click **Admin** and then **Connections**. This page lists all the existing connections.
    3. Click the **Services** card and the resource page will open. You can search and apply filters to efficiently find a service.
    5. Click on the service you want to connect to. 
    6. Enter a name and a description for the connection.
    7. Select an **Access Mode** and **Authentication Scheme** for the connection.
    8. Click **Create**.
   
    This creates the connection and displays its details for each environment, along with an inline guide on how to use the connection in your component. 

    !!! note
        During connection creation, secret values for the lowest environment are visible, allowing you to copy them for local use if necessary. Secret values for higher environments remain hidden to ensure security.
     
    <h2>Create a connection to an external service</h2>

    Follow these steps to create a connection to an external service:

[//]: # (TODO: Explain more about these steps)
    1. In the left navigation menu, click **Admin** and then **Third Party Services**. This page lists all the existing third-party services.
    2. Click **+Register**. This opens the Register a Third Party Service window.
    3. Enter the **Name**, **Version**, and **Summary**.
    4. Select a the **Service Definition** file to upload.
    4. Select a the **Service Type** from the dropdown.
    5. Click **Define Endpoints**.
    6. Add endpoints to your requirement and click **Register**.

      For step-by-step instructions on using a connection in your integration, see [Use a Connection in Your Integration](./use-a-connection-in-your-integration.md).


=== "Create a connection to a database"

    Prerequisites:

     - Create a Devant-managed database. For details, see [Devant-Managed Databases and Caches](../manage-databases-and-caches/devant-managed-databases-and-caches.md).
     - Add the database to the Marketplace. For details, see [Add Devant-Managed Databases and Caches to the Marketplace](../manage-databases-and-caches/add-devant-managed-databases-and-caches-to-the-marketplace.md).

    Follow these steps to create a connection to a Devant-managed database:

    1. In the Devant Console, go to the top navigation menu and set the visibility level as [project](../devant-concepts/connections.md#project-connections) or [component](../devant-concepts/connections.md#component-connections) as follows: 

        - **Project Connection**: Select an organization and a project in that organization. 
        - **Component Connection**: Select an organization, a project in that organization, and a component in the selected project. 

    2. In the left navigation menu, click **Dependencies**  and then **Connections**. This page lists all the existing connections.
    3. Click **+Create**. This opens the Marketplace view where you can browse and search for services or databases.
    4. Click the **Databases** tab. You can search and apply filters to efficiently find a database.
    5. Click on the database you want to connect to. 
    6. To create the connection, follow these steps:

        1. Enter a name and description.
        2. Under **Environment Configuration**, select credentials for each environment.

            !!! note
                 By default, the selected database is applied to all environments. To use different databases for specific environments, select the appropriate database and provide the corresponding credentials for each environment.

        3. Click **Create**.  
    
    This creates the connection and displays the database connection details for each environment, along with an inline guide on how to use the connection in your component. 

    !!! note
        During connection creation, secret values for the lowest environment are visible, allowing you to copy them for local use if necessary. Secret values for higher environments remain hidden to ensure security.
    
    For step-by-step instructions on using a database in your component, see [Use a Database Connection in Your Component](./use-a-database-connection-in-your-integration.md).
