# Deploy Your First Integration as API

## Overview

In this guide, you will:

- Create a simple Integration as an API that calls a backend service and returns its response to the client. 
- The backend service responds with a JSON with a key `message` and the value `Hello World!!!`, and the API deployed in Devant forwards this response to the client.
- Use WSO2 Micro Integrator (MI) to develop the API.
- Push the integration to Devant, which automatically builds and deploys the integration to the development environment.
- Test the integration.

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If you're signing in to the Devant for the first time, create an organization:
    1. Go to [https://console.devant.dev/](https://console.devant.dev/) and sign in using your Google, GitHub, or Microsoft account.
    2. Enter a unique organization name. For example, `Stark Industries`.
    3. Read and accept the privacy policy and terms of use and Click **Create**.
3. VSCode: [Install VSCode](https://code.visualstudio.com/download) if you don't have it installed already.

## Step 1: Attach a Git repository
1. Go to [https://console.devant.dev/](https://console.devant.dev/) and sign in. This opens the organization overview page and lists the projects.
2. Select the **Default** project.
3. On the project overview page, click **Attach a Git Repository**.
4. Click **Authorize with GitHub** to connect Devant to your GitHub account. If you haven't connected your GitHub repository to Devant, authorize the WSO2 cloud app stage with your GitHub account [WSO2 Cloud App](https://github.com/marketplace/choreo-apps).
5. Under the **Organization**  dropdown click **+ Add**. This redirects you to the **Install WSO2 Cloud App Stage** page.
6. Select your GitHub account and install [WSO2 Cloud App](https://github.com/marketplace/choreo-apps)

    !!! note
        The **WSO2 Cloud App** requires:
        - Read and write access to code and pull requests.
        - Read access to issues and metadata.

         You can [revoke access](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/reviewing-your-authorized-integrations#reviewing-your-authorized-github-apps) at any time. Write access is used to push changes directly to your repository.

7. Under the **Organization**  dropdown, select your organization. If it is still not listed, click the Refetch button.
8. Select a repository to save your integration. Additionally, you can select a **Branch** and a **Path** of the selected repository to save your integration.
9. **Name** and **Identifier** fields are automatically populated. Additionally, you can edit them to your preference.
10. Select the **Technology** as `WSO2 MI`.
11. Choose the **Integration Type** as `Integration as API` and Click **Create**.

This redirects you to the overview page of the integration. Now, let's design the integration.

## Step 3: Install the MI extension

1. Click **Install Micro Integrator extension** on the overview page. This opens the VSCode extensions page.
2. Click **Install** to install the extension. This installs the development environment for MI on VSCode.

[//]: # (Todo: this step may be not needed in future. MI extension will detect the Devant projct and use it)
## Step 3: Create a new MI project
1. Click on the MI icon on the Activity Bar of the VSCode editor.
   <a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/mi_icon.png"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/mi_icon.png" alt="Micro Integrator Icon" width="70%"></a>
2. Click **Create New Project** on MI Project Explorer. For more options for creating a new integration project, see [Create an Integration Project](https://mi.docs.wso2.com/en/latest/develop/create-integration-project/).
3. Enter the following details:

   | **Field**                                       | **Value**         |
   |-------------------------------------------------|-------------------|
   | **Project Name**                                | HelloWorld        |
   | **Micro Integrator runtime version**            | 4.4.0             |


4. Provide a location for the integration project under **Project Directory**.
5. Click **Create**. This creates the project and opens the **Add Artifact** pane.

!!! note
    You need the following to work with the MI for VSCode extension.

    - Java Development Kit (JDK) version 21
    - WSO2 Micro Integrator (MI) 4.4.0 runtime

    If you don't have them installed on your local machine, the MI for VSCode extension automatically prompts you to download and configure them during the project creation step:

    1. Click **Download Java & MI** to download and set up Java and MI runtime.

        <a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/download-java-and-mi.png"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/download-java-and-mi.png" alt="Download Java and MI" width="80%"></a>

        !!! info
            If your local machine has a different JDK or WSO2 MI version installed, the system will prompt you to download the required versions. 

            1. Click **Download** to install the required JDK or/and MI version(s).
            2. Once the download is complete, configure the Java Home or/and MI Home paths by clicking **Select Java Home** or/and **Select MI Path**, respectively.

            If the required JDK and WSO2 MI versions are already installed, you can directly configure the Java Home and MI Home paths in this step by clicking **Select Java Home** and **Select MI Path**, respectively.

        Once the process is complete, a window reload is required, and you will be prompted with the following message:

        <a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/reload-window.png"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/reload-window.png" alt="Reload Window" width="80%"></a>

    2. Click **Reload Window**.

## Step 2 - Create an API

Now, the integration project is ready to add an API. In this scenario, the API calls a backend service and responds to the client. First, let's create an API.

1. In the **Add Artifact** interface, under **Create an Integration**, click on **API**. This opens the **API Form**.

2. Enter `HelloWorldAPI` as the API **Name**. The system automatically populates the API **Context** field with the same value.

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/new-api.png"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/new-api.png" alt="Create New API" width="80%"></a>

3. Click **Create**.

Once you create the API, a default resource is automatically generated. You can see this default resource listed in the **Service Designer** under **Available resources**. You'll use this resource in this tutorial.

## Step 3 - Design the integration

Now, it's time to design your API. This underlying logic is executed behind the scenes when an API request is made. In this scenario, you first need to call the backend service. For that, you have to add an [HTTP connection](https://mi.docs.wso2.com/en/latest/reference/connectors/http-connector/http-connector-overview/). Follow the below steps to create an HTTPS connection.

1. Open the **Resource View** of the API resource by clicking the `GET` resource under **Available resources** on **Service Designer**.

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/get-resource.png"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/get-resource.png" alt="Add new connection" width="80%"></a>

2. Once you open the **Resource View**, click on the **+** icon on the canvas to open the palette.

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/open-palette.png"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/open-palette.png" alt="Add new connection" width="80%"></a>

3. Under **Mediators** > **HTTP** select the **GET** operation.

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/add-get-operation.png"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/add-get-operation.png" alt="Add new connection" width="80%"></a>

4. In the **Add Get** pane that appears, click **Add new connection**.

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/add-new-connection.png"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/add-new-connection.png" alt="Add new connection" width="40%"></a>

5. Under **Add New Connection**, select **HTTPS**.

6. Specify the following values:

    | Property            | Value                   |
    |---------------------|-------------------------|
    | **Connection Name** | `HelloWorldConn`        |
    | **Base URL**        | `https://apis.wso2.com` |

7. Click **Add**. You'll be directed to the **Add Get** pane again.

8. Enter `/zvdz/mi-qsg/v1.0` as the **Relative Path**. So the actual endpoint is `https://apis.wso2.com/zvdz/mi-qsg/v1.0`.

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/add-get.png"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/add-get.png" alt="Add new connection" width="40%"></a>

9. Click **Submit**.

    Now, let's add a [Respond Mediator](https://mi.docs.wso2.com/en/latest/reference/mediators/respond-mediator/) to respond the message to the client.

10. Click on the **+** icon placed just after the HTTPS GET operation to open the palette.

11. Select **Respond** mediator under **Mediators**.

12. Click **Add**.

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/design-api.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/design-api.gif" alt="Design API" width="80%"></a>

Now you have successfully designed the integration.

!!! note
    You can view the source view by clicking on the **Show Source** (`</>`) icon located in the top right corner of the VSCode.

## Step 4 - Run the integration artifacts

Now that you have developed an integration using the MI for the Visual Studio Code plugin, it's time to deploy the integration to the MI server runtime.

Click the **Build and Run** icon located in the top right corner of VSCode.

<a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/build-and-run-project.png"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/build-and-run-project.png" alt="Build and run" width="80%"></a>

## Step 5 - Test the integration service locally

Now, let's test the integration service. For that, you can use the inbuilt try-it functionality in the MI for the VSCode extension.

When you run the integration artifact as in [Step 4](#step-4-run-the-integration-artifacts), the **Runtime Services** interface opens. You can see all the available services.

Select `HelloWorldAPI`, which you have developed, and test the resource.

<a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/test-api.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/test-api.gif" alt="Test API" width="80%"></a>
    
!!! note
    For more information, refer to [Micro Integrator Documentation](https://mi.docs.wso2.com/en/latest/).

## Step 6: Push to Devant <!-- Todo Update this if this is supported by the Ballerina Integrator extension itself -->
1. Click **Source Control** icon on the sidebar.
2. Click **+** to stage all the changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to remote.

## Step 7: Test the API
1. Once you push the changes, the overview page of the Devant integration will automatically refresh and show you the **Latest Commit** and automatically build and deploy your integration showing the **Build Status**.

    !!! note
        The build process may take some time. Once complete, the build status changes to **Success**. You can see the Build History by clicking **Build** in the left navigation.

2. Once the **Build Status** shows as `Build completed`, click **Test** in the left navigation.
3. Click **Console** on the **Test** dropdown. The console page lists all the available resources.
4. Click **Get Test Key** to get a key for testing.
5. You will have a single resource available **GET /**. Click to expand the resource.
6. Click **Try it out**.
7. Click **Execute**. You will see the response from the backend service as `{"message": "Hello World!!!"}`.
    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-integration/test-api-response.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-integration/test-api-response.gif" alt="Test API Response" width="80%"></a>  <!-- Todo Update this gif with the real one after choreo supports MI 4.4.0 -->
[//]: # (After successfully testing your service, explore other Devant features like [managing]&#40;../api-management/lifecycle-management.md&#41;, [observing]&#40;../monitoring-and-insights/observability-overview.md&#41;, and [DevOps]&#40;../devops-and-ci-cd/view-runtime-details.md&#41;.  <!-- Todo Update this with the real features -->)
