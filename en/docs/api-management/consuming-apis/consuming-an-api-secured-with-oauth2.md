# Consuming an API secured with OAuth2

This document provides guidance on how to consume an API that is secured using the OAuth2 security scheme.

## Prerequisites

Before you begin, ensure you have the following:

- An Integration as API configured with OAuth2 security in Devant. Refer to the [API Security](../../api-security/) documentation for details on setting up OAuth2 security for your API.
- The Integration as API is promoted to the Production environment.

## Steps to Consume an OAuth2 Secured API

1. Sign in to [Devant](https://console.devant.dev).
2. Select your project and navigate to the **Overview** page in the left navigation.
3. Select the Integration as API that you want to consume.
4. In the Integration **Overview** page, on the right side, click **Developer Portal**. This will open the Developer Portal for the selected API.
5. In the Developer Portal, click **Subscribe** to subscribe the API to an application.
6. If you already have an application, select it from the list. If not, enter a name for a new application and click **Create Application**.
7. Once the application is created, click **Subscribe** to complete the subscription process.
8. In the left navigation menu, click **Applications** and select your application.
9. Under the **OAuth2** section of the application details card, click **Generate Key**.
10. A dialog box showing the credentials will appear, which you can close after noting down the necessary details.
11. You can modify the **Advanced Configuration** in the same **OAuth2** section if needed.
12. To test the API, click **Generate** under **Token:** subsection. This will generate an access token using the OAuth2 client credentials flow.

    <div style="width: 80%;">
    ![Consuming API with OAuth2]({{base_path}}/assets/img/api-management/oauth2-consumption.gif)
    </div>

Once you have the access token, you can use it to make authenticated requests to the secured API. Include the token in the `Authorization` header of your HTTP requests as follows:

```
Authorization: Bearer <access_token>
```

An example using `curl` to make a request to the secured API:

```bash
curl --request GET \
  --url <endpoint> \
  --header 'Accept: text/plain' \
  --header 'Authorization: Bearer <access_token>'
```

You can also click **Documentation** in the **API Overview** page to view the API documentation, and test the API endpoints directly from the Developer Portal using the generated access token.