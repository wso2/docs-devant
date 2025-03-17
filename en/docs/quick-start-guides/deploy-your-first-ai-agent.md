# Deploy Your First AI Agent

## Overview

In this guide, you will:

- Create a simple AI Agent that provides motivational quotes.
- Develop the AI Agent integration using Ballerina Integrator.
- Push the AI Agent to Devant from Ballerina Integrator, which will automatically build and deploy it into the development environment.
- Test the AI Agent by sending prompts.
- Promote it to the production environment and use it as an API.

<!-- Todo add a YouTube video tutorial for this quick start -->

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If signing in to Devant for the first time, create an organization:
    1. Go to [https://console.devant.dev/](https://console.devant.dev/) and sign in using Google, GitHub, or Microsoft account.
    2. Enter a unique organization name. For example, `Stark Industries`.
    3. Read and accept the privacy policy and terms of use and click **Create**.
3. VSCode: [Install VSCode](https://code.visualstudio.com/download) if you don't have it installed already.

<!-- Todo finalize the names and structure -->
## Step 1: Attach a Git repository
1. Go to [https://console.devant.dev/](https://console.devant.dev/) and sign in. This redirects you to the **Default** project or to the project you visited last.
2. On the project overview page, click **Attach a Git Repository**.
3. Click **Authorize with GitHub** to connect Devant to your GitHub account. If you haven't connected your GitHub repository to Devant, authorize the WSO2 cloud app stage with your GitHub account [WSO2 Cloud App](https://github.com/marketplace/choreo-apps).
4. Under the **Organization** dropdown, click **+ Add**. This redirects you to the **Install WSO2 Cloud App Stage** page.
5. Select your GitHub account and install [WSO2 Cloud App](https://github.com/marketplace/choreo-apps)

    !!! note
        The **WSO2 Cloud App** requires:
        - Read and write access to code and pull requests.
        - Read access to issues and metadata.

        You can [revoke access](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/reviewing-your-authorized-integrations#reviewing-your-authorized-github-apps) at any time. Write access is used to push changes directly to your repository.

7. Select your organization under the **Organization** dropdown. If your organization is not listed, click the Refetch button.
8. Select a repository to save your AI Agent. Optionally, you may select a **Branch** and a **Path** of the selected repository to save your AI Agent.
9. The **Name** and **Identifier** fields are automatically populated. Optionally, you can edit them to your preference.
10. Select the **Technology** as `Ballerina`.
11. Choose the **Integration Type** as `AI Agent` and click **Create**.

This redirects you to the overview page of the AI Agent. Now, let's develop the AI Agent.

## Step 2: Install the Ballerina Integrator extension

1. Click **Install Ballerina Integrator extension** on the overview page. This opens the VSCode extensions page.
2. Click **Install** to install the extension. This installs both **Ballerina Integrator** and **Ballerina** extensions on VSCode.

## Step 3: Set up Ballerina Integrator for the first time
1. Click the Ballerina Integrator icon on the sidebar.
   <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi_icon.png"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi_icon.png" alt="Ballerina Integrator Icon" width="80%"></a>
2. Click **`Set Up Ballerina Integrator`**. The setup wizard installs and configures the [Ballerina](https://ballerina.io/) distribution required for the Ballerina Integrator.
3. Click **`Restart VS Code`** to complete the setup.
   <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi-setup.gif"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi-setup.gif" alt="Ballerina Integrator Setup" width="80%"></a>

???+ info "Update Ballerina Integrator's Ballerina Distribution"
    The setup wizard installs the Ballerina distribution required for the Ballerina Integrator into the `<USER_HOME>/.ballerina/ballerina-home` directory.
    Press `Ctrl + Shift + P` on Windows and Linux, or `Shift + ⌘ + P` on a Mac and type `Ballerina: Update Ballerina Integrator` to update the installed Ballerina distribution.

## Step 4: Develop AI Agent in VSCode
1. Click **Develop in Ballerina Integrator** in the AI Agent overview page. This opens your project in VSCode. <!-- Todo This is not working ATM update this if we are going live without this -->
2. Click the Ballerina Integrator icon on the sidebar. <!-- Todo step 1-6 will be automatically done by the Ballerina Integrator extension. But that is not working ATM. Remove those steps once we support that -->
3. Click **Create New Integration** and enter the Integration Name as `MotivationAssistant`.
4. The project directory should be automatically populated. If not, select the project directory by clicking the **Select Location** button.
5. Click **Create Integration** to create the integration project.
   <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/create-integration.gif"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/create-integration.gif" alt="Create Integration" width="80%"></a>
6. In the design view, click **Add Construct**.
7. Select **AI Chat Agent** from the Constructs menu.
8. Then provide the name of the listener as `motivationAssistant` for listener configuration and click next.
9. For the service configuration, provide the service base path as `/agentChat`.  
10. Click **Create** to create the AI Agent. This directs you to the AI Agent diagram view.
11. Click **+** after the **Start** node to open the node panel.
12. Select **Function Call** and select **println**.
13. Click **+ Add Another Value**, type `"Hello World"` and click **Save**.
14. Click **Run** in the top right corner to start the AI Agent. This compiles and runs the AI Agent service in the embedded Ballerina runtime.
   <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/design-integration.gif"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/design-integration.gif" alt="Design Integration" width="80%"></a>


## Step 5: Push to Devant <!-- Todo Update this if this is supported by the Ballerina Integrator extension itself -->
1. Click the **Source Control** icon on the sidebar.
2. Click **+** to stage all changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to remote.

## Step 6: Test and Consume AI Agent
1. Once you push the changes, the overview page of the Devant AI Agent will automatically refresh and show you the **Latest Commit** and automatically builds and shows the **Build Status**.

    !!! note
        The build process may take some time. Once complete, the build status changes to **Success**. You can see the Build History by clicking **Build** in the left navigation.

2. Once the **Build Status** shows `Build completed`, it will get automatically deployed into the development card.
3. Send a prompt similar to the following to get the AI Agent response:

[//]: # (After successfully testing your service, explore other Devant features like [managing]&#40;../api-management/lifecycle-management.md&#41;, [observing]&#40;../monitoring-and-insights/observability-overview.md&#41;, and [DevOps]&#40;../devops-and-ci-cd/view-runtime-details.md&#41;.  <!-- Todo Update this with the real features -->)
