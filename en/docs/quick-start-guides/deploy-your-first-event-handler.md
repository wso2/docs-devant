# Deploy Your First Event Handler

An event handler executes predefined actions in response to specific events. Devant simplifies the process of creating and deploying such integrations.

This guide walks you through the steps to create and deploy an Event Handler using WSO2 MI and Devant.

In this guide, you will build a simple event handler that monitors RabbitMQ for new messages and displays them once they become available.

## Prerequisites

1. If signing in to Devant for the first time, [create an organization](../references/create-an-organization.md) to begin with.
2. Set up RabbitMQ:
    - Use an existing RabbitMQ instance or start a new [RabbitMQ](https://www.rabbitmq.com/download.html) instance on a server that can be accessed via the internet.
    - Obtain the `username`, `hostname`, `password`, and `vhost` from the RabbitMQ instance to use later as environment variables.

## Step 1: Attach a Git repository

1. Go to [https://console.devant.dev/new](https://console.devant.dev/new) and sign in. This opens the new integration page.
2. On the new integration page, click **Attach a Git Repository**.
3. Click **Use a Third-Party Public Git Repository** under **Authorize with GitHub**.
4. Click **Try with a sample**. This will automatically pick a sample repository managed by wso2.
5. Choose `/micro-integrator/RabbitMQIntegration` in the **Path** field.
6. Other fields are automatically populated for you. Choose the **Integration Type** as `Event Integration`.
7. Click **Create**.

## Step 2: Configure the event handler

Once you create the event handler, Devant will automatically build and deploy it to the development environment. You can now configure the event handler.

1. On the Development environment card, click **Configure**.
2. In the **Configure** pane, click **+ Add** corresponding to **Environment Configurations** and add the following environment variables:

    !!! tip
        Use the values from your RabbitMQ instance as per the [Prerequisites](#prerequisites) section for the environment variables.

       | **Name**     | **Value**                                         |
       | ------------- |--------------------------------------------------|
       | **HOSTNAME**  | Hostname of your RabbitMQ server                 |
       | **VHOST**     | Virtual hostname of your RabbitMQ server         |
       | **USERNAME**  | Username for connecting to RabbitMQ              |
       | **PASSWORD**  | Password associated with the RabbitMQ username   |

3. Click **Update**. This updates the event handler in the development environment.

## Step 3: Test the integration

1. Send a sales order message to the **SalesOrderQueue** on the RabbitMQ server. You can send a sample sales order message similar to the following:

    ```json
    {
        "order_id": "12345",
        "customer_name": "John Doe",
        "product": "Widget",
        "quantity": 10,
        "total_amount": 100.00
    }
    ```

2. Observe the logs:
    - You can view the order message in the logs pane of the development card.

Now you have gained hands-on experience in creating, configuring, deploying, and testing an event handler.
