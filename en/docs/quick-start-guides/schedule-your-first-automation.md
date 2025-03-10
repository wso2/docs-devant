# Schedule Your First Automation

## Overview

In this guide, you will:

- Create a simple automation that will print `"Hello World"` every Day.
- Use Ballerina Integrator to develop the automation.
- Push the automation to Devant from the Ballerina Integrator which will automatically build the automation.
- Schedule the automation to run every Day.

<!-- Todo add a YouTube video tutorial for this quick start -->

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If you're signing in to the Devant for the first time, create an organization:
    1. Go to [https://console.devant.dev/](https://console.devant.dev/) and sign in using your Google, GitHub, or Microsoft account.
    2. Enter a unique organization name. For example, `Stark Industries`.
    3. Read and accept the privacy policy and terms of use and Click **Create**.
3. VSCode: [Install VSCode](https://code.visualstudio.com/download) if you don't have it installed already.

<!-- Todo finalize the names and structure -->
## Step 1: Attach a Git repository
1. Go to [https://console.devant.dev/](https://console.devant.dev/) and sign in. This opens the organization overview page and lists the projects.
2. Select the **Default** project.
3. On the project overview page, click **Attach a Git Repository**.
4. Click **Authorize with GitHub** to connect Devant to your GitHub account. If you haven't connected your GitHub repository to Devant, authorize the WSO2 cloud app stage with your GitHub account [WSO2 Cloud App](https://github.com/marketplace/choreo-apps).
5. Under the **Organization**  dropdown click **+ Add**. This will redirect you to **Install WSO2 Cloud App Stage** page.
6. Select your GitHub account and install [WSO2 Cloud App](https://github.com/marketplace/choreo-apps)

    !!! note
        The **WSO2 Cloud App** requires:
        - Read and write access to code and pull requests.
        - Read access to issues and metadata.

        You can [revoke access](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/reviewing-your-authorized-integrations#reviewing-your-authorized-github-apps) at any time. Write access is used to push changes directly to your repository.

7. Select your organization under the **Organization**  dropdown. If your organization is still not listed click the Refetch button.
8. Select a repository to save your automation. Additionally, you can select a **Branch** and a **Path** of the selected repository to save your automation.
9. **Name** and **Identifier** fields will be automatically populated. Additionally, you can edit them to your preference.
10. Select the **Technology** as `Ballerina`.
11. Choose the **Integration Type** as `Automation` and Click **Create**.

This will redirect you to the overview page of the automation. Now, let's design the automation.

## Step 3: Install the Ballerina Integrator extension

1. Click **Install Ballerina Integrator extension** on the overview page. This will open the VSCode extensions page.
2. Click **Install** to install the extension. This will install the **Ballerina Integrator** and **Ballerina** extensions on VSCode.

## Step 4: Set up Ballerina Integrator for the first time
1. Click the Ballerina Integrator icon on the sidebar.    
   <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi_icon.png"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi_icon.png" alt="Ballerina Integrator Icon" width="80%"></a>
2. Click **`Set Up Ballerina Integrator`**. The setup wizard will install and configure the [Ballerina](https://ballerina.io/) distribution required for the Ballerina Integrator.
3. Click **`Restart VS Code`** to complete the setup.
   <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi-setup.gif"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi-setup.gif" alt="Ballerina Integrator Setup" width="80%"></a>

???+ info "Update Ballerina Integrator's Ballerina Distribution"
    The setup wizard will install the Ballerina distribution required for the Ballerina Integrator into `<USER_HOME>/.ballerina/ballerina-home` directory.
    Press `Ctrl + Shift + P` on Windows and Linux, or `shift + ⌘ + P` on a Mac and type `Ballerina: Update Ballerina Integrator` to update the installed Ballerina distribution.

## Step 5: Develop automation in VSCode
1. Click **Develop automation in VSCode** in the automation overview page. This will open up your project on VSCode. <!-- Todo This is not working ATM update this if we are going live without this -->
2. Click the Ballerina Integrator icon on the sidebar. <!-- Todo step 1-6 will be automatically done by the Ballerina Integrator extension. But that is not working ATM. Remove those steps once we support that -->
3. Click **Create New Integration** and Enter the Integration Name as `HelloWorld`.
4. The project directory should be automatically populated. If not, select the project directory by clicking on the **Select Location** button.
5. Click **Create Integration** to create the integration project.
   <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/create-integration.gif"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/create-integration.gif" alt="Create Integration" width="80%"></a>
6. In the design view, click **Add Construct**.
7. Select **Automation** from the Constructs menu.
8. Click **Create** to create an automation. This will direct you to the automation diagram view.
9. Click **+** after the **Start** node to open the node panel.
10. Select **Function Call** and select **println**.
11. Click **+ Add Another Value**, type `"Hello World"` and click **Save**.
12. Click **Run** in the top right corner to run the automation. The automation will be compiled and run in the embedded Ballerina runtime.
   <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/design-integration.gif"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/design-integration.gif" alt="Design Integration" width="80%"></a>

## Step 6: Push to Devant <!-- Todo Update this if this is supported by the Ballerina Integrator extension itself -->
1. Click **Source Control** icon on the sidebar.
2. Click **+** to stage all the changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to remote.

## Step 7: Schedule Automation
1. Once you push the changes, the overview page of the Devant automation will automatically refresh and show you the **Latest Commit** and automatically build your automation showing the **Build Status**.

    !!! note
        The build process may take some time. Once complete, the build status changes to **Success**. You can see the Build History by clicking **Build** in the left navigation.

2. Once the **Build Status** shows as `Build completed`, click **Test** to run your automation once.
3. The development card will be automatically updated with the execution details. Click the refresh button in the top right corner if it is not automatically updated.
4. Click **View Logs** on an execution. You will see the `Hello World` is printed along with the execution time.
5. Click **Schedule** to schedule the automation.
6. In the **BY INTERVAL** tab, Select **Day** from the dropdown.
7. Add `1` to the **Repeat every** text box.
8. Add `01:00 AM` to the **At** text box and click **Update**.
9. Your automation will run every Day at 01:00 AM. You can see the next execution time as **Next run in** in the Development card.
   <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/view-logs.gif"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/view-logs.gif" alt="View Logs" width="80%"></a>

[//]: # (After successfully testing your service, explore other Devant features like [managing]&#40;../api-management/lifecycle-management.md&#41;, [observing]&#40;../monitoring-and-insights/observability-overview.md&#41;, and [DevOps]&#40;../devops-and-ci-cd/view-runtime-details.md&#41;.  <!-- Todo Update this with the real features -->)
