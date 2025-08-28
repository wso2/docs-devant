## Overview

In this guide, you will:

- Create a simple Integration as an API that acts as a service that calls a third-party endpoint and returns its response to the client. 
- The endpoint responds with a JSON, and the service deployed in Devant forwards this response to the client.
- Use WSO2 Integrator: MI to develop the API.
- Push the integration to Devant, which automatically builds and deploys the integration to the development environment.
- Test the integration.

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If signing in to Devant for the first time, [create an organization](../references/create-an-organization.md) to begin with.
3. VS Code: [Install VS Code](https://code.visualstudio.com/download) if you don't have it installed already.

## Step 1: Create the new integration

1. Import a new repository to begin your integration. Refer [Import a Repository](../references/import-a-repository.md) for more details.
2. Select the **Technology** as `WSO2 Integrator: MI`.
3. Choose the **Integration Type** as `Integration as API` and click **Create**.

This redirects you to the **Create New Integration in VS Code** page. 

## Step 2: Install the WSO2 Integrator: MI extension and open the integration

1. Install WSO2 Integrator: MI extension. Refer [Install and Set Up WSO2 Integrator: MI](https://mi.docs.wso2.com/en/latest/develop/mi-for-vscode/install-wso2-mi-for-vscode/) for more details.

    !!! note
        If you don't have the required Java version and Micro Integrator Runtime installed, the extension will prompt you to install them. The extension will automatically install the required dependencies once you accept the installation.
        
2. Click **Develop in WSO2 Integrator: MI**. This will clone your integration project and open it in MI. 

## Step 3: Develop the integration as an API in WSO2 Integrator: MI

Let’s build an API that calls the [https://dev-tools.wso2.com/gs/helpers/v1.0/countries](https://dev-tools.wso2.com/gs/helpers/v1.0/countries) endpoint and returns its response.

1. In the WSO2 Integrator: MI Design View, it will automatically open the API Form, where you can create the API.
2. Enter the **Name** as `countries`. It will automatically populate the **Context** field as well. Then click **Create**.
3. Locate the `/` resource function and select it.
4. In the top left corner of the **Resource View**, click on the **Edit** button and change the **Resource Path** to `/data`. Then click **Update**.
5. Now, in the flow diagram, select the **+** icon after the **Start** node to open the node panel.
7. Under **Connections** tab, click **+ Add new connection**.
8. Choose **HTTPS** connection.
9. Give an appropriate **Connection Name** and enter the **Base URL** as `https://dev-tools.wso2.com/gs/helpers/v1.0/`, then click **Add**.
10. The **Connections** tab must now show the created connection. There, choose the `GET` method.
11. Enter `/countries` as the **Relative Path**, and set the **Output Variable Name** as `response`, and make sure **Overwrite Message Body** is unchecked.

    !!! note
        If you leave **Overwrite Message Body** checked, that would overwrite the *Payload*, which lets you skip Step 12 & 13. We use Step 12 & 13 so that we can modify the response per your requirement. However, in this Demo, it is not required.

12. Select the **+** icon again to add another node. 
13. In the node panel, select **Payload** and click on the $fx$ icon to open the **Expression Editor**. There, select **Variables**, then under `response` variable, select `payload`, then click **Add**.
14. Add another node after the **Payload** node, and add a **Respond** node, which responds with the existing payload.
15. Click **Run** in the top right corner to test it locally. This compiles the integrator and you can try out the API using the **Runtime Services** panel.

    <div style="width: 80%;">
    ![Test API Response](../../assets/img/get-started/deploy-your-first-integration-as-api/develop-integration-as-api-mi.gif)
    </div>

## Step 4: Push to Devant

1. Click the **Source Control** icon on the sidebar.
2. Click **+** to stage all changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to remote.
5. Go back to the **Design** view using the back arrow in the top left corner.
6. From the right side panel, click the **View in Devant** to view this integration in Devant.


## Step 5: Test the API

1. After you push, Devant detects the commit, builds it, and deploys the integration to the development environment, showing the status on the overview page.

    !!! note
        The build process may take some time. Once complete, the build status changes to **Success**. You can see the Build History by clicking **Build** in the left navigation.

2. Once the **Build Status** shows as `Build completed`, click **Test** on the development environment card. This will bring you to the **Console** page.
3. Click **Get Test Key** to get a key for testing.
4. You will have a single resource available **GET /**. Click to expand the resource.
5. Click **Try it out**.
6. Click **Execute**. You will see the response from the backend service as a JSON.
7. After successfully testing, you can promote your event integration to production by clicking the **Promote** button.