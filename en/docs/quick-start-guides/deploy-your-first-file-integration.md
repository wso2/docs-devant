# Deploy Your First File Integration

## Overview

In this guide, you will:

- Create a FTP listener that fetches recent weather data.
- Use Ballerina Integrator to develop the File integration.
- Push the File Integration to Devant from Ballerina Integrator, which will automatically build and deploy it into the development environment.
- Test the File Integration.
- Promote it to the production environment and use it as an API.

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already. 
2. If signing in to Devant for the first time, create an organization:
    1. Go to [https://console.devant.dev/](https://console.devant.dev/) and sign in using Google, GitHub, or Microsoft account.
    2. Enter a unique organization name. For example, `Stark Industries`.
    3. Read and accept the privacy policy and terms of use and click **Create**.
3. VS Code: [Install VS Code](https://code.visualstudio.com/download) if you don't have it installed already.

## Step 1: Attach a Git repository
1. Go to [https://console.devant.dev/new](https://console.devant.dev/new) and sign in. This opens the new integration page.
2. On the new integration page, click **Attach a Git Repository**.

    !!! tip
        If you're using a public Git repository, you can skip ahead to sub-step 8. Click **Use a Third-Party Public Git Repository** and enter the repository URL.

3. Click **Authorize with GitHub** to connect Devant to your GitHub account. If you haven't connected your GitHub repository to Devant, authorize the WSO2 cloud app with your GitHub account [WSO2 Cloud App](https://github.com/marketplace/choreo-apps).
4. Under the **Organization**  dropdown click **+ Add**. This redirects you to the **Install WSO2 Cloud App** page.
5. Select your GitHub account and install [WSO2 Cloud App](https://github.com/marketplace/choreo-apps)

    !!! note
        The **WSO2 Cloud App** requires:

        - Read and write access to code and pull requests.
        - Read access to issues and metadata.

         You can [revoke access](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/reviewing-your-authorized-integrations#reviewing-your-authorized-github-apps) at any time. Write access is used to push changes directly to your repository.

6. Under the **Organization**  dropdown, select your organization. If it is still not listed, click the Refetch button.
7. Select a repository to save your integration.
8. Select a **Branch** and a **Path** of the selected repository to save your integration.
9. **Name** and **Identifier** fields are automatically populated. Additionally, you can edit them to your preference.
10. Select the **Technology** as `Ballerina Integrator`.
11. Choose the **Integration Type** as `File Integration` and Click **Create**.

This redirects you to the overview page of the File Integration. Now, let's develop the File Integration.

## Step 2: Install the Ballerina Integrator extension

1. Click **Install Ballerina Integrator extension** on the overview page. This opens the VS Code extensions page.
2. Click **Install** to install the extension. This installs both **Ballerina Integrator** and **Ballerina** extensions on VS Code.

## Step 3: Set up Ballerina Integrator for the first time
1. Click the Ballerina Integrator icon on the sidebar.

    <a href="{{base_path}}/assets/img/get-started/bi-icon.png"><img src="{{base_path}}/assets/img/get-started/bi-icon.png" alt="Ballerina Integrator Icon" width="80%"></a>

2. Click **`Set Up Ballerina Integrator`**. The setup wizard installs and configures the [Ballerina](https://ballerina.io/) distribution required for the Ballerina Integrator.
3. Click **`Restart VS Code`** to complete the setup.

    <a href="{{base_path}}/assets/img/get-started/bi-setup.gif"><img src="{{base_path}}/assets/img/get-started/bi-setup.gif" alt="Ballerina Integrator Setup" width="80%"></a>

    !!! note
        If you already have the integration logic configured or want to immediately push your existing changes to Devant, you can
        skip directly to [Step 5: Push to Devant](#step-5-push-to-devant)

        - You can find a ready-made file integration example here: 
        [weather-data-listener](https://github.com/wso2/integration-samples/tree/main/ballerina-integrator/weather-data-listener)

        Otherwise, continue with the steps below to build the FTP-based file integration flow from scratch.

## Step 4: Develop File Integration in VS Code
1. Go to the Overview page of the integration you have created and click **Develop in Ballerina Integrator**. This will clone your project and open it in Ballerina Integrator.
2. In the Ballerina Integrator design view, click **Add Artifact**.
3. Select **FTP Service** from the Constructs menu. Choosing the **File Integration** from the Devant console disables the other options.
4. From the left side panel, click **+** on the **Configurations**, and add the following configurables,

    | Configurable        | Type       | Default                |
    |---------------------|------------|------------------------|
    | `ftpUser`           | `string`   | `"anonymous"`          |
    | `ftpPassword`       | `string`   | `""`                   |
    | `ftpHost`           | `string`   | `"tgftp.nws.noaa.gov"` |

5. Provide the name of the **Listener Configuration** as `WeatherListener`.

6. Then expand the **Advanced Configurations** and enter the following configurables:

    | Field                   | Value                                                          |
    |-------------------------|----------------------------------------------------------------|
    | **Protocol**            | `ftp:FTP`                                                      |
    | **Host**                | `ftpHost`                                                      |
    | **Port**                | `21`                                                           |
    | **Auth**                | `{ credentials: { username: ftpUser, password: ftpPassword }}` |
    | **Path**                | `"/data/observations/metar/decoded/"`                          |
    | **FileNamePattern**     | `"(.*).TXT"`                                                   |
    | **PollingInterval**     | `10`                                                           |

7. Click **Next**.
8. Then enter the **Service Configuration** name as `WeatherListener` and click on **Create**. It will redirect you to the
**Service Designer** view.
9. Click the `+ Function` button on top right corner in the **Service Designer** view.
10. Select the `onFileChange` as the **Available Function** and click **Save**.
11. Then go to the **Design** view by clicking the Home icon on top left corner of the **Service Designer** view.
12. In the **Design** view, click the `onFileChange` function box. It will redirect you to the flow diagram view.
13. Click the plus icon after the **Start** node to open the node panel.
14. Select **Foreach** and enter the following values in relevant fields:

    | Field               | Value              |
    |---------------------|--------------------|
    | **Variable Name**   | `addedFile`        |
    | **Variable Type**   | `ftp:FileInfo`     |
    | **Collection**      | `event.addedFiles` |

15. Under the **Foreach** node, add a **Declare Variable** node with the following values:

    | Field          | Value                                  |
    |----------------|----------------------------------------|
    | **Name**       | `fileStream`                           |
    | **Type**       | `stream<byte[] & readonly, io:Error?>` |
    | **Expression** | `caller->get(addedFile.pathDecoded)`   |

16. Add another **Declare Variable** node with:

    | Field          | Value                             |
    |----------------|-----------------------------------|
    | **Name**       | `content`                         |
    | **Type**       | `record {\|byte[] value;\|}\|()`  |
    | **Expression** | `check fileStream.next()`         |

17. Add an **If** node with the following condition: `content is record {| byte[] value; |}` Also, 
click **+ Add Else Block** to define an alternative execution path.
18. The same way, select the **Call Function** from the node panel and search for `fromBytes` and select it.
19. Enter the following values in relevant fields and save it:

    | Field               | Value           |
    |---------------------|-----------------|
    | **Variable Name**   | `fileContent`   |
    | **Variable Type**   | `string`        |
    | **Bytes**           | `content.value` |

20. Next, select **Declare Variable** from the node panel and enter the following values:

    | Field          | Value                       |
    |----------------|-----------------------------|
    | **Name**       | `firstLineIndex`            |
    | **Type**       | `int\|()`                   |
    | **Expression** | `fileContent.indexOf("\n")` |

21. Add another **If** node with the condition: `firstLineIndex is int`.
22. Inside the if block (where the condition is `firstLineIndex is int`), add a **Declare Variable** node with 
the following properties:

    | Field          | Value                                      |
    |----------------|--------------------------------------------|
    | **Name**       | `location`                                 |
    | **Type**       | `string`                                   |
    | **Expression** | `fileContent.substring(0, firstLineIndex)` |

23. Add a **Log Info** node below the location variable. Set the **Msg** to: `"Received weather information from: " + location`.
24. In the else block of the first if condition (which checks content is `record {| byte[] value; |}`), add a **Log Error** node. Set the **Msg** to: `"Failed to read weather content"`.

## Step 5: Push to Devant
1. Click the **Source Control** icon on the sidebar.
2. Click **+** to stage all changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to remote.
5. Go back to the **Design** view using the back arrow in the top left corner.
6. From the right side panel, click the **View in Devant** to view this integration in Devant.

## Step 6: Test File Integration
1. Once you push the changes, the overview page of the Devant File Integration will automatically refresh and show you the **Latest Commit** and automatically builds and shows the **Build Status**.

    !!! note
        The build process may take some time. Once complete, the build status changes to **Success**. You can see the Build History by clicking **Build** in the left navigation.

2. Once the **Build Status** shows `Build completed`, it will be automatically deployed into the development card.
3. Once the deployment is successful, you can view the logs printed by the weather listener in the development card. If no logs are visible, try clicking the refresh button.
4. After successfully testing, you can promote your File Integration to production by clicking the **Promote** button.
5. Once deployed to production, you can access your File Integration through the API endpoints and embed it in your applications.
