# Consuming an API secured with an API Key

This document provides guidance on how to consume an API that is secured using the API Key security scheme.

## Prerequisites

Before you begin, ensure you have the following:

- An Integration as API configured with API Key security in Devant. Refer to the [API Security](../../api-security/) documentation for details on setting up API Key security for your API.
- The Integration as API is promoted to the Production environment.

## Steps to Consume an API secured with API Key

1. Sign in to [Devant](https://console.devant.dev).
2. Select your project and navigate to the **Overview** page in the left navigation.
3. Select the Integration as API that you want to consume.
4. In the Integration **Overview** page, on the right side, click **Developer Portal**. This will open the Developer Portal for the selected API.
5. In the Developer Portal, click **Subscribe** to subscribe the API to an application.
6. If you already have an application, select it from the list. If not, enter a name for a new application and click **Create Application**.
7. Once the application is created, click **Subscribe** to complete the subscription process.
8. In the left navigation menu, click **Applications** and select your application.
9. The Integration as API will appear in the **Subscribed API Proxies** table. 
10. Click **Generate Key** under **API Key** column to generate an API Key.
11. A dialog box with the credentials will appear, which you can close after noting down the necessary details.

    <div style="width: 80%;">
    ![Consuming API with API Key](../../assets/img/api-management/api-key-consumption.gif)
    </div>

Once you have the API Key, you can use it to make authenticated requests to the secured API. Include the key in the `api-key` header of your HTTP requests as follows:

```
api-key: <api_key>
```

An example using `curl` to make a request to the secured API:

```bash
curl --request GET \
  --url <endpoint> \
  --header 'Accept: text/plain' \
  --header 'api-key: <api_key>'
```

You can also click **Documentation** in the **API Overview** page to view the API documentation, and test the API endpoints directly from the Developer Portal using the generated API Key.