# Deploy Your First Event Integration

An event handle executes predefined actions in response to specific events. Devant simplifies the process of creating and deploying such integrations.

This guide walks you through the steps to create and deploy an event integration using WSO2 Integrator:BI and Devant.

In this guide, you will build a simple event integration that monitors RabbitMQ for new messages and displays them once they become available.

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If signing in to Devant for the first time, [create an organization](../references/create-an-organization.md) to begin with.
3. VS Code: [Install VS Code](https://code.visualstudio.com/download) if you don't have it installed already.
4. Set up RabbitMQ:
    - Use an existing RabbitMQ instance or start a new [RabbitMQ](https://www.rabbitmq.com/download.html) instance on a server that can be accessed via the internet.
    - Obtain the `host`, `port`, `username`, and `password` from the RabbitMQ instance.

## Step 1: Create the new integration

1. Import a new repository to begin your integration. Refer [Import a Repository](../references/import-a-repository.md) for more details.
2. Select the **Technology** as `WSO2 Integrator: BI`.
3. Choose the **Integration Type** as `Event Integration` and click **Create**.

This redirects you to the **Create New Integration in VS Code** page. 

## Step 2: Install the WSO2 Integrator: BI extension and open the integration

1. Install WSO2 Integrator: BI extension. Refer [Install and Set Up WSO2 Integrator: BI](../references/install-and-setup-wso2-integrator-bi.md) for more details.
2. Click **Develop in WSO2 Integrator: BI**. This will clone your integration project and open it in BI.

## Step 3: Develop Event Integration in WSO2 Integrator: BI

1. From the left side panel, click **+** on the **Configurations**, and add the following configurables.

    | Configurable        | Type       |
    |---------------------|------------|
    | `host`              | `string`   |
    | `port`              | `int`      |
    | `username`          | `string`   |
    | `password`          | `string`   |
    
    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-event-integration/add-configurables.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-event-integration/add-configurables.gif" alt="Add Configurations" width="80%"></a>

2. Go to the **Design View** by clicking the Home icon on the top left corner and click **Add Artifact**.
3. Select **RabbitMQ Event Handler**. Choosing the **Event Integration** from the Devant console disables the other options.
4. Provide the name of the **RabbitMQ Configuration** as `eventListener`.
5. Select previously defined `host` and `port` configuration variables for the **Host** and **Port**.
6. Then, expand the **Advanced Configurations** and enter the following configurables. Then click **Next**.

    | Field                   | Value        |
    |-------------------------|--------------|
    | **username**            | `username`   |
    | **password**            | `password`   |

7. Add `Orders` as the **Queue Name** and click **Create**. If there is no queue named `Orders` in RabbitMQ server, this will create a new queue with this name. 

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-event-integration/add-event-listener.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-event-integration/add-event-listener.gif" alt="Add Configurations" width="80%"></a>

8. In the **Design** view, click the `onMessage` function box. It will redirect you to the flow diagram view.
9. Click the plus icon after the **Start** node to open the node panel.
10. Add a **Log Info** node with the **Msg** as `message.toString()`. 

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-event-integration/implement-event-handler.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-event-integration/implement-event-handler.gif" alt="Add Configurations" width="80%"></a>

## Step 4: Push to Devant

1. Click the **Source Control** icon on the sidebar.
2. Click **+** to stage all changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to remote.
5. Go back to the **Design** view using the back arrow in the top left corner.
6. From the right side panel, click the **View in Devant** to view this integration in Devant.

## Step 5: Test the integration

1. Once you push the changes, the overview page of the Devant File Integration will automatically refresh and show you the **Latest Commit** and automatically build and show the **Build Status**.

    !!! note
        The build process may take some time. Once complete, the build status changes to **Success**. You can see the Build History by clicking **Build** in the left navigation.

2. Once the **Build Status** shows `Build completed`, click on `Configure to Continue` and details of RabbitMQ instance.

3. Send a sales order message to the **Orders** on the RabbitMQ server. You can send a sample sales order message similar to the following:

    ```json
    {
        "order_id": "12345",
        "customer_name": "John Doe",
        "product": "Widget",
        "quantity": 10,
        "total_amount": 100.00
    }
    ```

4. Observe the logs:
    - You can view the order message in the logs pane of the development card.

5. After successfully testing, you can promote your event integration to production by clicking the **Promote** button.

Now you have gained hands-on experience in creating, configuring, deploying, and testing an event integration.
