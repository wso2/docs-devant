# Connections

Services can exist in two main forms: standalone and integrated. Connecting services is an integral part in creating integrated solutions. Devant allows you to connect services using Connections. 

Using Connections, you can integrate the service you intend to deploy on Devant with other services on Devant or external resources. Upon creating a connection to a service on Devant, Devant provides you a Connection ID along with a set of connection parameters. Thereafter, you have the capability to configure your service to establish a connection using this Connection ID and map connection parameters to environment variable names in your Devant component. You can read these environment variable names in your service implementation to retrieve the values, to create a programmatic connection to the service you want to consume. 

At runtime, Devant dynamically injects values into the environment variables based on the configured mapping. This approach ensures that the connection parameter values and the service connection creation remain loosely coupled, providing developers with flexibility and ease of maintenance.

You can add Connections in different visibility levels: Project and Component. The visibility levels are described below:

## Project Connections

Project Connections are Connections you create to connect to services within a particular project. The Connections **can be used by any component within the project**. 

For example, if you want to share a third-party service like Twilio across the project for all the components within that project to reuse, you can create a project connection. Components can refer to Project Connections using the connection ID. 
Project connections created to consume Devant services under the OAuth security scheme will share the same OAuth application across the project. Any component reusing such a connection will use the same client ID and client secret.

## Component Connections

Component Connections are Connections you define at the component level and **used by only that component**. 

For example, create a component connection if you want to connect a legacy service to a given component. Components can refer to the Component Connection using the connection ID. 
If your component consumes more than one Devant service, the Component connections created to consume those Devant services under the OAuth security scheme can share the same OAuth application by sharing the same client ID and secret between all such connections.

Learn how you can [share and reuse services using connections](../develop-components/sharing-and-reusing/create-a-connection.md) in Devant.
