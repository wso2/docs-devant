---
title: Develop Your First File Integration
description: Learn how to develop your first file integration in Devant.
---

# Develop Your First File Integration

## Overview

In this guide, you will:

- Create an FTP listener that fetches recent weather data.
- Use WSO2 Integrator: BI to develop the File integration.
- Push the File Integration to Devant from WSO2 Integrator: BI, which will automatically build and deploy it into the development environment.
- Test the File Integration.
- Promote it to the production environment and use it as an API.

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If signing in to Devant for the first time, [create an organization](../references/create-an-organization.md) to begin with.
3. VS Code: [Install VS Code](https://code.visualstudio.com/download) if you don't have it installed already.

## Step 1: Create the new integration

1. Import a new repository to begin your integration. Refer [Import a Repository](../references/import-a-repository.md) for more details.
2. Select the **Technology** as `WSO2 Integrator: BI`.
3. Choose the **Integration Type** as `File Integration` and click **Create**.

This redirects you to the **Create New Integration in VS Code** page. 

## Step 2: Install the WSO2 Integrator: BI extension and open the integration

1. Install WSO2 Integrator: BI extension. Refer [Install and Set Up WSO2 Integrator: BI](../references/install-and-setup-wso2-integrator-bi.md) for more details.
2. Click **Develop in WSO2 Integrator: BI**. This will clone your integration project and open it in BI.

## Step 3: Develop File Integration in WSO2 Integrator: BI

1. From the left side panel, click **+** on the **Configurations**, and add the following configurables.

    | Configurable        | Type       |
    |---------------------|------------|
    | `host`              | `string`   |
    | `username`          | `string`   |
    | `password`          | `string`   |
    | `path`              | `string`   |
    | `pattern`           | `string`   |

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-file-integration/add-configurables.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-file-integration/add-configurables.gif" alt="Add Configurations" width="80%"></a>

2. Go to the **Design View** by clicking the Home icon on the top left corner and click **Add Artifact**.
3. Select **FTP Service**. Choosing the **File Integration** from the Devant console disables the other options.
4. Provide the name of the **Listener Configuration** as `weatherListener`.
5. Then expand the **Advanced Configurations** and enter the following configurables:

    | Field                   | Value                                                          |
    |-------------------------|----------------------------------------------------------------|
    | **Host**                | `host`                                                         |
    | **Auth**                | `{ credentials: { username: username, password: password }}`   |
    | **Path**                | `path`                                                         |
    | **FileNamePattern**     | `pattern`                                                      |

6. Click **Next**, and you will see the created listener with the name `weatherListener`. 
7. Then click on **Create**. It will redirect you to the **Service Designer** view.

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-file-integration/setup-listener-and-service-configs.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-file-integration/setup-listener-and-service-configs.gif" alt="Setup listener & service configs" width="80%"></a>

8. In the **Design** view, click the `onFileChange` function box. It will redirect you to the flow diagram view.
9. Click the plus icon after the **Start** node to open the node panel.
10. Select **Foreach** and enter the following values in relevant fields:

    | Field               | Value              |
    |---------------------|--------------------|
    | **Variable Name**   | `addedFile`        |
    | **Variable Type**   | `var`              |
    | **Collection**      | `event.addedFiles` |

11. Under the **Foreach** node, add a **Log Info** node with the **Msg** as `"File added:" + addedFile.name`. 

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-file-integration/implement-onfilechange.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-file-integration/implement-onfilechange.gif" alt="Setup listener & service configs" width="80%"></a>

## Step 4: Push to Devant

1. Click the **Source Control** icon on the sidebar.
2. Click **+** to stage all changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to remote.
5. Go back to the **Design** view using the back arrow in the top left corner.
6. From the right side panel, click the **View in Devant** to view this integration in Devant.

## Step 5: Test File Integration

1. Once you push the changes, the overview page of the Devant File Integration will automatically refresh and show you the **Latest Commit** and automatically build and show the **Build Status**.

    !!! note
        The build process may take some time. Once complete, the build status changes to **Success**. You can see the Build History by clicking **Build** in the left navigation.

2. Once the **Build Status** shows `Build completed`, click on `Configure to Continue` and add the sample FTP service details.

    | Configurable        | Value                                 |
    |---------------------|---------------------------------------|
    | `host`              | `tgftp.nws.noaa.gov`                  |
    | `username`          | `anonymous`                           |
    | `password`          | `""`                                  |
    | `path`              | `/data/observations/metar/decoded/`   |
    | `pattern`           | `(.*).TXT`                            |


3. Once the deployment is successful, you can view the logs printed by the weather listener in the development card.
4. After successfully testing, you can promote your File Integration to production by clicking the **Promote** button.
5. Once deployed to production, you can access your File Integration through the API endpoints and embed it in your applications.
