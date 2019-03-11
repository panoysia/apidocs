<h2 id="create-player-token">Creating a player access token</h2>

> Example Request

```shell
curl -X POST \
  https://test.forio.com/v3/epicenter/manager/authentication \
  -H 'Content-Type: application/json' \
  -d '{
  "handle": "janedoe2",
  "password": "janedoe2",
  "accountShortName": "bucks",
  "objectType": "player"
}'
```

> Example Response

```json
{
    "session": "eyJ0eXAiOiJKV1QiLA0K.....",
    "timestamp": "2019-03-11T07:14:26.728Z",
    "expires": true,
    "timeoutMinutes": 240,
    "groupRole": "FACILITATOR",
    "assignedWorldKeys": [],
    "assignedWorldRoles": [],
    "playerKey": "000001695b47f0062c8286372ac03aa98794",
    "playerHandle": "janedoe2",
    "pseudonymKey": "000001695b47f0062c8286372ac03aa98794",
    "pseudonymHandle": "janedoe2",
    "accountShortName": "bucks",
    "projectShortName": "cleanup",
    "groupName": "starting-five",
    "groupKey": "000001695b47f0062c8286372ac03aa9871e",
    "objectType": "player"
}
```


### Request Body Parameters

### *Required* parameters
| Name /*type* | Description /*example* |
|:----------|:------------|
|handle<br>*string*|The end user's/player's username.|
|password<br>*string*|The player's password.|
|accountShortName<br>*string*|The team under which the player belongs.|
|objectType<br>*const*|The string value `"player"`.|

### *Optional* parameters
| Name /*type* | Description /*example* |
|:----------|:------------|
|modality<br>*enum*|A value of either `["NONE", "HBP", "ICC"]`|
|groupKey<br>*string*|The 36 character unique identifier for a group.|


### Returns

Returns a [PlayerWhoAmI](#playerwhoami) object.


<h3 id="playerwhoami">The PlayerWhoAmI object</h3>

| Name /*type* | Description /*example* |
|:----------|:------------|
|projectShortName<br>*string*|The short name of the project the player belongs.|
|possibleGroupKeys<br>*array (string)*|A list of `groupKeys` to which a player has rights (has roles for). Another authorization request should be sent with one of these groups chosen.|
|expires<br>*boolean*|`true` if the token/session has an expiry. Otherwise, `false`.|
|accountShortName<br>*string*|The short name of the team the player belongs.|
|assignedWorldKeys<br>*array (string)*|A list of worldKeys (36 character unique identifier for a world) to which a user is assigned in their chosen group (normally only one, but could be more).|
|session<br>*string*|The generated specific access token.|
|playerHandle<br>*string*|The player’s chosen login name.|
|assignedWorldRoles<br>*array (string)*|A list of roles the user has for the simulation instance in each world. This should be the same length of list as the assigned `worldKeys` and is a one to one mapping, i.e., for each world key in the assigned world key list, there will be an entry which is the user’s role in that world. Unlike the other roles (`accountRole` and `groupRole`) the world role provides no permissions, has no meaning in the Epicenter APIs, and can be different for every simulation.|
|timeoutMinutes<br>*number*|The number of minutes until the token expires.|
|groupKey<br>*string*|The 36 character unique identifier for a group.|
|groupRole<br>*enum*|The ‘role’ of a player in the classroom group, which can be one of `"FACILITATOR"` (the instructor for the class) or `"PARTICIPANT"` (a player of a simulation).|
|objectType<br>*const*|`"player"`|
|groupName<br>*string*|The name of a group (a descriptive name with no spaces, no punctuation, all lower case).|
|playerKey<br>*string*|The 36 character unique ID of a player.|
|pseudonymKey<br>*string*|The 36 character unique ID of a player’s pseudonym (a pseudonymizing entity for GDPR compliance, it’s the player’s pseudonym which links them to all their data).|
|pseudonymHandle<br>*string*|The player’s chosen online display name, so we can provide an identity for each player who is not connected to their real personally identifying information (for GDPR compliance).|
|timestamp<br>*string (DateTime)*|The time that the request was made.|

