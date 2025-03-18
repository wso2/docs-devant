# Schedule Your First Automation

## Overview

In this guide, you will:

- Create a simple automation that prints `"Hello World"` every day.
- Use Ballerina Integrator to develop the automation.
- Push the automation to Devant from the Ballerina Integrator which automatically builds the automation.
- Schedule the automation to run every day.

<!-- Todo add a YouTube video tutorial for this quick start -->

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If signing in to Devant for the first time, create an organization:
    1. Go to [https://console.devant.dev/](https://console.devant.dev/) and sign in using your preferred sign-in option.
    2. Enter a unique organization name. For example, `Stark Industries`.
    3. Read and accept the privacy policy and terms of use and click **Create**.
    4. Select your region and click **Confirm**.
3. VSCode: [Install VSCode](https://code.visualstudio.com/download) if you don't have it installed already.

## Step 1: Attach a Git repository
1. Go to [https://console.devant.dev/new](https://console.devant.dev/new) and sign in. This opens the new integration page.
2. On the new integration page, click **Attach a Git Repository**.

    !!! tip
        If you're using a public Git repository, you can skip ahead to sub-step 8. Click **Use a Third-Party Public Git Repository** and enter the repository URL.

3. Click **Authorize with GitHub** to connect Devant to your GitHub account. If you haven't connected your GitHub repository to Devant, authorize the WSO2 cloud app with your GitHub account [WSO2 Cloud App](https://github.com/marketplace/choreo-apps).
4. Under the **Organization** dropdown, click **+ Add**. This redirects you to the **Install WSO2 Cloud App** page.
5. Select your GitHub account and install [WSO2 Cloud App](https://github.com/marketplace/choreo-apps)

    !!! note
        The **WSO2 Cloud App** requires:

        - Read and write access to code and pull requests.
        - Read access to issues and metadata.

        You can [revoke access](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/reviewing-your-authorized-integrations#reviewing-your-authorized-github-apps) at any time. Write access is used to push changes directly to your repository.

6. Select your organization under the **Organization** dropdown. If your organization is not listed, click the Refetch button.
7. Select a repository to save your integration.
8. Select a **Branch** and a **Path** of the selected repository to save your integration.
9. The **Name** and **Identifier** fields are automatically populated. Optionally, you can edit them to your preference.
10. Select the **Technology** as `Ballerina Integrator`.
11. Choose the **Integration Type** as `Automation` and click **Create**.

This redirects you to the overview page of the automation. Now, let's design the automation.

## Step 2: Install the Ballerina Integrator extension

1. Click **Install Ballerina Integrator extension** on the overview page. This opens the VSCode extensions page.
2. Click **Install** to install the extension. This installs both **Ballerina Integrator** and **Ballerina** extensions on VSCode.

## Step 3: Set up Ballerina Integrator for the first time
1. Click the Ballerina Integrator icon on the sidebar.

    <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi-icon.png"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi-icon.png" alt="Ballerina Integrator Icon" width="80%"></a>

2. Click **`Set Up Ballerina Integrator`**. The setup wizard installs and configures the [Ballerina](https://ballerina.io/) distribution required for the Ballerina Integrator.
3. Click **`Restart VS Code`** to complete the setup.

    <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi-setup.gif"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/bi-setup.gif" alt="Ballerina Integrator Setup" width="80%"></a>

## Step 4: Develop automation in VSCode
1. Go to the Overview page of the integration you have created and click **Develop in Ballerina Integrator**. This will clone your project and open in Ballerina Integrator.
2. In Ballerina Integrator design view, click **Add Artifact**.
3. Select **Automation** from the Constructs menu. Since **Automation** is chosen from the Devant console, other options are disabled.
4. Click **Create** to create an automation. This directs you to the automation diagram view.
5. Click **+** after the **Start** node to open the node panel.
6. Select **Call Function** and select **println**.
7. Click **+ Add Another Value**, type `"Hello World"` and click **Save**.
8. Click **Run** in the top right corner to run the automation. This compiles the automation and runs it in the embedded Ballerina runtime.

    <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/design-integration.gif"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/design-integration.gif" alt="Design Integration" width="80%"></a>

## Step 5: Push to Devant
1. Click the **Source Control** icon on the sidebar.
2. Click **+** to stage all changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to remote.

## Step 6: Schedule Automation
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

    <a href="{{base_path}}/assets/img/get-started/schedule-your-first-automation/view-logs.gif"><img src="{{base_path}}/assets/img/get-started/schedule-your-first-automation/view-logs.gif" alt="View Logs" width="80%"></a>

[//]: # (After successfully testing your service, explore other Devant features like [managing]&#40;../api-management/lifecycle-management.md&#41;, [observing]&#40;../monitoring-and-insights/observability-overview.md&#41;, and [DevOps]&#40;../devops-and-ci-cd/view-runtime-details.md&#41;.  <!-- Todo Update this with the real features -->)
