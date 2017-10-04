---
title: Swagger Petstore v1.0.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
toc_footers: []
includes: []
search: true
highlight_theme: darkula
---
# Swagger Petstore v1.0.0
> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.
Base URLs:
* <a href="http://petstore.swagger.io/v1">http://petstore.swagger.io/v1</a>
 License: MIT
# pets
## listPets
> Code samples
```shell
# You can also use wget
curl -X GET http://petstore.swagger.io/v1/pets \
  -H 'Accept: application/json'
```
```http
GET http://petstore.swagger.io/v1/pets HTTP/1.1
Host: petstore.swagger.io
Accept: application/json
```
```javascript
var headers = {
  'Accept':'application/json'
};
$.ajax({
  url: 'http://petstore.swagger.io/v1/pets',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```
```javascript--nodejs
const request = require('node-fetch');
const headers = {
  'Accept':'application/json'
};
fetch('http://petstore.swagger.io/v1/pets',
{
  method: 'GET',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```
```ruby
require 'rest-client'
require 'json'
headers = {
  'Accept' => 'application/json'
}
result = RestClient.get 'http://petstore.swagger.io/v1/pets',
  params: {
  }, headers: headers
p JSON.parse(result)
```
```python
import requests
headers = {
  'Accept': 'application/json'
}
r = requests.get('http://petstore.swagger.io/v1/pets', params={
}, headers = headers)
print r.json()
```
```java
URL obj = new URL("http://petstore.swagger.io/v1/pets");
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
`GET /pets`
*List all pets*
### Parameters
Parameter|In|Type|Required|Description
---|---|---|---|---|
limit|query|integer(int32)|false|How many items to return at one time (max 100)
> Example responses
```json
[
  {}
]
```
```json
{}
```
### Responses
Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|An paged array of pets|[Pets](#schemapets)
default|Default|unexpected error|[Error](#schemaerror)
### Response Headers
Status|Header|Type|Format|Description
---|---|---|---|---|
200|x-next|string||A link to the next page of responses
<aside class="success">
This operation does not require authentication
</aside>
## createPets
> Code samples
```shell
# You can also use wget
curl -X POST http://petstore.swagger.io/v1/pets \
  -H 'Accept: application/json'
```
```http
POST http://petstore.swagger.io/v1/pets HTTP/1.1
Host: petstore.swagger.io
Accept: application/json
```
```javascript
var headers = {
  'Accept':'application/json'
};
$.ajax({
  url: 'http://petstore.swagger.io/v1/pets',
  method: 'post',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```
```javascript--nodejs
const request = require('node-fetch');
const headers = {
  'Accept':'application/json'
};
fetch('http://petstore.swagger.io/v1/pets',
{
  method: 'POST',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```
```ruby
require 'rest-client'
require 'json'
headers = {
  'Accept' => 'application/json'
}
result = RestClient.post 'http://petstore.swagger.io/v1/pets',
  params: {
  }, headers: headers
p JSON.parse(result)
```
```python
import requests
headers = {
  'Accept': 'application/json'
}
r = requests.post('http://petstore.swagger.io/v1/pets', params={
}, headers = headers)
print r.json()
```
```java
URL obj = new URL("http://petstore.swagger.io/v1/pets");
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
`POST /pets`
*Create a pet*
> Example responses
```json
{}
```
### Responses
Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Null response|None
default|Default|unexpected error|[Error](#schemaerror)
<aside class="success">
This operation does not require authentication
</aside>
## showPetById
> Code samples
```shell
# You can also use wget
curl -X GET http://petstore.swagger.io/v1/pets/{petId} \
  -H 'Accept: application/json'
```
```http
GET http://petstore.swagger.io/v1/pets/{petId} HTTP/1.1
Host: petstore.swagger.io
Accept: application/json
```
```javascript
var headers = {
  'Accept':'application/json'
};
$.ajax({
  url: 'http://petstore.swagger.io/v1/pets/{petId}',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```
```javascript--nodejs
const request = require('node-fetch');
const headers = {
  'Accept':'application/json'
};
fetch('http://petstore.swagger.io/v1/pets/{petId}',
{
  method: 'GET',
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```
```ruby
require 'rest-client'
require 'json'
headers = {
  'Accept' => 'application/json'
}
result = RestClient.get 'http://petstore.swagger.io/v1/pets/{petId}',
  params: {
  }, headers: headers
p JSON.parse(result)
```
```python
import requests
headers = {
  'Accept': 'application/json'
}
r = requests.get('http://petstore.swagger.io/v1/pets/{petId}', params={
}, headers = headers)
print r.json()
```
```java
URL obj = new URL("http://petstore.swagger.io/v1/pets/{petId}");
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
`GET /pets/{petId}`
*Info for a specific pet*
### Parameters
Parameter|In|Type|Required|Description
---|---|---|---|---|
petId|path|string|true|The id of the pet to retrieve
> Example responses
```json
[
  {}
]
```
```json
{}
```
### Responses
Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Expected response to a valid request|[Pets](#schemapets)
default|Default|unexpected error|[Error](#schemaerror)
<aside class="success">
This operation does not require authentication
</aside>
# Schemas
## Pet
<a name="schemapet"></a>
```json
{} 
```
### Properties
Name|Type|Required|Description
---|---|---|---|
id|integer(int64)|true|No description
name|string|true|No description
tag|string|false|No description
## Pets
<a name="schemapets"></a>
```json
[
  {}
] 
```
### Properties
Name|Type|Required|Description
---|---|---|---|
anonymous|[[Pet](#schemapet)]|false|No description
» id|integer(int64)|true|No description
» name|string|true|No description
» tag|string|false|No description
## Error
<a name="schemaerror"></a>
```json
{} 
```
### Properties
Name|Type|Required|Description
---|---|---|---|
code|integer(int32)|true|No description
message|string|true|No description

