# Schedule Your First Automation

## Overview

In this guide, you will:

- Create a simple automation that prints `"Hello World"` every day.
- Use WSO2 Integrator: BI to develop the automation.
- Push the automation to Devant from the WSO2 Integrator: BI, which automatically builds the automation.
- Schedule the automation to run every day.

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If signing in to Devant for the first time, [create an organization](../references/create-an-organization.md) to begin with.
3. VS Code: [Install VS Code](https://code.visualstudio.com/download) if you don't have it installed already.

## Step 1: Create the new integration

1. Import a new repository to begin your integration. Refer [Import a Repository](../references/import-a-repository.md) for more details.
2. Select the **Technology** as `WSO2 Integrator: BI`.
3. Choose the **Integration Type** as `Automation` and click **Create**.

This redirects you to the **Create New Integration in VS Code** page. 

## Step 2: Install the WSO2 Integrator: BI extension and open the integration

1. Install WSO2 Integrator: BI extension. Refer [Install and Set Up WSO2 Integrator: BI](../references/install-and-setup-wso2-integrator-bi.md) for more details.
2. Click **Develop in WSO2 Integrator: BI**. This will clone your integration project and open it in BI.

## Step 3: Develop automation in WSO2 Integrator: BI

1. In WSO2 Integrator: BI design view, click **Add Artifact**.
2. Select **Automation** from the Constructs menu. Since **Automation** is chosen from the Devant console, other options are disabled.
3. Click **Create** to create an automation. This directs you to the automation diagram view.
4. Click **+** after the **Start** node to open the node panel.
5. Select **Call Function** and select **println**.
6. Click **+ Add Another Value**, type `"Hello World"` and click **Save**.
7. Click **Run** in the top right corner to run the automation. This compiles the automation and runs it in the embedded Ballerina runtime.

    <div style="width: 80%;">
    ![Design Integration](../../assets/img/get-started/schedule-your-first-automation/design-integration.gif)
    </div>

## Step 4: Push to Devant

1. Click the **Source Control** icon on the sidebar.
2. Click **+** to stage all changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to remote.

## Optional: Test the Automation manually

You can execute your automation directly from the environment card on the **Overview** page:

1. On the Overview page, locate the **Development** card.
2. Click **Test** to run your automation immediately.

    !!! info "Inject Dynamic Values into Your Application as Command-Line Arguments"
        To pass dynamic values to your application when testing manually, follow these steps:

        1. Click the drop-down icon next to **Test** and then click **Test with Arguments**.
        2. In the **Runtime Arguments** pane, enter the arguments you want to pass to your application.
        3. Click **Execute**. This triggers the task with the specified arguments.

        The capability to run a manual task with arguments is supported for the following build presets:

        === "WSO2 MI"
            To explore a WSO2 MI-based manual task with arguments, try out the [Weather to Logs Task](https://github.com/wso2/choreo-samples/tree/main/weather-to-logs-mi-manual-task) sample. For instructions, see the `README.md` file in the sample repository.

            !!! info
                When working on WSO2 MI projects and deploying a WSO2 MI integration as a manual task in Choreo, use the WSO2 MI automation mode. For details, see [Running the Micro Integrator in Automation Mode](https://mi.docs.wso2.com/en/latest/install-and-setup/install/running-the-mi-in-automation-mode/).

        === "WSO2 BI"
            To explore a Ballerina manual task with arguments, try out the [Weather to Email Task](https://github.com/wso2/choreo-samples/tree/main/weather-to-email-integration) sample. For instructions, see the `README.md` file in the sample repository.

            !!! info
                If you want to pass arguments to Ballerina main functions, use the **Test with Arguments** capability. For details on the arguments you can pass, see the [Ballerina documentation](https://ballerina.io/learn/by-example/main-function/). You can also override configurable values in the same manner. For more information, see [Provide values to configurable variables](https://ballerina.io/learn/provide-values-to-configurable-variables/#provide-via-command-line-arguments).
    !!! note
        As user portal features are added, testing and other actions will be accessible directly from the **Overview** page, making it easier to manage and validate your automations.

## Step 5: Schedule Automation

1. Once you push the changes, the overview page of the Devant automation will automatically refresh and show you the **Latest Commit** and automatically build your automation showing the **Build Status**.

    !!! note
        The build process may take some time. Once complete, the build status changes to **Success**. You can see the Build History by clicking **Build** in the left navigation.

2. Once the **Build Status** shows `Build completed`, click **Test** to run your automation once.
3. The development card automatically updates with execution details. Click the refresh button in the top right corner if it is not automatically updated.
4. Click **View Logs** on an execution. You will see the `Hello World` log printed along with the execution time.
5. Click **Schedule** to schedule the automation.
6. In the **BY INTERVAL** tab, select **Day** from the dropdown.
7. Enter `1` in the **Repeat every** text box.
8. Enter `01:00 AM` in the **At** text box and click **Update**.
9. Your automation will now run every day at 01:00 AM. You can see the next execution time as **Next run in** in the Development card.

    <div style="width: 80%;">
    ![View Logs](../../assets/img/get-started/schedule-your-first-automation/view-logs.gif)
    </div>

10. After successfully testing, you can promote your automation to production by clicking the **Promote** button.
11. Once promoted to production, click **Run** to run your automation immediately.
    
    !!!info
        If you want to pass runtime arguments when running in production, use the **Run with Arguments** option in the same way as described above in the [Test the Automation manually](#optional-test-the-automation-manually) section.

12. In critical environments (Production), you will be able to see automation metrics such as:

    - **Error Rate**: Percentage of failed executions
    - **Average Duration**: Average time taken for executions
    - **99th Percentile Latency**: Latency at the 99th percentile for executions
    - **Total Executions**: Total number of times the automation has been executed

    <div style="width: 80%;">
    ![Automation Metrics](../../assets/img/get-started/schedule-your-first-automation/metrics.png)
    </div>
