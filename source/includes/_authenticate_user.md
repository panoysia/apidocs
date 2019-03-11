<h2 id="create-user-token">Creating a user access token</h2>

> Example Request

```shell
curl -X POST \
  https://test.forio.com/v3/epicenter/manager/authentication \
  -H 'Content-Type: application/json' \
  -d '{
  "handle": "john_doe@forio.com",
  "password": "<your account password>",
  "objectType": "user",
  "teamAccountShortName": "lakers"
}'
```

> Example Response

```json
{
    "session": "eyJ0eXAiOiJKV1QiLA0K.....",
    "timestamp": "2019-03-10T19:21:33.721Z",
    "expires": true,
    "timeoutMinutes": 240,
    "teamAccountRole": "AUTHOR",
    "personalAccountShortName": "john_doe",
    "teamAccountShortName": "lakers",
    "userKey": "000000000000000000000000000000000000",
    "userHandle": "john_doe@forio.com",
    "objectType": "user"
}
```

### Request Body Parameters

### *Required* parameters
| Name /*type* | Description /*example* |
|:----------|:------------|
|handle<br>*string*|Your account's email.|
|password<br>*string*|You account's password.|
|objectType<br>*const*|The string value `"user"`.|

### *Optional* parameters
| Name /*type* | Description /*example* |
|:----------|:------------|
|teamAccountShortName<br>*string*|The short name of a ‘team’ account, i.e. a paying licensed account which may have more than one author (team member).<br><br>If you don't include this in your request, then all teams under the user are shown in the `possibleTeamAccountShortNames` attribute as part of the response.|


### Returns

Returns a [UserWhoAmI](#userwhoami) object.


<h3 id="userwhoami">The UserWhoAmI object</h3>

| Name /*type* | Description /*example* |
|:----------|:------------|
|userHandle<br>*string*|The user’s chosen login name. It's usually your account's email.|
|personalAccountShortName<br>*string*|The short name of a ‘personal’ account, i.e., a free account with limitation provided to each person who signs up for Epicenter.|
|expires<br>*boolean*|`true` if the token/session has an expiry. Otherwise, `false`.|
|session<br>*string*|The generated specific access token.|
|teamAccountRole<br>*enum*|The ‘role’ of an author on an account, which is either `"AUTHOR"` (a full team member) or `"SUPPORT"` (someone with lesser privileges in a customer support role).|
|possibleTeamAccountShortNames<br>*array (string)*|A list of account `shortNames` to which the user has rights (has roles for). Another authorization request should be sent with one of these accounts chosen.|
|teamAccountShortName<br>*string*|The short name of a `team` account, i.e. a paying licensed account which may have more than one author (team member).|
|timeoutMinutes<br>*number*|The number of minutes until the token expires.|
|userKey<br>*string*|The 36 character unique identifier for a user.|
|timestamp<br>*string (DateTime)*|The time that the request was made.|
|objectType<br>*const*|`"user"`|
