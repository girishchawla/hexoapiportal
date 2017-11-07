---
title: Uber API v1.0.0
language_tabs:
  - shell
  - http
  - html
  - javascript
  - python
  - ruby
  - java
toc_footers: []
includes: []
search: true
highlight_theme: darkula
---

# Uber API v1.0.0

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Move your app forward with the Uber API

Base URLs:

* <a href="https://api.uber.com/v1">https://api.uber.com/v1</a>





# Authentication


* API Key
    - Parameter Name: **server_token**, in: query. 



# Products

## GET /products

> Code samples

```shell
# You can also use wget
curl -X GET https://api.uber.com/v1/products?latitude=0&longitude=0 \
  -H 'Accept: application/json'

```

```http
GET https://api.uber.com/v1/products?latitude=0&longitude=0 HTTP/1.1
Host: api.uber.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.uber.com/v1/products',
  method: 'get',
  data: '?latitude=0&longitude=0',
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

r = requests.get('https://api.uber.com/v1/products', params={
  'latitude': 0,  'longitude': 0
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.uber.com/v1/products',
  params: {
  'latitude' => 'number(double)',
'longitude' => 'number(double)'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.uber.com/v1/products?latitude=0&longitude=0");
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

*Product Types*

The Products endpoint returns information about the Uber products offered at a given location. The response includes the display name and other details about each product, and lists the products in the proper display order.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
latitude|query|number(double)|true|Latitude component of location.
longitude|query|number(double)|true|Longitude component of location.


> Example responses

```json
{}
```
```json
{}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|An array of products|[ProductList](#schemaproductlist)
default|Default|Unexpected error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

# Estimates

## GET /estimates/price

> Code samples

```shell
# You can also use wget
curl -X GET https://api.uber.com/v1/estimates/price?start_latitude=0&start_longitude=0&end_latitude=0&end_longitude=0 \
  -H 'Accept: application/json'

```

```http
GET https://api.uber.com/v1/estimates/price?start_latitude=0&start_longitude=0&end_latitude=0&end_longitude=0 HTTP/1.1
Host: api.uber.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.uber.com/v1/estimates/price',
  method: 'get',
  data: '?start_latitude=0&start_longitude=0&end_latitude=0&end_longitude=0',
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

r = requests.get('https://api.uber.com/v1/estimates/price', params={
  'start_latitude': 0,  'start_longitude': 0,  'end_latitude': 0,  'end_longitude': 0
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.uber.com/v1/estimates/price',
  params: {
  'start_latitude' => 'number(double)',
'start_longitude' => 'number(double)',
'end_latitude' => 'number(double)',
'end_longitude' => 'number(double)'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.uber.com/v1/estimates/price?start_latitude=0&start_longitude=0&end_latitude=0&end_longitude=0");
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

*Price Estimates*

The Price Estimates endpoint returns an estimated price range for each product offered at a given location. The price estimate is provided as a formatted string with the full price range and the localized currency symbol.<br><br>The response also includes low and high estimates, and the [ISO 4217](http://en.wikipedia.org/wiki/ISO_4217) currency code for situations requiring currency conversion. When surge is active for a particular product, its surge_multiplier will be greater than 1, but the price estimate already factors in this multiplier.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
start_latitude|query|number(double)|true|Latitude component of start location.
start_longitude|query|number(double)|true|Longitude component of start location.
end_latitude|query|number(double)|true|Latitude component of end location.
end_longitude|query|number(double)|true|Longitude component of end location.


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
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|An array of price estimates by product|Inline
default|Default|Unexpected error|[Error](#schemaerror)

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[PriceEstimate](#schemapriceestimate)]|false|No description
» product_id|string|false|Unique identifier representing a specific product for a given latitude & longitude. For example, uberX in San Francisco will have a different product_id than uberX in Los Angeles
» currency_code|string|false|[ISO 4217](http://en.wikipedia.org/wiki/ISO_4217) currency code.
» display_name|string|false|Display name of product.
» estimate|string|false|Formatted string of estimate in local currency of the start location. Estimate could be a range, a single number (flat rate) or "Metered" for TAXI.
» low_estimate|number|false|Lower bound of the estimated price.
» high_estimate|number|false|Upper bound of the estimated price.
» surge_multiplier|number|false|Expected surge multiplier. Surge is active if surge_multiplier is greater than 1. Price estimate already factors in the surge multiplier.



<aside class="success">
This operation does not require authentication
</aside>

## GET /estimates/time

> Code samples

```shell
# You can also use wget
curl -X GET https://api.uber.com/v1/estimates/time?start_latitude=0&start_longitude=0 \
  -H 'Accept: application/json'

```

```http
GET https://api.uber.com/v1/estimates/time?start_latitude=0&start_longitude=0 HTTP/1.1
Host: api.uber.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.uber.com/v1/estimates/time',
  method: 'get',
  data: '?start_latitude=0&start_longitude=0',
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

r = requests.get('https://api.uber.com/v1/estimates/time', params={
  'start_latitude': 0,  'start_longitude': 0
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.uber.com/v1/estimates/time',
  params: {
  'start_latitude' => 'number(double)',
'start_longitude' => 'number(double)'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.uber.com/v1/estimates/time?start_latitude=0&start_longitude=0");
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

*Time Estimates*

The Time Estimates endpoint returns ETAs for all products offered at a given location, with the responses expressed as integers in seconds. We recommend that this endpoint be called every minute to provide the most accurate, up-to-date ETAs.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
start_latitude|query|number(double)|true|Latitude component of start location.
start_longitude|query|number(double)|true|Longitude component of start location.
customer_uuid|query|string(uuid)|false|Unique customer identifier to be used for experience customization.
product_id|query|string|false|Unique identifier representing a specific product for a given latitude & longitude.


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
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|An array of products|Inline
default|Default|Unexpected error|[Error](#schemaerror)

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Product](#schemaproduct)]|false|No description
» product_id|string|false|Unique identifier representing a specific product for a given latitude & longitude. For example, uberX in San Francisco will have a different product_id than uberX in Los Angeles.
» description|string|false|Description of product.
» display_name|string|false|Display name of product.
» capacity|integer|false|Capacity of product. For example, 4 people.
» image|string|false|Image URL representing the product.



<aside class="success">
This operation does not require authentication
</aside>

# User

## GET /me

> Code samples

```shell
# You can also use wget
curl -X GET https://api.uber.com/v1/me \
  -H 'Accept: application/json'

```

```http
GET https://api.uber.com/v1/me HTTP/1.1
Host: api.uber.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.uber.com/v1/me',
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

r = requests.get('https://api.uber.com/v1/me', params={

}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.uber.com/v1/me',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.uber.com/v1/me");
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

*User Profile*

The User Profile endpoint returns information about the Uber user that has authorized with the application.

> Example responses

```json
{}
```
```json
{}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Profile information for a user|[Profile](#schemaprofile)
default|Default|Unexpected error|[Error](#schemaerror)

<aside class="success">
This operation does not require authentication
</aside>

## GET /history

> Code samples

```shell
# You can also use wget
curl -X GET https://api.uber.com/v1/history \
  -H 'Accept: application/json'

```

```http
GET https://api.uber.com/v1/history HTTP/1.1
Host: api.uber.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.uber.com/v1/history',
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

r = requests.get('https://api.uber.com/v1/history', params={

}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.uber.com/v1/history',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.uber.com/v1/history");
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

*User Activity*

The User Activity endpoint returns data about a user's lifetime activity with Uber. The response will include pickup locations and times, dropoff locations and times, the distance of past requests, and information about which products were requested.<br><br>The history array in the response will have a maximum length based on the limit parameter. The response value count may exceed limit, therefore subsequent API requests may be necessary.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
offset|query|integer(int32)|false|Offset the list of returned results by this amount. Default is zero.
limit|query|integer(int32)|false|Number of items to retrieve. Default is 5, maximum is 100.


> Example responses

```json
{}
```
```json
{}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|History information for the given user|[Activities](#schemaactivities)
default|Default|Unexpected error|[Error](#schemaerror)

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

## Product

<a name="schemaproduct"></a>

```json
{} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
product_id|string|false|Unique identifier representing a specific product for a given latitude & longitude. For example, uberX in San Francisco will have a different product_id than uberX in Los Angeles.
description|string|false|Description of product.
display_name|string|false|Display name of product.
capacity|integer|false|Capacity of product. For example, 4 people.
image|string|false|Image URL representing the product.



## ProductList

<a name="schemaproductlist"></a>

```json
{} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
products|[[Product](#schemaproduct)]|false|Contains the list of products
» product_id|string|false|Unique identifier representing a specific product for a given latitude & longitude. For example, uberX in San Francisco will have a different product_id than uberX in Los Angeles.
» description|string|false|Description of product.
» display_name|string|false|Display name of product.
» capacity|integer|false|Capacity of product. For example, 4 people.
» image|string|false|Image URL representing the product.



## PriceEstimate

<a name="schemapriceestimate"></a>

```json
{} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
product_id|string|false|Unique identifier representing a specific product for a given latitude & longitude. For example, uberX in San Francisco will have a different product_id than uberX in Los Angeles
currency_code|string|false|[ISO 4217](http://en.wikipedia.org/wiki/ISO_4217) currency code.
display_name|string|false|Display name of product.
estimate|string|false|Formatted string of estimate in local currency of the start location. Estimate could be a range, a single number (flat rate) or "Metered" for TAXI.
low_estimate|number|false|Lower bound of the estimated price.
high_estimate|number|false|Upper bound of the estimated price.
surge_multiplier|number|false|Expected surge multiplier. Surge is active if surge_multiplier is greater than 1. Price estimate already factors in the surge multiplier.



## Profile

<a name="schemaprofile"></a>

```json
{} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
first_name|string|false|First name of the Uber user.
last_name|string|false|Last name of the Uber user.
email|string|false|Email address of the Uber user
picture|string|false|Image URL of the Uber user.
promo_code|string|false|Promo code of the Uber user.



## Activity

<a name="schemaactivity"></a>

```json
{} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
uuid|string|false|Unique identifier for the activity



## Activities

<a name="schemaactivities"></a>

```json
{} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
offset|integer(int32)|false|Position in pagination.
limit|integer(int32)|false|Number of items to retrieve (100 max).
count|integer(int32)|false|Total number of items available.
history|[[Activity](#schemaactivity)]|false|No description
» uuid|string|false|Unique identifier for the activity



## Error

<a name="schemaerror"></a>

```json
{} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
code|string|false|No description
message|string|false|No description
fields|string|false|No description





