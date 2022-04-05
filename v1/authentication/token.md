# Obtain access token

External applications could obtain a user authorized API token via the OAuth2 protocol. Before getting started, developers need to create their applications in [App Management Console](https://app.raindrop.io/settings/integrations) and configure a valid OAuth redirect URL. A registered Raindrop.io application is assigned a unique `Client ID` and `Client Secret` which are needed for the OAuth2 flow.

This procedure is comprised of several steps, which will be described below.

{% hint style="info" %}
If you just want to test your application, or do not plan to access any data except yours account you don't need to make all of those steps.

Just go to [App Management Console](https://app.raindrop.io/settings/integrations) and open your application settings. Copy **Test token** and use it as described in [**Make authorized calls**](calls.md)**.**
{% endhint %}

{% swagger baseUrl="https://raindrop.io" path="/oauth/authorize" method="get" summary="Step 1: The authorization request" %}
{% swagger-description %}
Direct the user to our authorization URL with specified request parameters.

\


— If the user is not logged in, they will be asked to log in

\


— The user will be asked if he would like to grant your application access to his Raindrop.io data
{% endswagger-description %}

{% swagger-parameter in="query" name="redirect_uri" type="string" %}
Redirect URL configured in your application setting
{% endswagger-parameter %}

{% swagger-parameter in="query" name="client_id" type="string" %}
The unique Client ID of the Raindrop.io app that you registered
{% endswagger-parameter %}

{% swagger-response status="307" description="Check details in Step 2" %}
```
```
{% endswagger-response %}
{% endswagger %}

![User will be asked if he would like to grant your application access to his Raindrop.io data](../../.gitbook/assets/authorize.png)

Here example CURL request:

```bash
curl "https://api.raindrop.io/v1/oauth/authorize?client_id=5e1c382cf6f48c0211359083&redirect_uri=https:%2F%2Foauthdebugger.com%2Fdebug"
```

## Step 2: The redirection to your application site

When the user grants your authorization request, the user will be redirected to the redirect URL configured in your application setting. The redirect request will come with query parameter attached: `code` .

The `code` parameter contains the authorization code that you will use to exchange for an access token.

In case of error redirect request will come with `error` query parameter:

| Error                        | Description                                                                                                    |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------- |
| access\_denied               | When the user denies your authorization request                                                                |
| invalid\_application\_status | When your application exceeds the maximum token limit or when your application is being suspended due to abuse |

{% swagger baseUrl="https://raindrop.io" path="/oauth/access_token" method="post" summary="Step 3: The token exchange" %}
{% swagger-description %}
Once you have the authorization 

`code`

, you can exchange it for the 

`access_token`

 by doing a 

`POST`

 request with all required body parameters as JSON:
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="body" name="grant_type" type="string" %}
**authorization_code**
{% endswagger-parameter %}

{% swagger-parameter in="body" name="code" type="string" %}
Code that you received in step 2
{% endswagger-parameter %}

{% swagger-parameter in="body" name="client_id" type="string" %}
The unique Client ID of the Raindrop.io app that you registered
{% endswagger-parameter %}

{% swagger-parameter in="body" name="client_secret" type="string" %}
Client secret
{% endswagger-parameter %}

{% swagger-parameter in="body" name="redirect_uri" type="string" %}
Same 

`redirect_uri`

 from step 1
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
  "access_token": "ae261404-11r4-47c0-bce3-e18a423da828",
  "refresh_token": "c8080368-fad2-4a3f-b2c9-71d3z85011vb",
  "expires": 1209599768, //in miliseconds, deprecated
  "expires_in": 1209599, //in seconds, use this instead!!!
  "token_type": "Bearer"
}
```
{% endswagger-response %}

{% swagger-response status="400" description="Occurs when code parameter is invalid" %}
```javascript
{"error": "bad_authorization_code"}
```
{% endswagger-response %}
{% endswagger %}

Here an example CURL request:

```bash
curl -X "POST" "https://raindrop.io/oauth/access_token" \
     -H 'Content-Type: application/json' \
     -d $'{
  "code": "c8983220-1cca-4626-a19d-801a6aae003c",
  "client_id": "5e1c589cf6f48c0211311383",
  "redirect_uri": "https://oauthdebugger.com/debug",
  "client_secret": "c3363988-9d27-4bc6-a0ae-d126ce78dc09",
  "grant_type": "authorization_code"
}'
```

{% swagger baseUrl="https://raindrop.io" path="/oauth/access_token" method="post" summary="♻️ The access token refresh" %}
{% swagger-description %}
For security reasons access tokens (except "test tokens") will 

**expire after two weeks**

. In this case you should request the new one, by calling 

`POST`

 request with body parameters (JSON):
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="body" name="client_id" type="string" %}
The unique Client ID of your app that you registered
{% endswagger-parameter %}

{% swagger-parameter in="body" name="client_secret" type="string" %}
Client secret of your app
{% endswagger-parameter %}

{% swagger-parameter in="body" name="grant_type" type="string" %}
**refresh_token**
{% endswagger-parameter %}

{% swagger-parameter in="body" name="refresh_token" type="string" %}
Refresh token that you get in step 3
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
  "access_token": "ae261404-18r4-47c0-bce3-e18a423da898",
  "refresh_token": "c8080368-fad2-4a9f-b2c9-73d3z850111b",
  "expires": 1209599768, //in miliseconds, deprecated
  "expires_in": 1209599, //in seconds, use this instead!!!
  "token_type": "Bearer"
}
```
{% endswagger-response %}
{% endswagger %}
