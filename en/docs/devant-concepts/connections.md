# Connections

Integrations can exist in two main forms: standalone and integrated. Connecting integrations is an integral part of creating integrated solutions. Devant allows you to connect integrations using Connections. 

Using Connections, you can connect the integration you intend to deploy on Devant with other integrations on Devant or external services. Upon creating a connection to an integration on Devant, Devant provides you a Connection ID along with a set of connection parameters. Thereafter, you can configure your integration to establish a connection using this Connection ID and map connection parameters to environment variable names in your Devant integration. You can read these environment variable names in your integration implementation to retrieve the values, to create a programmatic connection to the integration or service you want to consume. 

At runtime, Devant dynamically injects values into the environment variables based on the configured mapping. This approach ensures that the connection parameter values and the integration connection creation remain loosely coupled, providing developers with flexibility and ease of maintenance.

You can add Connections with different visibility levels: Project and Integration. The visibility levels are described below:

## Project Connections

Project Connections are Connections you create to connect to services within a particular project. The Connections **can be used by any integration within the project**. 

For example, if you want to share a third-party service like Twilio across the project for all the integration within that project to reuse, you can create a project connection. Integration can refer to Project Connections using the connection ID. 
Project connections created to connect to Devant integrations under the OAuth security scheme will share the same OAuth application across the project. Any integration reusing such a connection will use the same client ID and client secret.

## Integration Connections

Integration Connections are Connections you define at the integration level and **used by only that integration**. 

For example, create an integration connection if you want to connect a legacy service to a given integration. Integration can refer to the integration connection using the connection ID. 
If your integration connects to more than one Devant integration, the integration connections created to connect to those Devant integrations under the OAuth security scheme can share the same OAuth application by sharing the same client ID and secret between all such connections.

[//]: # (ToDo: Enable this link after the required page is completed)
[//]: # (Learn how you can [share and reuse services using connections]&#40;../develop-components/sharing-and-reusing/create-a-connection.md&#41; in Devant.)
