# Obtain access token

External applications could obtain a user authorized API token via the OAuth2 protocol. Before getting started, developers need to create their applications in [App Management Console](https://app.raindrop.io/#/settings/apps/dev) and configure a valid OAuth redirect URL. A registered Raindrop.io application is assigned a unique `Client ID` and `Client Secret` which are needed for the OAuth2 flow.

This procedure is comprised of several steps, which will be described below.

{% hint style="info" %}
If you just want to test your application, or do not plan to access any data except yours account you don't need to make all of those steps.

Just go to [App Management Console](https://app.raindrop.io/#/settings/apps/dev) and open your application settings. Copy **Test token** and use it as described in **Step 4.**
{% endhint %}

{% api-method method="get" host="https://raindrop.io" path="/oauth/authorize" %}
{% api-method-summary %}
Step 1: The authorization request
{% endapi-method-summary %}

{% api-method-description %}
Direct the user to our authorization URL with specified request parameters.  
— If the user is not logged in, they will be asked to log in  
— The user will be asked if he would like to grant your application access to his Raindrop.io data
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="redirect\_uri" type="string" required=true %}
Redirect URL configured in your application setting
{% endapi-method-parameter %}

{% api-method-parameter name="client\_id" type="string" required=true %}
The unique Client ID of the Raindrop.io app that you registered
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=307 %}
{% api-method-response-example-description %}
Check details in Step 2
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

![User will be asked if he would like to grant your application access to his Raindrop.io data](../../.gitbook/assets/authorize.png)

### Step 2: The redirection to your application site

When the user grants your authorization request, the user will be redirected to the redirect URL configured in your application setting. The redirect request will come with query parameter attached: `code` .

The `code` parameter contains the authorization code that you will use to exchange for an access token.

In case of error redirect request will come with `error` query parameter:

| Error | Description |
| :--- | :--- |
| access\_denied | When the user denies your authorization request |
| invalid\_application\_status | When your application exceeds the maximum token limit or when your application is being suspended due to abuse |

{% api-method method="post" host="https://raindrop.io" path="/oauth/access\_token" %}
{% api-method-summary %}
Step 3: The token exchange
{% endapi-method-summary %}

{% api-method-description %}
Once you have the authorization `code`, you can exchange it for the `access_token` by doing a `POST` request to this URL
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="code" type="string" required=true %}
Code that you received in step 2
{% endapi-method-parameter %}

{% api-method-parameter name="client\_id" type="string" required=true %}
The unique Client ID of the Raindrop.io app that you registered
{% endapi-method-parameter %}

{% api-method-parameter name="client\_secret" type="string" required=true %}
Client secret
{% endapi-method-parameter %}

{% api-method-parameter name="redirect\_uri" type="string" required=true %}
Same `redirect_uri` from step 1
{% endapi-method-parameter %}

{% api-method-parameter name="grant\_type" type="string" required=true %}
**authorization\_code**
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "access_token": "ae261404-11r4-47c0-bce3-e18a423da828",
  "refresh_token": "c8080368-fad2-4a3f-b2c9-71d3z85011vb",
  "expires": 1209599768,
  "token_type": "Bearer"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Occurs when `code` parameter is invalid
{% endapi-method-response-example-description %}

```
{"error": "bad_authorization_code"}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://raindrop.io" path="/oauth/access\_token" %}
{% api-method-summary %}
♻️ The access token refresh
{% endapi-method-summary %}

{% api-method-description %}
For security reasons access tokens \(except "test tokens"\) will **expire after two weeks**. In this case you should request the new one, by calling `POST` request with such parameters:
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="client\_id" type="string" required=true %}
The unique Client ID of your app that you registered
{% endapi-method-parameter %}

{% api-method-parameter name="client\_secret" type="string" required=true %}
Client secret of your app
{% endapi-method-parameter %}

{% api-method-parameter name="grant\_type" type="string" required=true %}
**refresh\_token**
{% endapi-method-parameter %}

{% api-method-parameter name="refresh\_token" type="string" required=true %}
Refresh token that you get in step 3
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "access_token": "ae261404-18r4-47c0-bce3-e18a423da898",
  "refresh_token": "c8080368-fad2-4a9f-b2c9-73d3z850111b",
  "expires": 1209599768,
  "token_type": "Bearer"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

