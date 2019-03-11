# Authentication

> Example Request

```shell
curl -X POST \
  https://test.forio.com/v3/epicenter/manager/authentication \
  --header 'Content-Type: application/json' \
  --data '{
  "handle": "john_doe@forio.com",
  "password": "<your account password>",
  "objectType": "user"
}'
```

> Example Response

```json
{
  "session": "eyJ0eXAiOiJKV1QiLA0K.....",
  "timestamp": "2019-03-10T18:28:51.389Z",
  "expires": true,
  "timeoutMinutes": 240,
  "possibleTeamAccountShortNames": [
      "lakers",
      "warriors"
  ],
  "personalAccountShortName": "john_doe",
  "userKey": "000000000000000000000000000000000000",
  "userHandle": "john_doe@forio.com",
  "objectType": "user"
}
```

Authentication to the Epicenter API is done by making a request to the authentication endpoint and providing a valid authentication token (a JSON object) as part of the request body. Once authenticated, you'll be granted with a session-specific access token that you can then use to call any of our other APIs successfully.

Our API provides five types of access tokens:

* __User access tokens__ are specific to an Epicenter author, team member, or end user. API calls using this kind of token have access to all of the data that the user has access to.

* __Player access tokens__

* __Project access tokens__ are created with the Public and Secret API keys for the project. API calls using this kind of token have access to all of the data in the project.

* __Admin access tokens__

* __Anonymous access tokens__
<br>

To authenticate, provide these settings as part of your request:

**HTTP Request**<br>
`POST /v3/epicenter/manager/authentication`

**Headers**<br>
Set `Content-Type` to `application/json`

**Example request body**<br>
`
{
  "handle": "john_doe@forio.com",
  "password": "<your account password>",
  "objectType": "user"
}
`

A successful request returns a polymorphic JSON object based on the type of authentication token you've provided.

As an example, displayed at the right is how to create a user access token. It shows the parameters you need to include in your request body and the expected response object to be returned.

The following sections below show the various methods of creating the five types of access tokens:

  * Creating a user access token
  * Creating a player access token
  * Creating a project access token
  * Creating an anonymous access token
  * Creating an admin access token

<aside class="notice">
These various methods use the same request method and authentication endpoint as described previously. They differ only on the JSON payload you include on your request body.
</aside>
