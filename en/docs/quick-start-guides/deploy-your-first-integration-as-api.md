# Deploy Your First Integration as API

## Overview

In this guide, you will:

- Create a simple Integration as an API that acts as a service that calls a third-party endpoint and returns its response to the client. 
- The endpoint responds with a JSON, and the service deployed in Devant forwards this response to the client.
- Use WSO2 Integrator: BI to develop the API.
- Push the integration to Devant, which automatically builds and deploys the integration to the development environment.
- Test the integration.

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If signing in to Devant for the first time, [create an organization](../references/create-an-organization.md) to begin with.
3. VS Code: [Install VS Code](https://code.visualstudio.com/download) if you don't have it installed already.

## Step 1: Create the new integration

1. Attach a new repository to begin your integration. Refer [Attach a Repository](../references/attach-a-repository.md) for more details.
2. Select the **Technology** as `WSO2 Integrator: BI`.
3. Choose the **Integration Type** as `Integration as API` and click **Create**.

This redirects you to the **Create New Integration in VS Code** page. 

## Step 2: Install the WSO2 Integrator: BI extension and open the integration

1. Intall WSO2 Integrator: BI extension. Refer [Install and Set Up WSO2 Integrator: BI](../references/install-and-setup-wso2-integrator-bi.md) for more details.
2. Click **Develop in WSO2 Integrator: BI**. This will clone your integration project and open it in BI.

## Step 3: Develop automation in WSO2 Integrator: BI

Let’s build an API that calls the [https://dev-tools.wso2.com/gs/helpers/v1.0/countries](https://dev-tools.wso2.com/gs/helpers/v1.0/countries) endpoint and returns its response.

1. In the WSO2 Integrator: BI Design View, select **Add Artifact**.
2. Choose **HTTP Service**. Because **Integration as API** was selected in the Devant console, other artifact types are disabled.
3. Enter `countries` as the **Service base path**, then select **Create**.
4. Locate the `greeting` resource function and select the **Edit** button. Change the **Resource path** to `data`.
5. Select the resource function to open it in the flow diagram view.
6. In the flow diagram, select the **+** icon after the **Start** node to open the node panel.
7. Choose **+ Add Connection**, search for `HTTP`, and select it.
8. In the configuration panel, enter the **URL** as `"https://dev-tools.wso2.com/gs/helpers/v1.0/"` and select **Save**.
9. After saving, you’ll see `httpClient` under **Connections**. Select `get` to invoke the endpoint.
10. Set the following values for `get` operation and click **Save**.

    | Field                   | Value           |
    |-------------------------|-----------------|
    | **Variable name**       | `response`      |
    | **Target Type**         | `json`          |
    | **Path**                | `"/countries"`  |


11. Select the **+** icon again, choose the **Return** node, select `response` as the return value, and select **Save**.

<a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration-as-api/develop-integration-as-api.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration-as-api/develop-integration-as-api.gif" alt="Test API Response" width="80%"></a> 

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



