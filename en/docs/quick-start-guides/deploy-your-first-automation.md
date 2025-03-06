# Deploy Your First Automation

## Overview

In this guide, you will:

- Create a Devant project and add a simple automation which will print `"Hello World"` every minute .
- Use Ballerina Integrator (BI) to develop the automation.
- Push the automation to Devant from the BI which will automatically build the automation.
- Schedule the automation to run every minute.

<!-- Todo add a youtube video tutorial for this quick start -->

## Prerequisites

1. GitHub account: [Create a github account](https://github.com/signup) if you don't have one already.
<!-- [//]: # (Todo check the url is correct before going live) -->
2. If you're signing in to the Devant for the first time, create an organization:
    1. Go to [https://devant.dev/](https://devant.dev/) and sign in using your Google, GitHub, or Microsoft account.
    2. Enter a unique organization name. For example, `Stark Industries`.
    3. Read and accept the privacy policy and terms of use and Click **Create**.

1. VSCode: [Install VSCode](https://code.visualstudio.com/download) if you don't have it installed already.
2. Create a profile in VSCode:
    1. Open the VSCode.
    2. Navigate to **Settings**->**Profiles**.
    3. Click on **New Profile** and select **Create Profile**.
    4. Enter the profile name as `Ballerina Integrator` and click **Create**.
    5. Click on the ✔️ sign in front of the `Ballerina Integrator` profile to select the profile.


???+ info "VS Code Profile"
    To learn more about profiles, see [Visual Studio Code Profiles](https://code.visualstudio.com/docs/editor/profiles).

## Step 1: Create a project<!-- Todo check the url is correct before going live -->
1. Go to [https://devant.dev/](https://devant.dev/) and sign in. This opens the organization overview page.
2. On the organization overview page, click **+ Create Project**.
3. Enter the following details:

    !!! info
        The **Name** field must be unique and cannot be changed after creation.

    | **Field**                | **Value**                          |
    |--------------------------|------------------------------------|
    | **Project Display Name** | Hello World Project                  |
    | **Name**                 | hello-world-project                  |
    | **Project Description**  | My sample project                  |

4. Click **Create**. This creates the project and takes you to the project overview page.

<!-- Todo finalize the names and structure -->
## Step 2: Attach a Git repository
1. On the project overview page, click on **Attach a Git Repository**.
2. Go to the **GitHub** tab.
3. Click **Authorize with GitHub** to connect Devant to your GitHub account. If you haven't connected your GitHub repository to Devant, authorize WSO2 cloud app stage with your Github account [WSO2 Cloud App](https://github.com/marketplace/choreo-apps).
4. Under the **Organization**  dropdown click on **+ Add**. This will redirect you to **Install WSO2 Cloud App Stage** page.
5. Select your GitHub account and install [WSO2 Cloud App](https://github.com/marketplace/choreo-apps)

    !!! note
        The **WSO2 Cloud App** requires:
        - Read and write access to code and pull requests.
        - Read access to issues and metadata.

        You can [revoke access](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/reviewing-your-authorized-integrations#reviewing-your-authorized-github-apps) at any time. Write access is used to push changes directly to your repository.

6. Select your organization under the **Organization**  dropdown. If your your organization is still not listed click on the Refetch button.
7. Select a repository to save your automation. Additionally, you can select a **Branch** and a **Path** of the selected repository to save your automation.
9. **Name** and **Identifier** fields will be automatically populated. Additionally, you can edit them to your preference.
9. Select the **Technology** as `Ballerina`.
10. Choose the **Integration Type** as `Automation` and Click **Create**.

This will redirect you to the overview page of the automation. Now, let's design the automation.

## Step 3: Install the Ballerina Integrator extension

1. Click on **Install Ballerina Integrator extension** in the overview page. This will open the VSCode extensions page.
2. Click on **Install** to install the extension. This will install the **Ballerina Integrator** and **Ballerina** extensions on VSCode.

## Step 4: Set up Ballerina Integrator for the first time
1. Click on the Ballerina Integrator icon on the sidebar.    
   <a href="{{base_path}}/assets/img/get-started/bi_icon.png"><img src="{{base_path}}/assets/img/get-started/bi_icon.png" alt="Ballerina Integrator Icon" width="70%"></a>
2. Click on the **`Set Up Ballerina Integrator`** button. The setup wizard will install and configure the [Ballerina](https://ballerina.io/) distribution required for Ballerina Integrator.
3. Click on the **`Restart VS Code`** button to complete the setup.
   <a href="{{base_path}}/assets/img/get-started/bi_setup.gif"><img src="{{base_path}}/assets/img/get-started/bi_setup.gif" alt="BI Setup" width="70%"></a>

???+ info "Update Ballerina Integrator's Ballerina Distribution"
    The setup wizard will install the Ballerina distribution required for Ballerina Integrator in to `<USER_HOME>/.ballerina/ballerina-home` directory.
    Press `Ctrl + Shift + P` on Windows and Linux, or `shift + ⌘ + P` on a Mac and type `Ballerina: Update Ballerina Integrator` to update the installed Ballerina distribution.

## Step 5: Develop automation in VSCode
1. Click on **Develop automation in VSCode** in the automation overview page. This will open up your project on VSCode. <!-- Todo This is not working ATM update this if we are going live without this -->
2. Click on the Ballerina Integrator icon on the sidebar. <!-- Todo step 1-6 will be automatically done by the BI extension. But that is not working ATM. Remove those steps once we support that -->
3. Click on the **Create New Integration** button.
4. Enter the Integration Name as `HelloWorld`.
5. Project directory should be automatically populated. If not, select project directory by clicking on the **Select Location** button.
6. Click on the **Create Integration** button to create the integration project.
   <a href="{{base_path}}/assets/img/get-started/create_integration.gif"><img src="{{base_path}}/assets/img/get-started/create_integration.gif" alt="Create Integration" width="70%"></a>
7. In the design view, click on the **Add Construct** button.
8. Select **Automation** from the Constructs menu.
9. Click **Create** to create an automation. This will direct you to the automation diagram view.
10. Click on the **+** button after the **Start** node to open the node panel.
11. Select **Function Call** and select **println**.
12. Click on **+ Add Another Value**, type `"Hello World"` and click on **Save**.
13. Click on **Run** button at the lop right corner to run the automation. The automation will be compiled and run in the embedded Ballerina runtime.
   <a href="{{base_path}}/assets/img/get-started/design_integration.gif"><img src="{{base_path}}/assets/img/get-started/design_integration.gif" alt="Design Integration" width="70%"></a>

## Step 6: Push to Devant <!-- Todo Update this if this is supported by the BI extension itself -->
1. Click on **Source Control** icon on the sidebar.
2. Click on **+** button to stage all the changes.
3. Add a appropriate commit message and commit.
4. Click on **Sync Changes** to push the changes to remote.

## Step 7: Schedule Automation
1. Once you push the changes, the overview page of the Devant automation will automatically refresh and show you the **Latest Commit** and automatically build your automation showing the **Build Status**.

    !!! note
        The build process may take some time. You can track progress in the **Build History** pane. Once complete, the build status changes to **Success**.

2. Once the **Build Status** shows as `Build completed`, click on **Schedule** button.
3. Switch to **BY INTERVAL** tab.
4. Select **Minute** from the dropdown.
5. Add `1` to the **Repeat beginning of every** text box and click on **Update**.
1. Development card will be automatically update with the execution details. Click on the refresh button on the top right corner if it is not automatically updated.
2. Click on **View Logs** on an execution. You will see the `Hello World` is printed along with the execution time.
   <a href="{{base_path}}/assets/img/get-started/view_logs.gif"><img src="{{base_path}}/assets/img/get-started/view_logs.gif" alt="View Logs" width="70%"></a>

After successfully testing your service, explore other Devant features like [managing](../api-management/lifecycle-management.md), [observing](../monitoring-and-insights/observability-overview.md), and [DevOps](../devops-and-ci-cd/view-runtime-details.md).  <!-- Todo Update this with the real features -->
