## Creating an anonymous access token

> Example Request

```shell
curl -X POST \
  https://test.forio.com/v3/epicenter/manager/authentication \
  -H 'Content-Type: application/json' \
  -d '{
  "anonymous_key": "even a blank string works!",
  "objectType": "anonymous"
}'
```

> Example Response

```json
{
    "session": "eyJ0eXAiOiJKV1QiLA0K.....",
    "timestamp": "2019-03-11T17:06:57.419Z",
    "expires": true,
    "timeoutMinutes": 240,
    "objectType": "anonymous"
}
```


### Request Body Parameters

### *Required* parameters
| Name /*type* | Description /*example* |
|:----------|:------------|
|anonymous_key<br>*string*|Any string value is acceptable. Even an empty string is allowed.|
|objectType<br>*const*|The string value `"anonymous"`.|


### Returns

Returns a [AnonymousWhoAmI](#anonymouswhoami) object.


<h3 id="anonymouswhoami">The AnonymousWhoAmI object</h3>

| Name /*type* | Description /*example* |
|:----------|:------------|
|expires<br>*boolean*|`true` if the token/session has an expiry. Otherwise, `false`.|
|session<br>*string*|The generated specific access token.|
|timeoutMinutes<br>*number*|The number of minutes until the token expires.|
|timestamp<br>*string (datetime)*|The time that the request was made.|
|objectType<br>*const*|`"anonymous"`|
