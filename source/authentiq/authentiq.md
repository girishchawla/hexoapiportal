---
title: Authentiq Connect v1.0
language_tabs:
  - shell
  - http
  - html
  - javascript
  - python
  - ruby
  - java
toc_footers:
  - '<a href="https://developers.authentiq.com/">Authentiq Developer Docs</a>'
includes: []
search: true
highlight_theme: darkula
---

# Authentiq Connect v1.0

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Authentiq Connect OAuth 2.0 and OpenID Connect API reference.
Learn about [Authentiq ID](https://www.authentiq.com/) or check out the [Authentiq Connect](https://developers.authentiq.com) developer documentation.

Base URLs:

* <a href="https://connect.authentiq.io/">https://connect.authentiq.io/</a>


<a href="https://www.authentiq.com/tos/">Terms of service</a>
Email: <a href="mailto:hello@authentiq.com">Team Authentiq</a> Web: <a href="https://www.authentiq.com/">Team Authentiq</a> 

# Authentication


* API Key
    - Parameter Name: **Authorization**, in: header. Client management via registration token.





- oAuth2 authentication. Session management by confidential clients.

    - Flow: password

    - Token URL = [https://connect.authentiq.io/token](https://connect.authentiq.io/token)

|Scope|Scope Description|
|---|---|
|clients|Enable client management|





- oAuth2 authentication. End-user authentication.

    - Flow: authorizationCode
    - Authorization URL = [https://connect.authentiq.io/authorize](https://connect.authentiq.io/authorize)
    - Token URL = [https://connect.authentiq.io/token](https://connect.authentiq.io/token)

|Scope|Scope Description|
|---|---|
|address|The user's postal address|
|aq:location|The user's current location|
|aq:name|The user's full name|
|aq:push|Enable *One click sign-in*|
|email|The user's email address|
|oidc|Enable OIDC flow|
|phone|The user's phone number|





- oAuth2 authentication. End-user authentication.

    - Flow: implicit
    - Authorization URL = [https://connect.authentiq.io/authorize](https://connect.authentiq.io/authorize)

|Scope|Scope Description|
|---|---|
|address|The user's postal address|
|aq:location|The user's current location|
|aq:name|The user's full name|
|aq:push|Enable *One click sign-in*|
|email|The user's email address|
|oidc|Enable OIDC flow|
|phone|The user's phone number|





- oAuth2 authentication. Session management by Authentiq ID.

    - Flow: clientCredentials

    - Token URL = [https://connect.authentiq.io/token](https://connect.authentiq.io/token)

|Scope|Scope Description|
|---|---|
|session|Enable session management|




# Authentication

## authorize

> Code samples

```shell
# You can also use wget
curl -X GET https://connect.authentiq.io//authorize?client_id=string&response_type=string&scope=string&redirect_uri=string&state=string

```

```http
GET https://connect.authentiq.io//authorize?client_id=string&response_type=string&scope=string&redirect_uri=string&state=string HTTP/1.1
Host: connect.authentiq.io


```

```javascript

$.ajax({
  url: 'https://connect.authentiq.io//authorize',
  method: 'get',
  data: '?client_id=string&response_type=string&scope=string&redirect_uri=string&state=string',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```python
import requests

r = requests.get('https://connect.authentiq.io//authorize', params={
  'client_id': 'string',  'response_type': 'string',  'scope': 'string',  'redirect_uri': 'string',  'state': 'string'
)

print r.json()
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.get 'https://connect.authentiq.io//authorize',
  params: {
  'client_id' => 'string',
'response_type' => 'string',
'scope' => 'string',
'redirect_uri' => 'string',
'state' => 'string'
}

p JSON.parse(result)
```

```java
URL obj = new URL("https://connect.authentiq.io//authorize?client_id=string&response_type=string&scope=string&redirect_uri=string&state=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /authorize`

*Authenticate a user*

Start a session with Authentiq Connect and authenticate a user.

Example:

```
GET https://connect.authentiq.io/authorize?client_id=<your-client-id>&response_type=code+id_token&scope=openid+email&redirect_uri=<your-redirect-uri>&state=0123456789
```

This endpoint is compatible with OpenID Connect and also supports the POST method, in which case the parameters are passed as a form post.

See also:
  - [OAuth 2.0 Authorization Endpoint](http://tools.ietf.org/html/rfc6749#section-3.1)
  - [OIDC Authentication request](http://openid.net/specs/openid-connect-core-1_0.html#AuthRequest)
  - [OIDC Successful Authentication response](http://openid.net/specs/openid-connect-core-1_0.html#AuthResponse)
  - [OIDC Error Authentication response](http://openid.net/specs/openid-connect-core-1_0.html#AuthError)

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
client_id|query|string|true|A client ID obtained from the [Dashboard](https://dashboard.authentiq.com/).
response_type|query|string|true|The OIDC response type to use for this authentication flow. Valid choices are `code`, `id_token`, `token`, `token id_token`, `code id_token` `code token` and `code token id_token`, but a client can be configured with a more restricted set.
scope|query|string|true|The space-separated identity claims to request from the end-user. Always include `openid` as a scope for compatibility with OIDC.
redirect_uri|query|string|true|The location to redirect to after (un)successful authentication. See OIDC for the parameters passed in the query string (`response_mode=query`) or as fragments (`response_mode=fragment`). Unless the client is in test-mode this must be one of the registered redirect URLs.
state|query|string|true|An opaque string that will be passed back to the redirect URL and therefore can be used to communicate client side state and prevent CSRF attacks.
response_mode|query|string|false|Whether to append parameters to the redirect URL in the query string (`query`) or as fragments (`fragment`). This option usually has a sensible default for each of the response types.
nonce|query|string|false|An nonce provided by the client (and opaque to Authentiq Connect) that will be included in any ID Token generated for this session. Clients should use the nonce to mitigate replay attacks.
display|query|string|false|The authentication display mode, which can be one of `page`, `popup` or `modal`. Defaults to `page`.
prompt|query|string|false|Space-delimited, case sensitive list of ASCII string values that specifies whether the Authorization Server prompts the End-User for reauthentication and consent. The supported values are: `none`, `login`, `consent`. If `consent` the end-user is asked to (re)confirm what claims they share. Use `none` to check for an active session.
max_age|query|integer|false|Specifies the allowable elapsed time in seconds since the last time the end-user was actively authenticated.
ui_locales|query|string|false|Specifies the preferred language to use on the authorization page, as a space-separated list of BCP47 language tags. Ignored at the moment.


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
302|[Found](https://tools.ietf.org/html/rfc7231#section-6.4.3)|A successful or erroneous authentication response.|None
303|[See Other](https://tools.ietf.org/html/rfc7231#section-6.4.4)|*Sign in with Authentiq* page, popup or modal.|None

<aside class="success">
This operation does not require authentication
</aside>

## token

> Code samples

```shell
# You can also use wget
curl -X POST https://connect.authentiq.io//token \
  -H 'Authorization: string' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'Accept: application/x-www-form-urlencoded'

```

```http
POST https://connect.authentiq.io//token HTTP/1.1
Host: connect.authentiq.io
Content-Type: application/x-www-form-urlencoded
Accept: application/x-www-form-urlencoded
Authorization: string

```

```javascript
var headers = {
  'Authorization':'string',
  'Content-Type':'application/x-www-form-urlencoded',
  'Accept':'application/x-www-form-urlencoded'

};

$.ajax({
  url: 'https://connect.authentiq.io//token',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```python
import requests
headers = {
  'Authorization': 'string',
  'Content-Type': 'application/x-www-form-urlencoded',
  'Accept': 'application/x-www-form-urlencoded'
}

r = requests.post('https://connect.authentiq.io//token', params={

}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'string',
  'Content-Type' => 'application/x-www-form-urlencoded',
  'Accept' => 'application/x-www-form-urlencoded'
}

result = RestClient.post 'https://connect.authentiq.io//token',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://connect.authentiq.io//token");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /token`

*Obtain an ID Token*

Exchange en authorization code for an ID Token or Access Token.

This endpoint supports both `client_secret_post` and `client_secret_basic` authenticatino methods, as specified by the client's `token_endpoint_auth_method`.

See also:
  - [OIDC Token Endpoint](http://openid.net/specs/openid-connect-core-1_0.html#TokenRequest)
  - [OIDC Successful Token response](http://openid.net/specs/openid-connect-core-1_0.html#TokenResponse)
  - [OIDC Token Error response](http://openid.net/specs/openid-connect-core-1_0.html#TokenError)

> Body parameter

```yaml
client_id: string
client_secret: pa$$word
grant_type: string
code: string
redirect_uri: string

```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
Authorization|header|string|false|HTTP Basic authorization header.
body|body|object|false|No description
» client_id|body|string|true|The registered client ID.
» client_secret|body|string(password)|false|The registered client ID secret.
» grant_type|body|string|false|The authorization grant type, must be `authorization_code`.
» code|body|string|false|The authorization code previously obtained from the Authentication endpoint.
» redirect_uri|body|string|false|The redirect URL that was used previously with the Authentication endpoint.


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## userInfo

> Code samples

```shell
# You can also use wget
curl -X GET https://connect.authentiq.io//userinfo \
  -H 'Accept: application/x-www-form-urlencoded'

```

```http
GET https://connect.authentiq.io//userinfo HTTP/1.1
Host: connect.authentiq.io

Accept: application/x-www-form-urlencoded

```

```javascript
var headers = {
  'Accept':'application/x-www-form-urlencoded'

};

$.ajax({
  url: 'https://connect.authentiq.io//userinfo',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```python
import requests
headers = {
  'Accept': 'application/x-www-form-urlencoded'
}

r = requests.get('https://connect.authentiq.io//userinfo', params={

}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/x-www-form-urlencoded'
}

result = RestClient.get 'https://connect.authentiq.io//userinfo',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://connect.authentiq.io//userinfo");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /userinfo`

*Retrieve their user profile*

Use this endpoint to retrieve a user's profile in case you've not already obtained enough details from the ID Token via the Token Endpoint.
 See also:
 - [OIDC UserInfo endpoint](http://openid.net/specs/openid-connect-core-1_0.html#UserInfo)

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|No description|None
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No description|None
default|Default|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: oidc email phone address aq:location aq:name aq:push ), oauth2 ( Scopes: oidc email phone address aq:location aq:name aq:push )
</aside>

# Client Management

## client

> Code samples

```shell
# You can also use wget
curl -X GET https://connect.authentiq.io//client \
  -H 'Accept: application/json'

```

```http
GET https://connect.authentiq.io//client HTTP/1.1
Host: connect.authentiq.io

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://connect.authentiq.io//client',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://connect.authentiq.io//client', params={

}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://connect.authentiq.io//client',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://connect.authentiq.io//client");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /client`

*List clients*

Retrieve a list of clients.

> Example responses

```json
[
  {
    "application_type": "string",
    "client_id": "string",
    "client_name": "string",
    "client_uri": "string",
    "contacts": [
      "string"
    ],
    "default_max_age": 0,
    "default_scopes": [
      "string"
    ],
    "grant_types": [
      "string"
    ],
    "logo_uri": "string",
    "policy_uri": "string",
    "redirect_uris": [
      "string"
    ],
    "response_types": [
      "string"
    ],
    "tos_uri": "string"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of Client Objects.|Inline
default|Default|No description|None

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Client](#schemaclient)]|false|No description
» application_type|string|false|No description
» client_id|string|false|No description
» client_name|string|true|No description
» client_uri|string|true|No description
» default_max_age|integer(int64)|false|No description
» logo_uri|string|false|No description
» policy_uri|string|false|No description
» tos_uri|string|false|No description
» contacts|[string]|false|No description
» default_scopes|[string]|false|No description
» grant_types|[string]|false|No description
» redirect_uris|[string]|false|No description
» response_types|[string]|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey, oauth2, oauth2
</aside>

## createClient

> Code samples

```shell
# You can also use wget
curl -X POST https://connect.authentiq.io//client \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/x-www-form-urlencoded'

```

```http
POST https://connect.authentiq.io//client HTTP/1.1
Host: connect.authentiq.io
Content-Type: application/json
Accept: application/x-www-form-urlencoded

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/x-www-form-urlencoded'

};

$.ajax({
  url: 'https://connect.authentiq.io//client',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/x-www-form-urlencoded'
}

r = requests.post('https://connect.authentiq.io//client', params={

}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/x-www-form-urlencoded'
}

result = RestClient.post 'https://connect.authentiq.io//client',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://connect.authentiq.io//client");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /client`

*Register a client*

Register a new client with this Authentiq Connect provider.

This endpoint is compatible with [OIDC's Client Registration](http://openid.net/specs/openid-connect-registration-1_0.html) extension.

See also:
- [OIDC Client Registration Endpoint](http://openid.net/specs/openid-connect-registration-1_0.html#ClientRegistration)

> Body parameter

```json
{
  "application_type": "string",
  "client_id": "string",
  "client_name": "string",
  "client_uri": "string",
  "contacts": [
    "string"
  ],
  "default_max_age": 0,
  "default_scopes": [
    "string"
  ],
  "grant_types": [
    "string"
  ],
  "logo_uri": "string",
  "policy_uri": "string",
  "redirect_uris": [
    "string"
  ],
  "response_types": [
    "string"
  ],
  "tos_uri": "string"
}
```
```yaml
application_type: string
client_id: string
client_name: string
client_uri: string
contacts:
  - string
default_max_age: 0
default_scopes:
  - string
grant_types:
  - string
logo_uri: string
policy_uri: string
redirect_uris:
  - string
response_types:
  - string
tos_uri: string

```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Client](#schemaclient)|true|Client Object
» application_type|body|string|false|No description
» client_id|body|string|false|No description
» client_name|body|string|true|No description
» client_uri|body|string|true|No description
» default_max_age|body|integer(int64)|false|No description
» logo_uri|body|string|false|No description
» policy_uri|body|string|false|No description
» tos_uri|body|string|false|No description
» contacts|body|[string]|false|No description
» default_scopes|body|[string]|false|No description
» grant_types|body|[string]|false|No description
» redirect_uris|body|[string]|false|No description
» response_types|body|[string]|false|No description


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Client created|None
default|Default|No description|None

### Response Headers

Status|Header|Type|Format|Description
---|---|---|---|---|
201|Location|string||URL of new client resource

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey, oauth2, oauth2
</aside>

## clientClient_id

> Code samples

```shell
# You can also use wget
curl -X DELETE https://connect.authentiq.io//client/{client_id} \
  -H 'Accept: application/x-www-form-urlencoded'

```

```http
DELETE https://connect.authentiq.io//client/{client_id} HTTP/1.1
Host: connect.authentiq.io

Accept: application/x-www-form-urlencoded

```

```javascript
var headers = {
  'Accept':'application/x-www-form-urlencoded'

};

$.ajax({
  url: 'https://connect.authentiq.io//client/{client_id}',
  method: 'delete',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```python
import requests
headers = {
  'Accept': 'application/x-www-form-urlencoded'
}

r = requests.delete('https://connect.authentiq.io//client/{client_id}', params={

}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/x-www-form-urlencoded'
}

result = RestClient.delete 'https://connect.authentiq.io//client/{client_id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://connect.authentiq.io//client/{client_id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /client/{client_id}`

*Delete a client*

Delete a previously registered client.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
client_id|path|string|true|Client identifier


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Client deleted|None
default|Default|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey, oauth2, oauth2
</aside>

## getClient

> Code samples

```shell
# You can also use wget
curl -X GET https://connect.authentiq.io//client/{client_id} \
  -H 'Accept: application/json'

```

```http
GET https://connect.authentiq.io//client/{client_id} HTTP/1.1
Host: connect.authentiq.io

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://connect.authentiq.io//client/{client_id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://connect.authentiq.io//client/{client_id}', params={

}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://connect.authentiq.io//client/{client_id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://connect.authentiq.io//client/{client_id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /client/{client_id}`

*View a client*

Retrieve the configuration of a previously registered client.

See also:
- [OIDC Client Configuration Endpoint](http://openid.net/specs/openid-connect-registration-1_0.html#ClientConfigurationEndpoint)

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
client_id|path|string|true|Client identifier


> Example responses

```json
{
  "application_type": "string",
  "client_id": "string",
  "client_name": "string",
  "client_uri": "string",
  "contacts": [
    "string"
  ],
  "default_max_age": 0,
  "default_scopes": [
    "string"
  ],
  "grant_types": [
    "string"
  ],
  "logo_uri": "string",
  "policy_uri": "string",
  "redirect_uris": [
    "string"
  ],
  "response_types": [
    "string"
  ],
  "tos_uri": "string"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Client found|[Client](#schemaclient)
default|Default|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey, oauth2, oauth2
</aside>

## updateClient

> Code samples

```shell
# You can also use wget
curl -X PUT https://connect.authentiq.io//client/{client_id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT https://connect.authentiq.io//client/{client_id} HTTP/1.1
Host: connect.authentiq.io
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://connect.authentiq.io//client/{client_id}',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.put('https://connect.authentiq.io//client/{client_id}', params={

}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.put 'https://connect.authentiq.io//client/{client_id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://connect.authentiq.io//client/{client_id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PUT /client/{client_id}`

*Update a client*

Update the configuration of a previously registered client.

See also:
- [OIDC Client Configuration Endpoint](http://openid.net/specs/openid-connect-registration-1_0.html#ClientConfigurationEndpoint)

> Body parameter

```json
{
  "application_type": "string",
  "client_id": "string",
  "client_name": "string",
  "client_uri": "string",
  "contacts": [
    "string"
  ],
  "default_max_age": 0,
  "default_scopes": [
    "string"
  ],
  "grant_types": [
    "string"
  ],
  "logo_uri": "string",
  "policy_uri": "string",
  "redirect_uris": [
    "string"
  ],
  "response_types": [
    "string"
  ],
  "tos_uri": "string"
}
```
```yaml
application_type: string
client_id: string
client_name: string
client_uri: string
contacts:
  - string
default_max_age: 0
default_scopes:
  - string
grant_types:
  - string
logo_uri: string
policy_uri: string
redirect_uris:
  - string
response_types:
  - string
tos_uri: string

```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
client_id|path|string|true|Client identifier
body|body|[Client](#schemaclient)|true|Client Object
» application_type|body|string|false|No description
» client_id|body|string|false|No description
» client_name|body|string|true|No description
» client_uri|body|string|true|No description
» default_max_age|body|integer(int64)|false|No description
» logo_uri|body|string|false|No description
» policy_uri|body|string|false|No description
» tos_uri|body|string|false|No description
» contacts|body|[string]|false|No description
» default_scopes|body|[string]|false|No description
» grant_types|body|[string]|false|No description
» redirect_uris|body|[string]|false|No description
» response_types|body|[string]|false|No description


> Example responses

```json
{
  "application_type": "string",
  "client_id": "string",
  "client_name": "string",
  "client_uri": "string",
  "contacts": [
    "string"
  ],
  "default_max_age": 0,
  "default_scopes": [
    "string"
  ],
  "grant_types": [
    "string"
  ],
  "logo_uri": "string",
  "policy_uri": "string",
  "redirect_uris": [
    "string"
  ],
  "response_types": [
    "string"
  ],
  "tos_uri": "string"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Client updated|[Client](#schemaclient)
default|Default|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey, oauth2, oauth2
</aside>

# Session Management

## authorizeIframe

> Code samples

```shell
# You can also use wget
curl -X GET https://connect.authentiq.io//{client_id}/iframe

```

```http
GET https://connect.authentiq.io//{client_id}/iframe HTTP/1.1
Host: connect.authentiq.io


```

```javascript

$.ajax({
  url: 'https://connect.authentiq.io//{client_id}/iframe',
  method: 'get',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```python
import requests

r = requests.get('https://connect.authentiq.io//{client_id}/iframe', params={

)

print r.json()
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.get 'https://connect.authentiq.io//{client_id}/iframe',
  params: {
  }

p JSON.parse(result)
```

```java
URL obj = new URL("https://connect.authentiq.io//{client_id}/iframe");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /{client_id}/iframe`

*Include a session iframe*

An OpenID Connect Session Management iframe to facilitate e.g. single sign-on or remote logouts.

The iframe implements the OIDC postMessage-based [change notification protocol](http://openid.net/specs/openid-connect-session-1_0.html#ChangeNotification) via which a client can receive notifications about session state changes.

See also:
- [OIDC OP iframe](http://openid.net/specs/openid-connect-session-1_0.html#OPiframe)

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
client_id|path|string|true|Client identifier


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None

### Response Headers

Status|Header|Type|Format|Description
---|---|---|---|---|
200|Cache-Control|string||public, max-age=7200

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

## Address

<a name="schemaaddress"></a>

```json
{
  "country": "string",
  "locality": "string",
  "postal_code": "string",
  "region": "string",
  "street_address": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
country|string|false|No description
locality|string|false|No description
postal_code|string|false|No description
region|string|false|No description
street_address|string|false|No description



## Client

<a name="schemaclient"></a>

```json
{
  "application_type": "string",
  "client_id": "string",
  "client_name": "string",
  "client_uri": "string",
  "contacts": [
    "string"
  ],
  "default_max_age": 0,
  "default_scopes": [
    "string"
  ],
  "grant_types": [
    "string"
  ],
  "logo_uri": "string",
  "policy_uri": "string",
  "redirect_uris": [
    "string"
  ],
  "response_types": [
    "string"
  ],
  "tos_uri": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
application_type|string|false|No description
client_id|string|false|No description
client_name|string|true|No description
client_uri|string|true|No description
default_max_age|integer(int64)|false|No description
logo_uri|string|false|No description
policy_uri|string|false|No description
tos_uri|string|false|No description
contacts|[string]|false|No description
default_scopes|[string]|false|No description
grant_types|[string]|false|No description
redirect_uris|[string]|false|No description
response_types|[string]|false|No description



## OAuth2Error

<a name="schemaoauth2error"></a>

```json
{
  "error": "string",
  "error_description": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
error|string|true|No description
error_description|string|false|No description



## ProblemDetail

<a name="schemaproblemdetail"></a>

```json
{
  "detail": "string",
  "status": 0,
  "title": "string",
  "type": "about:blank"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
detail|string|false|Human-readable explanation specific to this occurrence of the problem. 
status|integer|true|The HTTP status code for this occurrence of the problem. 
title|string|false|Human-readable summary of the problem type. 
type|string|true|No description



## Session

<a name="schemasession"></a>

```json
{
  "authenticated_at": "2017-10-04T19:06:09Z",
  "client_id": "string",
  "client_name": "string",
  "client_uri": "string",
  "concluded_at": "2017-10-04T19:06:09Z",
  "connected_at": "2017-10-04T19:06:09Z",
  "contacts": [
    "string"
  ],
  "created_at": "string",
  "deleted_at": "2017-10-04T19:06:09Z",
  "logo_uri": "string",
  "nonce": "string",
  "policy_uri": "string",
  "redirect_uri": "string",
  "response_mode": "string",
  "response_type": "string",
  "scopes": [
    "string"
  ],
  "scopes_optional": [
    "string"
  ],
  "scopes_required": [
    "string"
  ],
  "scopes_seen": [
    "string"
  ],
  "scopes_signed": [
    "string"
  ],
  "session_id": "string",
  "session_state": "string",
  "session_uri": "string",
  "sub": "string",
  "tokens_seen": [
    "string"
  ],
  "tos_uri": "string",
  "version": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
authenticated_at|string(date-time)|false|No description
client_id|string|false|No description
client_name|string|false|No description
client_uri|string|false|No description
concluded_at|string(date-time)|false|No description
connected_at|string(date-time)|false|No description
created_at|string|false|No description
deleted_at|string(date-time)|false|No description
logo_uri|string|false|No description
nonce|string|false|No description
policy_uri|string|false|No description
redirect_uri|string|false|No description
response_mode|string|false|No description
response_type|string|false|No description
session_id|string|false|No description
session_state|string|false|No description
session_uri|string|false|No description
sub|string|false|No description
tos_uri|string|false|No description
version|integer|false|No description
contacts|[string]|false|No description
scopes|[string]|false|No description
scopes_optional|[string]|false|No description
scopes_required|[string]|false|No description
scopes_seen|[string]|false|No description
scopes_signed|[string]|false|No description
tokens_seen|[string]|false|No description



## Token

<a name="schematoken"></a>

```json
{
  "access_token": "string",
  "expires_at": 0,
  "expires_in": 0,
  "id_token": "string",
  "refresh_token": "string",
  "scope": "string",
  "token_type": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
access_token|string|false|The access token issued by the authorization server.
expires_at|integer(int64)|false|The time the access token will expire in seconds since epoch.
expires_in|integer(int32)|false|The lifetime in seconds of the access token.
id_token|string|false|ID Token value associated with the authenticated session.
refresh_token|string|false|The refresh token issued to the client, if any.
scope|string|false|The scope of the granted tokens.
token_type|string|true|No description



## UserInfo

<a name="schemauserinfo"></a>

```json
{
  "address": {
    "country": "string",
    "locality": "string",
    "postal_code": "string",
    "region": "string",
    "street_address": "string"
  },
  "aq:location": {
    "address": {
      "country": "string",
      "locality": "string",
      "postal_code": "string",
      "region": "string",
      "street_address": "string"
    },
    "latitude": 0,
    "longitude": 0
  },
  "email": "string",
  "email_verified": true,
  "family_name": "string",
  "given_name": "string",
  "name": "string",
  "phone_number": "string",
  "phone_number_verified": true,
  "sub": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
address|[Address](#schemaaddress)|false|OIDC Address structure
» country|string|false|No description
» locality|string|false|No description
» postal_code|string|false|No description
» region|string|false|No description
» street_address|string|false|No description
aq:location|object|false|Geolocation structure
» address|[Address](#schemaaddress)|false|OIDC Address structure
»» country|string|false|No description
»» locality|string|false|No description
»» postal_code|string|false|No description
»» region|string|false|No description
»» street_address|string|false|No description
» latitude|number(float)|false|No description
» longitude|number(float)|false|No description
email|string|false|No description
email_verified|boolean|false|No description
family_name|string|false|No description
given_name|string|false|No description
name|string|false|No description
phone_number|string|false|No description
phone_number_verified|boolean|false|No description
sub|string|true|No description





