# Resource Hierarchy


The following diagram depicts the high-level resources and their relationships in Devant.

[//]: # (Todo: Update the diagram with the new design)
![Resource hierarchy](../assets/img/devant-concepts/resource-hierarchy.png){.cInlineImage-full}

## Organizations and data planes

Data planes are connected to the organization and are available for all projects within the organization. When you create an environment in a project, the data plane connected to the organization is linked with an automatically generated Kubernetes namespace.

## Environments and clusters

Devant allows multiple Kubernetes clusters to be associated with an environment. This enables you to build highly resilient and resource-efficient solutions that utilize multiple clusters. Devant synchronizes your integrations and workloads between associated clusters in an environment, allowing you to perform multi-cluster deployment with a single click.

[//]: # (Todo: Uncomment the following line with the updated diagram)
[//]: # (The following diagram illustrates how multiple clusters associate with different environments:)

[//]: # (![Environments and dataplanes]&#40;../assets/img/devant-concepts/environments-and-dataplanes.png&#41;{.cInlineImage-full})

!!! info "Note"
    It is not necessary to use a different cluster per environment. You can create multiple environments on the same cluster. The above diagram is an example of a specific solution. Your integration architecture may require a different configuration than what is depicted.

## Integrations and environments

Integration belongs to a project in Devant, and environments are provisioned per project. When an integration is deployed, it is deployed as a container to the specified environment. Once deployed, you can promote the container image across the environments available in the project.
