# Manage Configurations and Secrets

Devant allows you to easily manage and version your component's configurations and secrets as **file mounts** or **environment variables**.

!!! info "Note"
    All configurations and secrets are stored in an encrypted secret vault in the cloud data plane managed by WSO2.
    For private data planes, configurations and secrets are stored in your cloud environment's attached secret manager.

## The difference between configurations and secrets

Devant treats all configurations and secrets as sensitive content, but lets you choose between a secret or a configuration when creating environment variables or file mounts.

- **Secrets** are write-only. Once created, you cannot view or retrieve their content via Devant, but you can overwrite them at any time.
- **Configurations** can be read and updated via Devant after creation.

    !!!info "Note"
        For sensitive data such as database passwords, cloud credentials, or service accounts, it is recommended to use secrets rather than configurations.

## Managing environment variables and file mounts on Devant

### Navigating to the Configs & Secrets page

1. Sign in to [Devant](https://console.devant.dev/).
2. Navigate to your project, and select your integration.
3. Under **Admin**, select the **Configs & Secrets** page in the left navigation menu.
4. Make sure you are on the correct **Deployment Track** and the **Environment** for which you want to manage configurations and secrets.

    <div style="width: 80%;">
    ![Navigate to Configurations & Secrets Page](../../assets/img/devops-and-ci-cd/manage-configurations-and-secrets/page-navigation.png)
    </div>

### Add an environment variable to your container

To add environment variables:

1. Navigate to the [**Configs & Secrets**](#navigating-to-the-configs-secrets-page) page.
2. Click **+ Create**.
3. Select **Environment Variables** in the **Create a Config or Secret** pane.
4. Select **Mark as a Secret** if the values contain sensitive information.

    !!!info "Note"
        Secret environment variables cannot be read after creation, but you can overwrite them at any time.

5. Enter a **Display Name** to identify this configuration.

    !!!tip
        The display name is for identification only and doesn't affect the actual environment variables.

6. Enter your environment variables as key-value pairs, then click **Add**. You can add multiple variables this way.

    !!!tip
        You can optionally import environment variables from a `.env` file by clicking **Import from .env file**.

7. Click **Create**.

### Add a file mount to your container

To add a file mount to your component:

1. Navigate to the [**Configs & Secrets**](#navigating-to-the-configs-secrets-page) page.
2. Click **+ Create**.
3. Select **File Mount** in the **Create a Config or Secret** pane.
4. Select **Mark as a Secret** if the file contains sensitive information.

    !!! info "Note"
        Secret file mounts cannot be viewed or read after creation.

5. Enter a **Display Name** to identify this file mount.
  
    !!! tip
        The display name is for identification only and doesn't affect the file mount or its content.

6. Specify the **File Mount Path** where the file should be mounted inside the container. Use an absolute path including filename and extension.
  
    !!! tip
        The mount path filename doesn't need to match your configuration name or uploaded filename.

7. Either upload a configuration file by clicking **Upload File** or paste content directly into the editor.
8. Click **Create**.

    !!! info "Note"
        Configurations and secrets apply immediately. The running replicas of your container will undergo a rolling restart to apply the changes.

### Update an existing configuration or secret

To update a configuration or secret:

1. Navigate to the [**Configs & Secrets**](#navigating-to-the-configs-secrets-page) page.
2. Click the edit icon next to the configuration or secret you want to update.
3. Make your changes and click **Save**.

### Delete an existing configuration or a secret

To delete a configuration or secret:

1. Navigate to the [**Configs & Secrets**](#navigating-to-the-configs-secrets-page) page.
2. Click the delete icon next to the configuration or secret you want to delete.
3. Type the name to confirm deletion.
4. Click **Delete**.

## Managing Ballerina configurables

Devant manages [Ballerina configurables](https://ballerina.io/learn/by-example/configurable-variables/) for your Ballerina integrations.

You can modify Ballerina configurables via the **Integration Overview** page when deploying or promoting a Ballerina integration by clicking the **Configure** button in the relevant environment card. If it is the initial build, you will see a **Configure to Continue** button to perform the same action.