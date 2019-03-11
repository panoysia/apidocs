## Creating a project access token

> Example Request

```shell
curl -X POST \
  https://test.forio.com/v3/epicenter/manager/authentication \
  -H 'Content-Type: application/json' \
  -d '{
  "secretKey": "<your project's secret key>",
  "projectKey": "<your project's public key>",
  "objectType": "project"
}'
```

> Example Response

```json
{
    "session": "eyJ0eXAiOiJKV1QiLA0K.....",
    "timestamp": "2019-03-10T22:54:02.314Z",
    "expires": false,
    "timeoutMinutes": 240,
    "accountShortName": "lakers",
    "objectType": "project"
}
```


### Request Body Parameters

### *Required* parameters
| Name /*type* | Description /*example* |
|:----------|:------------|
|projectKey<br>*string*|The public key of a project. It's a part of the pair of API keys generated for each project.|
|secretKey<br>*string*|The secret key of a project. It's the matching pair of API keys generated for each project, and is needed together with the public key to generate an access token.|
|objectType<br>*const*|The string value `"project"`.|


### Returns

Returns a [ProjectWhoAmI](#projectwhoami) object.


<h3 id="projectwhoami">The ProjectWhoAmI object</h3>

| Name /*type* | Description /*example* |
|:----------|:------------|
|expires<br>*boolean*|`true` if the token/session has an expiry. Otherwise, `false`.|
|accountShortName<br>*string*|The team under which the project belongs.|
|session<br>*string*|The generated specific access token.|
|timeoutMinutes<br>*number*|The number of minutes until the token expires.|
|timestamp<br>*string (datetime)*|The time that the request was made.|
|objectType<br>*const*|`"project"`|
