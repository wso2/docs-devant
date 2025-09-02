# Deploy a WSO2 Integrator: MI project on Devant

[WSO2 Integrator: MI](https://wso2.com/integrator/mi/) is a 100% open source low-code integration solution with an AI-powered development experience. This guide will help you deploy a WSO2 Integrator: MI project on Devant.

## Overview

In this guide, you will:

- Create a simple automation that prints `"Hello World"` every day.
- Use WSO2 Integrator: MI to develop the automation.
- Push the automation to Devant from the WSO2 Integrator: MI, which automatically builds the automation.
- Schedule the automation to run every day.

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If signing in to Devant for the first time, [create an organization](../references/create-an-organization.md) to begin with.
3. VS Code: [Install VS Code](https://code.visualstudio.com/download) if you don't have it installed already.

## Step 1: Create the new integration

1. Import a new repository to begin your integration. Refer [Import a Repository](../references/import-a-repository.md) for more details.
2. Select the **Technology** as `WSO2 Integrator: MI`.
3. Choose the **Integration Type** as `Automation` and click **Create**.

This redirects you to the **Create New Integration in VS Code** page. 

## Step 2: Install the WSO2 Integrator: MI extension and open the integration

1. Install WSO2 Integrator: MI extension. Refer [Install and Set Up WSO2 Integrator: MI](https://mi.docs.wso2.com/en/latest/develop/mi-for-vscode/install-wso2-mi-for-vscode/) for more details.

    !!! note
        If you don't have the required Java version and Micro Integrator Runtime installed, the extension will prompt you to install them. The extension will automatically install the required dependencies once you accept the installation.

2. Click **Develop in WSO2 Integrator: MI**. This will clone your integration project and open it in MI. 

## Step 3: Develop automation in WSO2 Integrator: MI

1. In the WSO2 Integrator: MI Design View, it will automatically open the Sequence Form, where you can create the automation.
2. Give the automation an appropriate **Name** and click **Create**.
3. A notification would pop up saying `The pom.xml file has been modified. Do you want to update the dependencies?` in the bottom right corner. Click **Yes**.
4. Click **+** after the **Start** node to open the node panel.
5. Select **Log** and enter `Hello World` in the **Message** field. Then click **Add**.

    <div style="width: 80%;">
    ![Design Integration](../../assets/img/devant-samples/develop-in-mi.gif)
    </div>

## Step 4: Push to Devant

1. Click the **Source Control** icon on the sidebar.
2. Click **+** to stage all changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to the remote.

## Step 5: Schedule the automation

1. Once you push the changes, the overview page of the Devant automation will automatically refresh and show you the **Latest Commit**. Then Devant will automatically build your automation, showing the **Build Status**.

    !!! note
        The build process may take some time. Once complete, the build status changes to **Success**. You can see the Build History by clicking **Build** in the left navigation.

2. Once the **Build Status** shows `Build completed`, click **Test** to run your automation once.
3. The development card automatically updates with execution details. Click the refresh button in the top right corner if it is not automatically updated.
4. Click **View Logs** on an execution. You will see the `Hello World` log printed along with the execution time.

    !!! tip
        You can search for the `Hello World` keyword to locate the log quickly.

5. Click **Schedule** to schedule the automation.
6. In the **BY INTERVAL** tab, select **Day** from the dropdown.
7. Enter `1` in the **Repeat every** text box.
8. Enter `01:00 AM` in the **At** text box and click **Update**.
9. Your automation will now run every day at 01:00 AM. You can see the next execution time as **Next run in** in the Development card.

    <div style="width: 80%;">
    ![View Logs](../../assets/img/devant-samples/devant-schedule.gif)
    </div>

10. After successfully testing, you can promote your automation to production by clicking the **Promote** button.