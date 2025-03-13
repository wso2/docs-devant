# CI/CD

Devant provides a streamlined continuous integration and continuous deployment (CI/CD) experience to deploy integrations and services efficiently across multiple environments.

Devant creates environments for each project, where all integrations within the project share the environments. An environment is an isolated deployment area with restricted network and resource access. Services deployed in one environment cannot communicate with services deployed in another.

The Devant cloud data plane provides two default environments (i.e., development and production). However, if you are in a private data plane organization, you can customize and create multiple environments based on your requirements.

Devant adopts a *build once, deploy many* strategy to manage integrations across multiple environments. An integration is automatically built per commit. Then it is promoted to subsequent environments. This allows testing changes in lower, non-production environments like development before promoting the build to production.

Devant injects configurations and secrets that you maintain at the environment level into integrations at runtime. This ensures a strict separation of environment-specific configurations from source code. Although configurations can vary across environments, the code and the built container remain unchanged. Configurations and secrets include:

- Resource credentials to a database, cache, or other backing services.
- Credentials to external cloud services such as Amazon S3 or external APIs.

All configurations and secrets are encrypted at rest and in transit and stored in a secure vault. In a private data plane organization, you can store configurations and secrets in your infrastructure.

## Build

Devant automated build pipelines work as follows:

- Automatically builds a container image from the provided source code for the new commit.
- Runs security and vulnerability scans if applicable, depending on the integration type.
- Pushes the container image to a container registry. In the cloud data plane, Devant pushes the image to a Devant-managed registry. If it is a private data plane organization, Devant pushes the image to a registry that you own.
- Updates service endpoints and API specifications from the provided repository if applicable.

### Repeatable builds

Devant can replicate builds from an identical code version (Git commit). This means that multiple builds initiated from the same Git commit will generate Docker images with the same behavior.

!!! note
    In the event of multiple builds from the same code version, Devant preserves only the most recent version of the Docker image created from the particular code version.

### Trigger a build

On the **Build** page, click **Build Latest** to build the latest commit. If necessary, you have the option to build earlier commits. Change the button to **Show commits** from the dropdown and click **Show commits**. Select the commit from the commits pane and click **Build**.

### Build logs

You can view build logs for specific builds on the **Build** page.

To view details of a specific build, click **View Details** corresponding to the build.

## Deployment

Once Devant builds the latest commit it automatically deploys to the Development environment, you can track the deployments on the **Deploy** page.

### Immutable deployments

Once Devant deploys an integration with configurations, the configurations become immutable. Any subsequent change results in a new deployment.

### Promote an integration to a higher environment

Devant builds a container once per GitHub commit and then promotes it to subsequent higher environments.

You can go to the **Deploy** page of an integration and promote it manually across environments.

## Configurations

Devant allows you to define both environment-independent configurations and environment-specific configurations.

### Environment-independent configurations

These configurations apply to all environments.

To change environment-independent configurations, go to the **Deploy** page of the integration, make the necessary configuration changes via the **Set Up** card, and then trigger a new deployment to the initial environment. From there, you can proceed to promote the integration to higher environments.

### Environment-specific configurations

These configurations apply to a particular environment.

To change environment-specific configurations, go to the **Deploy** page of the integration, make the necessary configuration changes via the specific environment card, and trigger a new deployment.

[//]: # (Todo: enable the following)
[//]: # (To learn more about managing these configurations, see [Configuration Management]&#40;https://wso2.com/devant/docs/devant-concepts/configuration-management/&#41;.)

## Test

The information on the **Test** page is only applicable to automation and API.

For the automation, click **Test** to run the automation once. Select **Test with Arguments** to test your automation with arguments. You can view current and historic execution details along with a quick snapshot of recent activity via the total count of executions within the last 30 days. For each execution, you can view vital details such as the unique execution ID, the time it was triggered, and relevant revision information. Furthermore, you can dive deeper into the details by clicking on a specific execution to access its associated logs. This information enhances transparency, troubleshooting capabilities, and overall execution management, allowing you to easily monitor and analyze workflows.

For API, click **Console** in the **Test** dropdown to list all the resources in the API. Click **Get Test Key** to get a test key. Click a resource to expand it. Click **Try it out** and fill in the parameters (if any). Click **Execute** to invoke the resource. This will show the resource response and the execution details. You can also select the **API Chat** in the **Test** dropdown to test the API using an Intelligent Agent.

## Zero-downtime deployments

Devant performs rolling updates to ensure zero downtime between deployments and promotions.

A new build undergoes a health check before traffic is switched to it from the current build.

If you configure the necessary health checks for an integration, it can prevent deploying and promoting unhealthy versions of an integration.
