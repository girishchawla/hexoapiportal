---
title: Amadeus Travel Innovation Sandbox v1.2
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

# Amadeus Travel Innovation Sandbox v1.2

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.


Base URLs:

* <a href="https://api.sandbox.amadeus.com/v1.2">https://api.sandbox.amadeus.com/v1.2</a>



Web: <a href="https://sandbox.amadeus.com">Amadeus Innovation and Research</a> 
License: <a href="https://sandbox.amadeus.com/terms-use">Amadeus Travel Innovation Sandbox License</a>

# Authentication


* API Key
    - Parameter Name: **apikey**, in: query. API Key provided for your account, to identify you for API access. Make sure to keep this API key secret.



# Default

## Airport Autocomplete

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/airports/autocomplete?term=Ban \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/airports/autocomplete?term=Ban HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/airports/autocomplete',
  method: 'get',
  data: '?term=Ban',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/airports/autocomplete', params={
  'term': 'Ban'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/airports/autocomplete',
  params: {
  'term' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/airports/autocomplete?term=Ban");
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

`GET /airports/autocomplete`

*Airport Autocomplete - Find an IATA location code for flight search based on a city or airport name using the term parameter. By only using the country parameter, this API is also able to find all the IATA location codes associated with a country. Both term and country parameters can be used together to filter the results accordingly. The API is fully JQuery-Autocomplete compatible to enable you to quickly build a drop-down list for your users to find the right airport easily.*

<p>Using the term parameter and given the start of any word in an airport's official name, a city name, or the start of an <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a>, this API provides the full name and IATA location code of the city or airport, for use in flight searches. Only major cities and civilian airports with several commercial flights per week are included by default. The response provides up to 20 possible matches, sorted by importance, in a <a href="http://jqueryui.com/autocomplete/">JQuery UI Autocomplete</a> compatible format. <a href="https://github.com/amadeus-travel-innovation-sandbox/sandbox-content/blob/master/airport-autocomplete-template.html">This sample implementation</a> using JQuery UI may help. This API uses data from the <a href="https://github.com/opentraveldata/opentraveldata/blob/master/opentraveldata/optd_por_public.csv">OpenTravelData</a> project.
</p> 
<p>By only using the country parameter, this API is also able to find all the IATA location codes associated with a country. Both term and country parameters can be used together to filter the results accordingly.          
</p>
<p>The value returned is the IATA location code. The label returned is always in UTF-8 format, with the airport official name (which is often in the native language), in the format of English City Name (if not already included in the airport name).</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
term|query|string|true|Search keyword that should represent the start of a word in a city or airport name.
country|query|string|false|Identified a country based of a <a href="https://en.wikipedia.org/wiki/ISO_3166-2#Current_codes">ISO 3166-1 alpha-2 code</a>
all_airports|query|boolean|false|Boolean to include or not all airports, no matter their traffic rank. False by default, to only display relevant airports.


> Example responses

```json
[
  {
    "label": "string",
    "value": "string"
  }
]
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|Inline
default|Default|Client or server error|[Error](#schemaerror)

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[AirportAutocompleteResponse](#schemaairportautocompleteresponse)]|false|No description
» label|string|true|The name of this airport, in UTF-8 format, prefixed with the name of the city if it is not already incorporated in the name of the airport, and appended with the location's <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> (as in value), enclosed in square brackets.
» value|string|true|The 3 letter IATA location code of the given city or airport. You can use this as an input parameter for a flight low-fare or inspiration search.



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Nearest Relevant Airport

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/airports/nearest-relevant?latitude=46.6734&longitude=-71.7412 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/airports/nearest-relevant?latitude=46.6734&longitude=-71.7412 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/airports/nearest-relevant',
  method: 'get',
  data: '?latitude=46.6734&longitude=-71.7412',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/airports/nearest-relevant', params={
  'latitude': '46.6734',  'longitude': '-71.7412'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/airports/nearest-relevant',
  params: {
  'latitude' => 'string',
'longitude' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/airports/nearest-relevant?latitude=46.6734&longitude=-71.7412");
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

`GET /airports/nearest-relevant`

*Nearest Relevant Airport - Find the most useful nearby airport to a given location.*

<p>This service gives the most relevant airports in a radius of 500 km around the given coordinates. The relevance of an airport is computed by dividing the number of airport movements (take offs and landings) by the distance from the point. This causes the relevance of an airport to increase exponentially as you approach it.</p>

<p>To minimize response time, all distances are computed as a <a href="http://en.wikipedia.org/wiki/Great-circle_distance">great-circle distance</a> from the provided coordinates to the airport coordinates, and thus do not take into account traffic conditions, international boundaries, mountains, water, or other elements that might make the a nearby airport hard to reach.</p>

<p>Only civilian airports with at least several commercial flights per week are included in the results.</p>

<p>The result is a list of airports sorted by decreasing relevance. It always contains the nearest airport with significant commercial traffic. You can freely download the <a href="https://github.com/opentraveldata/opentraveldata/blob/master/opentraveldata/optd_por_public.csv">point of reference information</a> used by this API from the <a href="https://github.com/opentraveldata/opentraveldata">Open Travel Data</a> project.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
latitude|query|string|true|Latitude location to be at the center of your search circle.
longitude|query|string|true|Longitude location to be at the center of your search circle.


> Example responses

```json
[
  {
    "aircraft_movements": 0,
    "airport": "string",
    "airport_name": "string",
    "city": "string",
    "city_name": "string",
    "distance": 0,
    "location": {
      "google_maps_link": "string",
      "latitude": 0,
      "longitude": 0
    },
    "state": "string",
    "timezone": "string"
  }
]
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|Inline
default|Default|Client or server error|[Error](#schemaerror)

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[NearestAirport](#schemanearestairport)]|false|No description
» aircraft_movements|integer|false|The annual number of aircraft movements at that airport.
» airport|string|true|The 3 letter IATA airport code of this given airport. You can use this as an input parameter for a low-fare flight search, to get more specific results than the city code, but inspiration search works best using the city code.
» airport_name|string|true|The name of this airport, in UTF-8 format
» city|string|true|The three letter <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city of the city in which this airport is located.
» city_name|string|true|The English name of the city in which this airport is located
» distance|number|true|The distance in km from the point specified in the query, to this location
» location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
»» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
»» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
»» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
» state|string|false|The state code of this city, if applicable
» timezone|string|true|The <a href="http://en.wikipedia.org/wiki/List_of_tz_database_time_zones">Olson format</a> name of the timezone in which this airport is located



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Car Rental Airport Search

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/cars/search-airport?location=NCE&pick_up=2017-08-07&drop_off=2017-08-08 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/cars/search-airport?location=NCE&pick_up=2017-08-07&drop_off=2017-08-08 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/cars/search-airport',
  method: 'get',
  data: '?location=NCE&pick_up=2017-08-07&drop_off=2017-08-08',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/cars/search-airport', params={
  'location': 'NCE',  'pick_up': '2017-08-07',  'drop_off': '2017-08-08'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/cars/search-airport',
  params: {
  'location' => 'string',
'pick_up' => 'string',
'drop_off' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/cars/search-airport?location=NCE&pick_up=2017-08-07&drop_off=2017-08-08");
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

`GET /cars/search-airport`

*Car Rental Airport Search - Find car rental providers and rates when you provide an airport code, as well as the pick-up and drop-off dates. Optional parameters such as currency and rental provider codes are also available and can be used to narrow down the results. This API is an ideal pairing with the flight and hotel search to provide ground transportation options at the destination.*

<p>With this API you can find out the price and type of car, for all car rental providers, near a specified airport.</p>

<p>You can quickly see the locations of car providers near a given airport, and what cars are available to rent, and at what prices. This API is based on our car pricing service that gets live availability from car providers, and is used to power a variety of airline and travel agency websites.</p>
           
<p>Results are validated from car providers, and thus response times may take up to 10 seconds (response times are typically about 5s), and the number of concurrent calls is throttled per user to avoid flooding our provider's systems. However, this means the final result is guaranteed to be live and accurate.</p>

<p>The configuration of this API allows search for car rentals in the rental location where the car is picked up (at the start of the rental), is the same as the one where it will be dropped off.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
location|query|string|true|The <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the airport at which the car will be rented.
pick_up|query|string|true|Date on which the car rental will be collected from the car rental location. If no time is provided, a default value of 09:00 is used. Past availability is not displayed, future availability becomes less useful from about 6 months from the current date.
drop_off|query|string|true|Date at which the car rental will end and the car will be returned to the rental location. If no time is provided, a default value of 17:00 is used.
lang|query|string|false|The preferred language of the content related to each car rental. Content will be returned in this language if available.
currency|query|string|false|The preferred <a href="https://en.wikipedia.org/wiki/ISO_4217">currency</a> to use when displaying prices and rates related to the car rental.
provider|query|string|false|2 character car rental provider code. You may provide this parameter more than once. 
rate_class|query|string|false|Allows to request specific rate types.
rate_plan|query|string|false|Qualifies the rate depending on the pickup date and the rental duration.
rate_filter|query|string|false|Defines the types of rates to be returned in the output
vehicle|query|array[string]|false|Specifies the type of vehicle to be rented. If selected, the results set will include only vehicles that match these type descriptions. The enumerations above correspond to ACRISS Pseudo Codes, and you may also provide an ACRISS pseudo code directly. If specifying a vehicle-specific ACRISS code, you may provide this parameter up to 3 times.


#### Enumerated Values

|Parameter|Value|
|---|---|
rate_filter|AVAILABLE|
rate_filter|ESTIMATED|
rate_filter|ALL|

> Example responses

```json
{
  "results": [
    {
      "airport": "string",
      "cars": [
        {
          "estimated_total": {
            "amount": "string",
            "currency": "string"
          },
          "images": [
            {
              "category": "string",
              "height": 0,
              "url": "string",
              "width": 0
            }
          ],
          "rates": [
            {
              "price": {
                "amount": "string",
                "currency": "string"
              },
              "type": "string"
            }
          ],
          "vehicle_info": {
            "acriss_code": "string",
            "air_conditioning": true,
            "category": "string",
            "fuel": "string",
            "transmission": "string",
            "type": "string"
          }
        }
      ],
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "provider": {
        "company_code": "string",
        "company_name": "string"
      }
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[CarSearchResponse](#schemacarsearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Car Rental Geosearch

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/cars/search-circle?latitude=35.1504&longitude=-114.57632&radius=42&pick_up=2017-08-07&drop_off=2017-08-08 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/cars/search-circle?latitude=35.1504&longitude=-114.57632&radius=42&pick_up=2017-08-07&drop_off=2017-08-08 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/cars/search-circle',
  method: 'get',
  data: '?latitude=35.1504&longitude=-114.57632&radius=42&pick_up=2017-08-07&drop_off=2017-08-08',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/cars/search-circle', params={
  'latitude': 35.1504,  'longitude': -114.57632,  'radius': 42,  'pick_up': '2017-08-07',  'drop_off': '2017-08-08'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/cars/search-circle',
  params: {
  'latitude' => 'number',
'longitude' => 'number',
'radius' => 'integer',
'pick_up' => 'string',
'drop_off' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/cars/search-circle?latitude=35.1504&longitude=-114.57632&radius=42&pick_up=2017-08-07&drop_off=2017-08-08");
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

`GET /cars/search-circle`

*Car Rental Geosearch - Locate car rental providers and available vehicles when you define a circular area with one coordinate and radius, as well as the pick-up and drop-off dates. Optional parameters such as currency and rental provider codes are also available and can be used to narrow down the results. This API is an ideal pairing with the flight and hotel search to provide ground transportation options at the destination.*

<p>With this API you can find out the price and type of car, for all car rental providers, in a specified geographical location.</p>

<p>You can quickly see the locations of car providers near a given point, and what cars are available to rent, and at what prices. This API is based on our car pricing service that gets live availability from car providers, and is used to power a variety of airline and travel agency websites.</p>
           
<p>Results are validated from car providers, and thus response times may take up to 10 seconds (response times are typically about 5s), and the number of concurrent calls is throttled per user to avoid flooding our provider's systems. However, this means the final result is guaranteed to be live and accurate.</p>

<p>The configuration of this API allows search for car rentals in the rental location where the car is picked up (at the start of the rental), is the same as the one where it will be dropped off. </p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
latitude|query|number|true|Latitude of the center of the search.
longitude|query|number|true|Longitude of the center of the search.
radius|query|integer|true|Radius around the center to look for hotels in kilometers (km).
pick_up|query|string|true|Date on which the car rental will be collected from the car rental location. If no time is provided, a default value of 09:00 is used. Past availability is not displayed, future availability becomes less useful from about 6 months from the current date.
drop_off|query|string|true|Date at which the car rental will end and the car will be returned to the rental location. If no time is provided, a default value of 17:00 is used.
lang|query|string|false|The preferred language of the content related to each car rental. Content will be returned in this language if available.
currency|query|string|false|The preferred <a href="https://en.wikipedia.org/wiki/ISO_4217">currency</a> to use when displaying prices and rates related to the car rental.
provider|query|string|false|2 character car rental provider code. You may provide this parameter more than once. 
rate_class|query|string|false|Allows to request specific rate types.
rate_plan|query|string|false|Qualifies the rate depending on the pickup date and the rental duration.
rate_filter|query|string|false|Defines the types of rates to be returned in the output
vehicle|query|array[string]|false|Specifies the type of vehicle to be rented. If selected, the results set will include only vehicles that match these type descriptions. The enumerations above correspond to ACRISS Pseudo Codes, and you may also provide an ACRISS pseudo code directly. If specifying a vehicle-specific ACRISS code, you may provide this parameter up to 3 times.


#### Enumerated Values

|Parameter|Value|
|---|---|
rate_filter|AVAILABLE|
rate_filter|ESTIMATED|
rate_filter|ALL|

> Example responses

```json
{
  "results": [
    {
      "airport": "string",
      "cars": [
        {
          "estimated_total": {
            "amount": "string",
            "currency": "string"
          },
          "images": [
            {
              "category": "string",
              "height": 0,
              "url": "string",
              "width": 0
            }
          ],
          "rates": [
            {
              "price": {
                "amount": "string",
                "currency": "string"
              },
              "type": "string"
            }
          ],
          "vehicle_info": {
            "acriss_code": "string",
            "air_conditioning": true,
            "category": "string",
            "fuel": "string",
            "transmission": "string",
            "type": "string"
          }
        }
      ],
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "provider": {
        "company_code": "string",
        "company_name": "string"
      }
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[CarSearchResponse](#schemacarsearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Flight Affiliate Search

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/flights/affiliate-search?origin=LON&destination=DUB&departure_date=2017-08-25 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/flights/affiliate-search?origin=LON&destination=DUB&departure_date=2017-08-25 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/flights/affiliate-search',
  method: 'get',
  data: '?origin=LON&destination=DUB&departure_date=2017-08-25',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/flights/affiliate-search', params={
  'origin': 'LON',  'destination': 'DUB',  'departure_date': '2017-08-25'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/flights/affiliate-search',
  params: {
  'origin' => 'string',
'destination' => 'string',
'departure_date' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/flights/affiliate-search?origin=LON&destination=DUB&departure_date=2017-08-25");
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

`GET /flights/affiliate-search`

*Flight Affiliate Search - Use Travel Audience Connect's affiliate network API to search flights from our list of partners and provides deep-links to allow the user to book directly on the airline website.*

<p>The Flight Affiliate Search API combines Amadeus' flight search technology with Travel Audience's Connect API partners to provide a unique flight search, where all results come with deep-links to book the flight at a partner's website. The API will let you easily provide the traveler with a path to book flights from your application.</p>
<p>Travel Audience Connect partners include
<ul>
  <li><a href="http://www.cityjet.com/">CityJet</a>, <a href="https://www.aireuropa.com/en/flights">Air Europa</a> and <a href="http://www.flytap.com/">TAP</a> in Western Europe,</li>
  <li><a href="http://uralairlines.com/">Ural Airlines</a> in Russia, </li>
  <li><a href="http://www.avianca.com.br/">Avianca Brazil</a>  and</li>
  <li><a href="http://www.jal.com/">JAL</a> in East Asia</li>
</ul>
</p>
<p>Only Travel Audience Connect partner airlines are searched. For an up-to-date list of routes, see the route maps on each partners respective websites above. You can earn commission using the deep links provided in the search results if you sign up for an account at <a href="http://connect.travelaudience.com/">connect.travelaudience.com</a>.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
origin|query|string|true|City code from which the traveler will depart. See the location and airport interfaces for more information.
destination|query|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city to which the traveler is going
departure_date|query|string|true|The date on which the traveler will depart from the origin to go to the destination. The maximum scope for a date range is 2 days, for a larger scope, use the Extensive Search! 
return_date|query|string|false|The date on which the traveler will depart from the destination to return to the origin. If this parameter is not specified, the search will find only one-way trips. If this, or the return_by parameter are specified, only return trips are found
adults|query|integer|false|The number of adult (age 12 and over) passengers traveling on this flight.
children|query|integer|false|The number of child (younger than age 12 on date of departure) passengers traveling on this flight who will each have their own separate seat
infants|query|integer|false|The number of infant (younger than age 2 on date of departure) passengers traveling on this flight. Infants travel in the lap of an adult passenger, and thus the number of infants must not exceed the number of adults.
include_merchants|query|array[string]|false|If specified, all results will include at least one flight where one or more of these airlines is the marketing carrier. Airlines are specified using <a href="https://en.wikipedia.org/wiki/Airline_codes"><a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a>s</a>
exclude_merchants|query|array[string]|false|If specified, no results will include any flights where any of these airlines is the marketing carrier. Airlines are specified using <a href="https://en.wikipedia.org/wiki/Airline_codes"><a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a>s</a>
max_price|query|integer|false|Maximum price of trips to find in the result set, in USD (US dollars) unless some other currency code is specified. By default, no limit is applied
currency|query|string|false|The preferred <a href="https://en.wikipedia.org/wiki/ISO_4217">currency</a> for the results
mobile|query|boolean|false|Setting this to true will show mobile web deeplinks 


> Example responses

```json
{
  "meta": {
    "carriers": {
      "property1": {
        "logos": {
          "medium": "string",
          "small": "string"
        },
        "name": "string"
      },
      "property2": {
        "logos": {
          "medium": "string",
          "small": "string"
        },
        "name": "string"
      }
    }
  },
  "results": [
    {
      "airline": "string",
      "deep_link": "string",
      "fare": {
        "currency": "string",
        "price_per_adult": {
          "tax": "string",
          "total_fare": "string"
        },
        "price_per_child": {
          "tax": "string",
          "total_fare": "string"
        },
        "price_per_infant": {
          "tax": "string",
          "total_fare": "string"
        },
        "restrictions": {
          "change_penalties": true,
          "refundable": true
        },
        "total_price": "string"
      },
      "inbound": {
        "duration": "string",
        "flights": [
          {
            "aircraft": "string",
            "arrives_at": "string",
            "booking_info": {
              "booking_code": "string",
              "cabin_code": "string",
              "fare_basis": "string",
              "fare_family": "string",
              "seats_remaining": "string",
              "travel_class": "string"
            },
            "departs_at": "string",
            "destination": {
              "airport": "string",
              "terminal": "string"
            },
            "flight_number": "string",
            "marketing_airline": "string",
            "operating_airline": "string",
            "origin": {
              "airport": "string",
              "terminal": "string"
            }
          }
        ]
      },
      "outbound": {
        "duration": "string",
        "flights": [
          {
            "aircraft": "string",
            "arrives_at": "string",
            "booking_info": {
              "booking_code": "string",
              "cabin_code": "string",
              "fare_basis": "string",
              "fare_family": "string",
              "seats_remaining": "string",
              "travel_class": "string"
            },
            "departs_at": "string",
            "destination": {
              "airport": "string",
              "terminal": "string"
            },
            "flight_number": "string",
            "marketing_airline": "string",
            "operating_airline": "string",
            "origin": {
              "airport": "string",
              "terminal": "string"
            }
          }
        ]
      },
      "payout": {
        "CPA": {
          "amount": "string",
          "currency": "string"
        },
        "CPC": {
          "amount": "string",
          "currency": "string"
        },
        "CPS": {
          "amount": "string",
          "currency": "string"
        }
      }
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[AffiliateSearchResponse](#schemaaffiliatesearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Flight Extensive Search

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/flights/extensive-search?origin=FRA&destination=LON \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/flights/extensive-search?origin=FRA&destination=LON HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/flights/extensive-search',
  method: 'get',
  data: '?origin=FRA&destination=LON',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/flights/extensive-search', params={
  'origin': 'FRA',  'destination': 'LON'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/flights/extensive-search',
  params: {
  'origin' => 'string',
'destination' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/flights/extensive-search?origin=FRA&destination=LON");
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

`GET /flights/extensive-search`

*Flight Extensive Search - Build travel searches based on very flexible and open range of dates. You can use it to answer questions such as "When is the best date to fly...".  It's built on Amadeus' Featured Results technology, which returns thousands of results (prices, itineraries and dates) in a matter of milliseconds. Results are available over half a calendar year with a 1 to 15 day stay duration*

<p>The Extensive Flight Search allows you to find the prices of one-way or return flights between two airports over a large number of dates, and for a large variety of stay durations. The search doesn't return exact itineraries, but rather tells you the best price for a flight on a given day, for a stay of a given duration.</p>

<p>The search is based on our Extreme Search platform, which continually caches a large number of flight search results from a list of origin cities to a variety of destinations. Since it's a cached search, the response time is fast, but not all origin airports are available. Here is <a href="https://github.com/amadeus-travel-innovation-sandbox/sandbox-content/blob/master/flight-search-cache-origin-destination.csv">a list of the currently supported origin-destination IATA location pairs</a>. We try to keep this list as fresh as possible for you, but be aware that it may not always be exactly up-to-date and it can change without warning.</p>

<p>That said, a price graph like this provides a powerful bargin shopping tool - allowing travelers with flexible itineraries to identify days on which they can get the cheapest flights to their destinations.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
origin|query|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city from which the traveler will depart. See the location and airport interfaces for more information.
destination|query|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city to which the traveler is going
departure_date|query|string|false|Range of dates between which the traveler could depart. Dates are specified in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> yyyy-MM-dd date format. Ranges are inclusive and ranges of months will apply from the start to the end of the month. If just a single date is specified, only that date will be searched. By default, the date range starts today and applies up to 361 in the future is applied. Past dates are generally not supported, future dates should be in the next 361 days, although results start to become sparse after about 6 months in the future, as airlines may still be defining their schedules. The default is to search all future dates available. 
one-way|query|boolean|false|When set to true, the query will be for a single trip from the origin to the destination. When this parameter is not provided, or is set to false, the query is for a round trip from the origin to the destination and back again.
duration|query|string|false|The allowed duration or range of durations of the trip, in days. This parameter must not be set if the one-way parameter is set to true.
direct|query|boolean|false|Limit the search to results that do not require the passenger to change plane?
max_price|query|string|false|Maximum price of trips to find in the result set, in the currency specified for this origin and destination pair in the cache contents spreadsheet. So, for example, if the origin is NYC, and the max price is 400, this means 400 USD. If the origin is PAR, and the max price is 400, this means 400 EUR. By default, no limit is applied
aggregation_mode|query|string|false|Specifies the granularity of results to be found. DAY is the default when one-way is true finds a result for departure date in the date range. STAY is the default otherwise and finds all round trip permutations for this route withim the given date range. DESTINATION finds one result, only the cheapest price for this route over the provided date range. WEEK finds the cheapest result for every week in the date range. Note that specifying a small granularity but a large search scope may result in a huge output. For some very large outputs, the API may refuse to provide a result.


> Example responses

```json
{
  "currency": "string",
  "origin": "string",
  "results": [
    {
      "airline": "string",
      "departure_date": "2017-10-04",
      "destination": "string",
      "price": "string",
      "return_date": "2017-10-04"
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[ExtremeSearchResponse](#schemaextremesearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Flight Inspiration Search

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/flights/inspiration-search?origin=NYC \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/flights/inspiration-search?origin=NYC HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/flights/inspiration-search',
  method: 'get',
  data: '?origin=NYC',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/flights/inspiration-search', params={
  'origin': 'NYC'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/flights/inspiration-search',
  params: {
  'origin' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/flights/inspiration-search?origin=NYC");
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

`GET /flights/inspiration-search`

*Flight Inspiration Search - Go beyond the traditional search by origin, destination and dates to meet the needs of travelers looking for suggestions and a search experience that reflects the way they choose their trip. This can help you answer the question "Where can I go within a given travel budget?"*

<p>The Inspiration Flight Search allows you to find the prices of one-way and return flights from an origin city without necessarily having a destination, or even a flight date, in mind. The search doesn't return a distinct set of price options, but rather, can tell you the price of flying from a given city to some destination, for a trip of a given duration, that falls within a given date range.</p>

<p>The search is based on our Extreme Search platform, which continually caches a large number of flight search results from a list of origin cities to a variety of destinations. Since it's a cached search, the response time is fast, but not all origin airports are available. Here is <a href="https://github.com/amadeus-travel-innovation-sandbox/sandbox-content/blob/master/flight-search-cache-origin-destination.csv">a list of the currently supported origin-destination IATA location pairs</a>. We try to keep this list as fresh as possible for you, but be aware that it may not always be exactly up-to-date and it can change without warning.</p>

<p>Despite this limitation don't underestimate the power of this API. Thanks to its quick response speed you can easily pair it with other APIs to provide a low fare and inspiration for any destination. For example, you can could combine it with a event search API and suggest a total price to see go and see an concert or a game in a selection of cities.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
origin|query|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city from which the traveler will depart. See the location and airport interfaces for more information.
destination|query|string|false|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city to which the traveler is going
departure_date|query|string|false|Range of dates between which the traveler could depart. Dates are specified in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> yyyy-MM-dd date format. Ranges are inclusive and ranges of months will apply from the start to the end of the month. If just a single date is specified, only that date will be searched. By default, the date range starts today and applies up to 361 in the future is applied. Past dates are generally not supported, future dates should be in the next 361 days, although results start to become sparse after about 6 months in the future, as airlines may still be defining their schedules. The default is to search all future dates available.
one-way|query|boolean|false|When set to true, the query will be for a single trip from the origin to the destination. When this parameter is not provided, or is set to false, the query is for a round trip from the origin to the destination and back again.
duration|query|string|false|The allowed duration or range of durations of the trip, in days. This parameter must not be set if the one-way parameter is set to true.
direct|query|boolean|false|Limit the search to results that do not require the passenger to change plane?
max_price|query|string(Integer)|false|Maximum price of trips to find in the result set, in the currency specified for this origin and destination pair in the cache contents spreadsheet. So, for example, if the origin is NYC, and the max price is 400, this means 400 USD. If the origin is PAR, and the max price is 400, this means 400 EUR. By default, no limit is applied
aggregation_mode|query|string|false|Specifies the granularity of results to be found. DESTINATION is the default and finds one result per city. COUNTRY finds one result per country, DAY finds on result for every day in the date range, WEEK finds one result for every week in the date range. Note that specifying a small granularity but a large search scope may result in a huge output. For some very large outputs, the API may refuse to provide a result.


> Example responses

```json
{
  "currency": "string",
  "origin": "string",
  "results": [
    {
      "airline": "string",
      "departure_date": "2017-10-04",
      "destination": "string",
      "price": "string",
      "return_date": "2017-10-04"
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[ExtremeSearchResponse](#schemaextremesearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Flight Low-Fare Search

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/flights/low-fare-search?origin=BOS&destination=LON&departure_date=2017-08-25 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/flights/low-fare-search?origin=BOS&destination=LON&departure_date=2017-08-25 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/flights/low-fare-search',
  method: 'get',
  data: '?origin=BOS&destination=LON&departure_date=2017-08-25',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/flights/low-fare-search', params={
  'origin': 'BOS',  'destination': 'LON',  'departure_date': '2017-08-25'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/flights/low-fare-search',
  params: {
  'origin' => 'string',
'destination' => 'string',
'departure_date' => 'string(string)'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/flights/low-fare-search?origin=BOS&destination=LON&departure_date=2017-08-25");
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

`GET /flights/low-fare-search`

*Flight Low-Fare Search - Find the cheapest one way or return itineraries and fares between two airports at specific dates.*

<p>This is the low fare search engine Amadeus uses to retrieve the best price for flights, based on our latest Master Pricer Travel Board technology. This document describes how to make a low fare search and how to handle the returned messages.</p>

<p>The message is composed of multiple results for given request. A result is defined by a unique combination of price, tax, passenger type, fare type, cabin, and availability for each requested segment.</p> 

<p>A result is then composed of single or multiple itineraries. Each itinerary is composed of an outbound leg, and, if a return date was specified, an inbound leg. Each leg is composed of a list of one or more flights, that the traveller will be required to take in order to get from the origin airport to the destination airport.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
origin|query|string|true|City code from which the traveler will depart. See the location and airport interfaces for more information.
destination|query|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city to which the traveler is going
departure_date|query|string(string)|true|The date on which the traveler will depart from the origin to go to the destination. You can specify a date range of up to 2 days. For a larger date range, use the Extensive Search. Dates are specified in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> yyyy-MM-dd date format and separated by --.
return_date|query|string|false|The date on which the traveler will depart from the destination to return to the origin. If this parameter is not specified, the search will find only one-way trips. If this, or the return_by parameter are specified, only return trips are found. You can specify a date range of up to 2 days.
arrive_by|query|string|false|The datetime by which the outbound flight should arrive, based on local time at the destination airport.  Date-times are specified in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> yyyy-MM-ddTHH:mm date format
return_by|query|string|false|The time by which the inbound flight should arrive, based on local time at the airport specified as the origin parameter
adults|query|integer|false|The number of adult (age 12 and over) passengers traveling on this flight.
children|query|integer|false|The number of child (younger than age 12 on date of departure) passengers traveling on this flight who will each have their own separate seat
infants|query|integer|false|The number of infant (younger than age 2 on date of departure) passengers traveling on this flight. Infants travel in the lap of an adult passenger, and thus the number of infants must not exceed the number of adults.
include_airlines|query|array[string]|false|If specified, all results will include at least one flight where one or more of these airlines is the marketing carrier. This behaves as an OR function. Airlines are specified using <a href="https://en.wikipedia.org/wiki/Airline_codes"><a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a>s</a>.
exclude_airlines|query|array[string]|false|If specified, no results will include any flights where any of these airlines is the marketing carrier. Airlines are specified using <a href="https://en.wikipedia.org/wiki/Airline_codes"><a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a>s</a>.
nonstop|query|boolean|false|Setting this to true will find only flights that do not require the passenger to change from one flight to another
max_price|query|integer|false|Maximum price of trips to find in the result set, in USD (US dollars) unless some other currency code is specified. By default, no limit is applied
currency|query|string|false|The preferred <a href="https://en.wikipedia.org/wiki/ISO_4217">currency</a> for the results
travel_class|query|string|false|Searches for results where the majority of the itinerary flight time should be in a the specified cabin class or higher
number_of_results|query|integer|false|The number of results to display. This will not be strictly interpreted but used as a guideline to display a useful number of results. By default, the number of results is dynamically determined. A maximum of 250 results will be displayed.


> Example responses

```json
{
  "currency": "string",
  "results": [
    {
      "fare": {
        "price_per_adult": {
          "tax": "string",
          "total_fare": "string"
        },
        "price_per_child": {
          "tax": "string",
          "total_fare": "string"
        },
        "price_per_infant": {
          "tax": "string",
          "total_fare": "string"
        },
        "restrictions": {
          "change_penalties": true,
          "refundable": true
        },
        "total_price": "string"
      },
      "itineraries": [
        {
          "inbound": {
            "duration": "string",
            "flights": [
              {
                "aircraft": "string",
                "arrives_at": "string",
                "booking_info": {
                  "booking_code": "string",
                  "cabin_code": "string",
                  "fare_basis": "string",
                  "fare_family": "string",
                  "seats_remaining": "string",
                  "travel_class": "string"
                },
                "departs_at": "string",
                "destination": {
                  "airport": "string",
                  "terminal": "string"
                },
                "flight_number": "string",
                "marketing_airline": "string",
                "operating_airline": "string",
                "origin": {
                  "airport": "string",
                  "terminal": "string"
                }
              }
            ]
          },
          "outbound": {
            "duration": "string",
            "flights": [
              {
                "aircraft": "string",
                "arrives_at": "string",
                "booking_info": {
                  "booking_code": "string",
                  "cabin_code": "string",
                  "fare_basis": "string",
                  "fare_family": "string",
                  "seats_remaining": "string",
                  "travel_class": "string"
                },
                "departs_at": "string",
                "destination": {
                  "airport": "string",
                  "terminal": "string"
                },
                "flight_number": "string",
                "marketing_airline": "string",
                "operating_airline": "string",
                "origin": {
                  "airport": "string",
                  "terminal": "string"
                }
              }
            ]
          }
        }
      ]
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[LowFareSearchResponse](#schemalowfaresearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Hotel Airport Search

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/hotels/search-airport?location=BOS&check_in=2017-08-15&check_out=2017-08-16 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/hotels/search-airport?location=BOS&check_in=2017-08-15&check_out=2017-08-16 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/hotels/search-airport',
  method: 'get',
  data: '?location=BOS&check_in=2017-08-15&check_out=2017-08-16',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/hotels/search-airport', params={
  'location': 'BOS',  'check_in': '2017-08-15',  'check_out': '2017-08-16'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/hotels/search-airport',
  params: {
  'location' => 'string',
'check_in' => 'string',
'check_out' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/hotels/search-airport?location=BOS&check_in=2017-08-15&check_out=2017-08-16");
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

`GET /hotels/search-airport`

*Hotel Airport Search - Locate the cheapest available rooms near a given airport, for a given stay period. This API is ideal if you want to connect flight and hotels. Provide an IATA airport code, as well as the check-in and check-out dates, and get a list of up to 140 properties (names, codes, image, amenities) with their locations and rates. Optional parameters such as currency and maximum rates, amenities or hotel chain codes are also available and can be used to narrow down the results. More optional parameters such as show_sold_out & rooms can be used to show sold out rooms and all available rooms.*

<p>A fast Hotel shopping API to see which hotels are available in a given area, on a given day and displays their lowest prices. With this API you can find out the price of the cheapest daily rate for all hotels near a given airport.</p>

<p>This API allows you to quickly see the locations of hotels near a given airport, and what prices in that area look like. Note that hotel images are not available to users outside of Amadeus, as we are not licensed to redistribute them. The API is based on our high-speed hotel pricing cache, which is also used to power the <a href="https://hotelsearchengine.amadeus.com/">Amadeus Hotel Search Engine</a> application. Results are returned very quickly, response times are generally under 2s. Our cache has great global coverage and is constantly refreshed with the latest prices.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
location|query|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> for hotel availability is required requested.
check_in|query|string|true|Date on which the guest will begin their stay in the hotel. Past availability is not displayed, future availability becomes less useful from about 6 months from the current date.
check_out|query|string|true|Date on which the guest will end their stay in the hotel.
radius|query|integer|false|Radius around the center to look for hotels in kilometers (km).
lang|query|string|false|The preferred language of the content related to each hotel. Content will be returned in this language if available.
currency|query|string|false|The preferred <a href="https://en.wikipedia.org/wiki/ISO_4217">currency</a> for the results
chain|query|string|false|Narrows the hotel search to a given hotel provider. The hotel chain is indicated by the first two characters of the property code.
max_rate|query|number|false|The maximum amount per night that any hotel in the shopping response should cost. This is calculated by dividing the total price of the stay for the given dates by the number of nights specified falling between the check_in and check_out dates.
number_of_results|query|integer|false|The maximum number of hotels to return in the results set. Hotels are ordered by total price, so if more than the given maximum number of hotels are available, only the cheapest options are returned.
all_rooms|query|boolean|false|This option if enabled will return all hotel room rates, not just the lowest room rate. Note: This will have an impact on the response time due to the larger messages returned.
show_sold_out|query|boolean|false|This option if enabled will return hotel names and addresses even if rooms are sold out (closed properties)
amenity|query|array[string]|false|Hotel <a href="hotels-api-supported-amenities-filter">amenities filter</a> to search narrow down hotels with certain amenities. For example&colon; amenity=POOL. (Note: multiple amenities can be used in searches: amenity=PARKING&amenity=RESTAURANT&amenity=PETS_ALLOWED).


> Example responses

```json
{
  "results": [
    {
      "address": {
        "city": "string",
        "country": "string",
        "line1": "string",
        "postal_code": "string",
        "region": "string"
      },
      "amenities": [
        {
          "amenity": "string",
          "description": "string",
          "ota_code": "string"
        }
      ],
      "awards": [
        {
          "provider": "string",
          "rating": "string"
        }
      ],
      "contacts": [
        {
          "detail": "string",
          "purpose": "string",
          "type": "string"
        }
      ],
      "images": [
        {
          "category": "string",
          "height": 0,
          "url": "string",
          "width": 0
        }
      ],
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "min_daily_rate": {
        "amount": "string",
        "currency": "string"
      },
      "more_rooms_at_this_hotel": {
        "href": "string"
      },
      "property_code": "string",
      "property_name": "string",
      "rooms": [
        {
          "booking_code": "string",
          "descriptions": [
            "string"
          ],
          "rate_plan_code": "string",
          "rate_type_code": "string",
          "rates": [
            {
              "currency": "string",
              "end_date": "2017-10-04",
              "price": 0,
              "start_date": "2017-10-04"
            }
          ],
          "room_type_code": "string",
          "room_type_info": {
            "bed_type": "string",
            "number_of_beds": "string",
            "room_type": "string"
          },
          "total_amount": {
            "amount": "string",
            "currency": "string"
          }
        }
      ],
      "total_price": {
        "amount": "string",
        "currency": "string"
      }
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[HotelSearchResponse](#schemahotelsearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Hotel Geosearch by box

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/hotels/search-box?south_west_corner=38.8675%2C-77.1457&north_east_corner=38.9072%2C-77.0632&check_in=2017-08-15&check_out=2017-08-16 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/hotels/search-box?south_west_corner=38.8675%2C-77.1457&north_east_corner=38.9072%2C-77.0632&check_in=2017-08-15&check_out=2017-08-16 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/hotels/search-box',
  method: 'get',
  data: '?south_west_corner=38.8675%2C-77.1457&north_east_corner=38.9072%2C-77.0632&check_in=2017-08-15&check_out=2017-08-16',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/hotels/search-box', params={
  'south_west_corner': '38.8675,-77.1457',  'north_east_corner': '38.9072,-77.0632',  'check_in': '2017-08-15',  'check_out': '2017-08-16'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/hotels/search-box',
  params: {
  'south_west_corner' => 'string',
'north_east_corner' => 'string',
'check_in' => 'string',
'check_out' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/hotels/search-box?south_west_corner=38.8675%2C-77.1457&north_east_corner=38.9072%2C-77.0632&check_in=2017-08-15&check_out=2017-08-16");
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

`GET /hotels/search-box`

*Hotel Geosearch by box - Locate the cheapest available rooms within a given rectangular region for a given stay period. It's ideal for displaying results on a map.*

<p>A fast Hotel shopping API to see which hotels are available in a given area, on a given day and displays their lowest prices. With this API you can find out the price of the cheapest daily rate for all hotels within a specified geographical region.</p>

<p>This API allows you to quickly see the hotel locations in a region, and what prices in that area look like,  as well as the check-in and check-out dates, and get a list of up to 140 properties (names, codes, image, amenities) with their locations and rates. Optional parameters such as currency and maximum rates, amenities or hotel chain codes are also available and can be used to narrow down the results. More optional parameters such as show_sold_out & rooms can be used to show sold out rooms and all available rooms.</p>
            
<p>The API is based on our high-speed hotel pricing cache, which is also used to power the <a href="https://hotelsearchengine.amadeus.com/">Amadeus Hotel Search Engine</a> application. Results are returned very quickly, response times are generally under 2s. Our cache has great global coverage and is constantly refreshed with the latest prices.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
south_west_corner|query|string|true|The coordinates of the south-west corner of the search box.
north_east_corner|query|string|true|The coordinates of the north-east corner of the search box.
check_in|query|string|true|Date on which the guest will begin their stay in the hotel. Past availability is not displayed, future availability becomes less useful from about 6 months from the current date.
check_out|query|string|true|Date on which the guest will end their stay in the hotel.
lang|query|string|false|The preferred language of the content related to each hotel. Content will be returned in this language if available.
currency|query|string|false|The preferred <a href="https://en.wikipedia.org/wiki/ISO_4217">currency</a> for the results
chain|query|string|false|Narrows the hotel search to a given hotel provider. The hotel chain is indicated by the first two characters of the property code.
max_rate|query|number|false|The maximum amount per night that any hotel in the shopping response should cost. This is calculated by dividing the total price of the stay for the given dates by the number of nights specified falling between the check_in and check_out dates.
number_of_results|query|integer|false|The maximum number of hotels to return in the results set. Hotels are ordered by total price, so if more than the given maximum number of hotels are available, only the cheapest options are returned.
all_rooms|query|boolean|false|This option if enabled will return all hotel room rates, not just the lowest room rate. Note: This will have an impact on the response time due to the larger messages returned.
show_sold_out|query|boolean|false|This option if enabled will return hotel names and addresses even if rooms are sold out (closed properties)
amenity|query|array[string]|false|Hotel <a href="hotels-api-supported-amenities-filter">amenities filter</a> to search narrow down hotels with certain amenities. For example&colon; amenity=POOL. (Note: multiple amenities can be used in searches: amenity=PARKING&amenity=RESTAURANT&amenity=PETS_ALLOWED).


> Example responses

```json
{
  "results": [
    {
      "address": {
        "city": "string",
        "country": "string",
        "line1": "string",
        "postal_code": "string",
        "region": "string"
      },
      "amenities": [
        {
          "amenity": "string",
          "description": "string",
          "ota_code": "string"
        }
      ],
      "awards": [
        {
          "provider": "string",
          "rating": "string"
        }
      ],
      "contacts": [
        {
          "detail": "string",
          "purpose": "string",
          "type": "string"
        }
      ],
      "images": [
        {
          "category": "string",
          "height": 0,
          "url": "string",
          "width": 0
        }
      ],
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "min_daily_rate": {
        "amount": "string",
        "currency": "string"
      },
      "more_rooms_at_this_hotel": {
        "href": "string"
      },
      "property_code": "string",
      "property_name": "string",
      "rooms": [
        {
          "booking_code": "string",
          "descriptions": [
            "string"
          ],
          "rate_plan_code": "string",
          "rate_type_code": "string",
          "rates": [
            {
              "currency": "string",
              "end_date": "2017-10-04",
              "price": 0,
              "start_date": "2017-10-04"
            }
          ],
          "room_type_code": "string",
          "room_type_info": {
            "bed_type": "string",
            "number_of_beds": "string",
            "room_type": "string"
          },
          "total_amount": {
            "amount": "string",
            "currency": "string"
          }
        }
      ],
      "total_price": {
        "amount": "string",
        "currency": "string"
      }
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[HotelSearchResponse](#schemahotelsearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Hotel Geosearch by circle

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/hotels/search-circle?latitude=36.0857&longitude=-115.1541&radius=42&check_in=2017-08-15&check_out=2017-08-16 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/hotels/search-circle?latitude=36.0857&longitude=-115.1541&radius=42&check_in=2017-08-15&check_out=2017-08-16 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/hotels/search-circle',
  method: 'get',
  data: '?latitude=36.0857&longitude=-115.1541&radius=42&check_in=2017-08-15&check_out=2017-08-16',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/hotels/search-circle', params={
  'latitude': 36.0857,  'longitude': -115.1541,  'radius': 42,  'check_in': '2017-08-15',  'check_out': '2017-08-16'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/hotels/search-circle',
  params: {
  'latitude' => 'number',
'longitude' => 'number',
'radius' => 'integer',
'check_in' => 'string',
'check_out' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/hotels/search-circle?latitude=36.0857&longitude=-115.1541&radius=42&check_in=2017-08-15&check_out=2017-08-16");
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

`GET /hotels/search-circle`

*Hotel Geosearch by Circle API - Locate the cheapest available rooms within a given radius of a defined point for a given stay period.*

<p>A fast Hotel shopping API to see which hotels are available in a given area, on a given day and displays their lowest prices. With this API you can find out the price of the cheapest daily rate for all hotels within a specified radius of a point.</p>

<p>This API allows you to quickly see the hotel locations in a region, and what prices in that area look like,  as well as the check-in and check-out dates, and get list of up to 140 properties (names, codes, image, amenities) with their locations and rates. Optional parameters such as currency and maximum rates, amenities or hotel chain codes are also available and can be used to narrow down the results. More optional parameters such as show_sold_out & rooms can be used to show sold out rooms and all available rooms. </p>

<p>The API is based on our high-speed hotel pricing cache, which is also used to power the <a href="https://hotelsearchengine.amadeus.com/">Amadeus Hotel Search Engine</a> application. Results are returned very quickly, response times are generally under 2s. Our cache has great global coverage and is constantly refreshed with the latest prices.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
latitude|query|number|true|Latitude of the center of the search.
longitude|query|number|true|Longitude of the center of the search.
radius|query|integer|true|Radius around the center to look for hotels in kilometers (km).
check_in|query|string|true|Date on which the guest will begin their stay in the hotel. Past availability is not displayed, future availability becomes less useful from about 6 months from the current date.
check_out|query|string|true|Date on which the guest will end their stay in the hotel.
lang|query|string|false|The preferred language of the content related to each hotel. Content will be returned in this language if available.
currency|query|string|false|The preferred <a href="https://en.wikipedia.org/wiki/ISO_4217">currency</a> for the results
chain|query|string|false|Narrows the hotel search to a given hotel provider. The hotel chain is indicated by the first two characters of the property code.
max_rate|query|number|false|The maximum amount per night that any hotel in the shopping response should cost. This is calculated by dividing the total price of the stay for the given dates by the number of nights specified falling between the check_in and check_out dates.
number_of_results|query|integer|false|The maximum number of hotels to return in the results set. Hotels are ordered by total price, so if more than the given maximum number of hotels are available, only the cheapest options are returned.
all_rooms|query|boolean|false|This option if enabled will return all hotel room rates, not just the lowest room rate. Note: This will have an impact on the response time due to the larger messages returned.
show_sold_out|query|boolean|false|This option if enabled will return hotel names and addresses even if rooms are sold out (closed properties)
amenity|query|array[string]|false|Hotel <a href="hotels-api-supported-amenities-filter">amenities filter</a> to search narrow down hotels with certain amenities. For example&colon; amenity=POOL. (Note: multiple amenities can be used in searches: amenity=PARKING&amenity=RESTAURANT&amenity=PETS_ALLOWED).


> Example responses

```json
{
  "results": [
    {
      "address": {
        "city": "string",
        "country": "string",
        "line1": "string",
        "postal_code": "string",
        "region": "string"
      },
      "amenities": [
        {
          "amenity": "string",
          "description": "string",
          "ota_code": "string"
        }
      ],
      "awards": [
        {
          "provider": "string",
          "rating": "string"
        }
      ],
      "contacts": [
        {
          "detail": "string",
          "purpose": "string",
          "type": "string"
        }
      ],
      "images": [
        {
          "category": "string",
          "height": 0,
          "url": "string",
          "width": 0
        }
      ],
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "min_daily_rate": {
        "amount": "string",
        "currency": "string"
      },
      "more_rooms_at_this_hotel": {
        "href": "string"
      },
      "property_code": "string",
      "property_name": "string",
      "rooms": [
        {
          "booking_code": "string",
          "descriptions": [
            "string"
          ],
          "rate_plan_code": "string",
          "rate_type_code": "string",
          "rates": [
            {
              "currency": "string",
              "end_date": "2017-10-04",
              "price": 0,
              "start_date": "2017-10-04"
            }
          ],
          "room_type_code": "string",
          "room_type_info": {
            "bed_type": "string",
            "number_of_beds": "string",
            "room_type": "string"
          },
          "total_amount": {
            "amount": "string",
            "currency": "string"
          }
        }
      ],
      "total_price": {
        "amount": "string",
        "currency": "string"
      }
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[HotelSearchResponse](#schemahotelsearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Hotel Property Code Search

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/hotels/{property_code}?check_in=2017-08-14&check_out=2017-08-15 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/hotels/{property_code}?check_in=2017-08-14&check_out=2017-08-15 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/hotels/{property_code}',
  method: 'get',
  data: '?check_in=2017-08-14&check_out=2017-08-15',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/hotels/{property_code}', params={
  'check_in': '2017-08-14',  'check_out': '2017-08-15'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/hotels/{property_code}',
  params: {
  'check_in' => 'string',
'check_out' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/hotels/{property_code}?check_in=2017-08-14&check_out=2017-08-15");
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

`GET /hotels/{property_code}`

*Hotel Property Code Search - Find out more room and rate information once you have found your preferred hotel.*

<p>This API allows you to quickly see the detailed information of a single hotel, including descriptions, address, GPS location, amenities, awards, lowest priced room and all room prices and booking information. </p>

<p>This API gives you more information on a specific property. Optional parameters such as show_sold_out & rooms can be used to show sold out rooms and all available rooms. </p>

<p>The API is based on our high-speed hotel pricing cache, which is also used to power the <a href="https://hotelsearchengine.amadeus.com/">Amadeus Hotel Search Engine</a> application. Results are returned very quickly, response times are generally under 2s. Our cache has great global coverage and is constantly refreshed with the latest prices.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
property_code|path|string|true|A Hotel property code based on 2 letter chain code + 3 letter <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city + 3 char property unique id.
check_in|query|string|true|Date on which the guest will begin their stay in the hotel. Past availability is not displayed, future availability becomes less useful from about 6 months from the current date.
check_out|query|string|true|Date on which the guest will end their stay in the hotel.
lang|query|string|false|The preferred language of the content related to each hotel. Content will be returned in this language if available.
currency|query|string|false|The preferred <a href="https://en.wikipedia.org/wiki/ISO_4217">currency</a> for the results
all_rooms|query|boolean|false|This option if enabled will return all hotel room rates, not just the lowest room rate. Note: This will have an impact on the response time due to the larger messages returned.
show_sold_out|query|boolean|false|This option if enabled will return hotel names and addresses even if rooms are sold out (closed properties)


> Example responses

```json
{
  "address": {
    "city": "string",
    "country": "string",
    "line1": "string",
    "postal_code": "string",
    "region": "string"
  },
  "amenities": [
    {
      "amenity": "string",
      "description": "string",
      "ota_code": "string"
    }
  ],
  "awards": [
    {
      "provider": "string",
      "rating": "string"
    }
  ],
  "contacts": [
    {
      "detail": "string",
      "purpose": "string",
      "type": "string"
    }
  ],
  "images": [
    {
      "category": "string",
      "height": 0,
      "url": "string",
      "width": 0
    }
  ],
  "location": {
    "google_maps_link": "string",
    "latitude": 0,
    "longitude": 0
  },
  "min_daily_rate": {
    "amount": "string",
    "currency": "string"
  },
  "more_rooms_at_this_hotel": {
    "href": "string"
  },
  "property_code": "string",
  "property_name": "string",
  "rooms": [
    {
      "booking_code": "string",
      "descriptions": [
        "string"
      ],
      "rate_plan_code": "string",
      "rate_type_code": "string",
      "rates": [
        {
          "currency": "string",
          "end_date": "2017-10-04",
          "price": 0,
          "start_date": "2017-10-04"
        }
      ],
      "room_type_code": "string",
      "room_type_info": {
        "bed_type": "string",
        "number_of_beds": "string",
        "room_type": "string"
      },
      "total_amount": {
        "amount": "string",
        "currency": "string"
      }
    }
  ],
  "total_price": {
    "amount": "string",
    "currency": "string"
  }
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Lookup Response|[HotelPropertyResponse](#schemahotelpropertyresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Location Information

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/location/{code} \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/location/{code} HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/location/{code}',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/location/{code}', params={

}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/location/{code}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/location/{code}");
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

`GET /location/{code}`

*Location Information - Find more information about any IATA city or airport location code. With this API, you can find information such as city and airport names and locations, as well as information on timezones and airport usage.*

<p>This service retrieves the location information corresponding to a IATA city or airport code.</p>

<p>When provided with an <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a>, the service determines whether this code could relate to a city code, an airport code or both. If the city could contain multiple airports, it will return all possible airports that correspond to that city code.</p>

<p>This API is based on the Amadeus supported <a href="http://opentraveldata.github.io/geobases">Geobases</a> open-source project. If you wish to make your own database with all IATA location information, in order to get faster reponses, you can download the latest raw data from their <a href="https://github.com/opentraveldata/opentraveldata/blob/master/opentraveldata/optd_por_public.csv">github page</a>.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
code|path|string|true|IATA location code for which further information is required


> Example responses

```json
{
  "airports": [
    {
      "aircraft_movements": 0,
      "city_code": "string",
      "city_name": "string",
      "code": "string",
      "country": "string",
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "name": "string",
      "state": "string",
      "timezone": "string"
    }
  ],
  "city": {
    "code": "string",
    "country": "string",
    "currency": "string",
    "geonames_ID": "string",
    "location": {
      "google_maps_link": "string",
      "latitude": 0,
      "longitude": 0
    },
    "name": "string",
    "state": "string",
    "timezone": "string"
  }
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Location lookup Response|[LocationResponse](#schemalocationresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## YapQ Geosearch

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-circle?latitude=35.1504&longitude=-114.57632&radius=42 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-circle?latitude=35.1504&longitude=-114.57632&radius=42 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-circle',
  method: 'get',
  data: '?latitude=35.1504&longitude=-114.57632&radius=42',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-circle', params={
  'latitude': 35.1504,  'longitude': -114.57632,  'radius': 42
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-circle',
  params: {
  'latitude' => 'number',
'longitude' => 'number',
'radius' => 'integer'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-circle?latitude=35.1504&longitude=-114.57632&radius=42");
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

`GET /points-of-interest/yapq-search-circle`

*YapQ Geosearch - Find landmarks and attractions near a given point.*

Amadeus has partnered with <a href="http://yapq.io/">YapQ</a> to bring you point of interest APIs with the goal of offering you unbiased ratings of landmarks and tourist attractions. YapQ rates places according to their interest on social media and provides Wikipedia content and Geonames ID at a given location. <br />
YapQ's service indexes millions of points around the world, and provides content in 12 different languages. This allows you to ensure you catch the <em>must-see</em> sights at a specific <a href="http://yapq.io/cities.html">YapQ supported location</a>.<br />
Each point of interest comes with links to content, grading information, location and directions to help make discovering your destination easy and fun.<br /><br />
This service is still under active development, and the response format may change without warning. We'd be interested in your feedback - <a href="mailto:sandbox@yapq.com">send us an email</a>.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
latitude|query|number|true|Latitude of the center of the search, in decimal degrees
longitude|query|number|true|Longitude of the center of the search, in decimal degrees
radius|query|integer|true|Radius around the center to look for points-of-interest around the given latitude and longitude in kilometers (km)
lang|query|string|false|The preferred language of the content related to each point of interest. Content will be returned in this language if available
category|query|string|false|Filters the resulting points_of_interest to include only results which have a least one category containing the given provided word. Good examples are <em>museum</em>, <em>landmark</em> or <em>church</em>
geonames|query|boolean|false|Setting this to true includes only points of interest with a geonames ID
vibes|query|boolean|false|Includes content that doesn't correspond to an active physical place, but which gives the user some background information, or <em>vibe</em> for the place they are visiting. An example of this may be information on an influential demolished building that used to exist at a certain location, or more information on a district of the city
social_media|query|boolean|false|Enabling this includes images from Instagram in the output results. This is disabled by default, since these images are often just pictures of people or food, which often have little relevance to the actual location
image_size|query|string|false|The size of the images you'd like to see in the response
number_of_images|query|integer|false|Number of images to display.
number_of_results|query|integer|false|The maximum number of points of interest to return in the results set. This is a range from 1 to 100


#### Enumerated Values

|Parameter|Value|
|---|---|
lang|DE|
lang|EN|
lang|ES|
lang|FR|
lang|HE|
lang|IT|
lang|JA|
lang|KO|
lang|NL|
lang|PL|
lang|RU|
lang|ZH|
image_size|SMALL|
image_size|MEDIUM|
image_size|LARGE|
image_size|HD|

> Example responses

```json
{
  "current_city": {
    "geoname_id": "string",
    "location": {
      "google_maps_link": "string",
      "latitude": 0,
      "longitude": 0
    },
    "name": "string",
    "total_points_of_interest": 0
  },
  "points_of_interest": [
    {
      "categories": [
        "string"
      ],
      "contextual_images": [
        {
          "hd": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          },
          "large": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          },
          "medium": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          },
          "small": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          }
        }
      ],
      "details": {
        "description": "string",
        "short_description": "string",
        "wiki_page_link": "string"
      },
      "geoname_id": 0,
      "grades": {
        "city_grade": 0,
        "yapq_grade": 0
      },
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "main_image": "string",
      "title": "string",
      "walk_time": 0
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Points of Interest Response from YapQ|[PointsOfInterestResponse](#schemapointsofinterestresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## YapQ City Name Search

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-text?city_name=Tel%20Aviv \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-text?city_name=Tel%20Aviv HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-text',
  method: 'get',
  data: '?city_name=Tel%20Aviv',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-text', params={
  'city_name': 'Tel Aviv'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-text',
  params: {
  'city_name' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/points-of-interest/yapq-search-text?city_name=Tel%20Aviv");
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

`GET /points-of-interest/yapq-search-text`

*YapQ City Name Search - Find landmarks and attractions in a given city.*

Amadeus has partnered with <a href="http://yapq.io/">YapQ</a> to bring you point of interest APIs with the goal of offering you unbiased ratings of landmarks and tourist attractions. YapQ rates these points according to their interest on social media and provides Wikipedia content and Geonames ID in a given city. <br />
YapQ's service indexes millions of points around the world, and provides content in 12 different languages. This allows you to ensure you catch the <em>must-see</em> sights in a <a href="http://yapq.io/cities.html">YapQ supported city</a>.<br />
Each point of interest comes with links to content, grading information, location and directions to help make discovering your destination easy and fun.<br /><br />
This service is still under active development, and the response format may change without warning. We'd be interested in your feedback - <a href="mailto:sandbox@yapq.com">send us an email</a>.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
city_name|query|string|true|The name of the <a href="http://yapq.io/cities.txt">supported city</a> for which you are searching, in the selected language.
lang|query|string|false|The preferred language of the content related to each point of interest. Content will be returned in this language if available
category|query|string|false|Filters the resulting points_of_interest to include only results which have a least one category containing the given provided word. Good examples are <em>museum</em>, <em>landmark</em> or <em>church</em>
geonames|query|boolean|false|Setting this to true includes only points of interest with a geonames ID
vibes|query|boolean|false|Includes content that doesn't correspond to an active physical place, but which gives the user some background information, or <em>vibe</em> for the place they are visiting. An example of this may be information on an influential demolished building that used to exist at a certain location, or more information on a district of the city
social_media|query|boolean|false|Enabling this includes images from Instagram in the output results. This is disabled by default, since these images are often just pictures of people or food, which often have little relevance to the actual location
image_size|query|string|false|The size of the images you'd like to see in the response
number_of_images|query|integer|false|Number of images to display
number_of_results|query|integer|false|The maximum number of points of interest to return in the results set. This is a range from 1 to 100


#### Enumerated Values

|Parameter|Value|
|---|---|
lang|DE|
lang|EN|
lang|ES|
lang|FR|
lang|HE|
lang|IT|
lang|JA|
lang|KO|
lang|NL|
lang|PL|
lang|RU|
lang|ZH|
image_size|SMALL|
image_size|MEDIUM|
image_size|LARGE|
image_size|HD|

> Example responses

```json
{
  "current_city": {
    "geoname_id": "string",
    "location": {
      "google_maps_link": "string",
      "latitude": 0,
      "longitude": 0
    },
    "name": "string",
    "total_points_of_interest": 0
  },
  "points_of_interest": [
    {
      "categories": [
        "string"
      ],
      "contextual_images": [
        {
          "hd": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          },
          "large": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          },
          "medium": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          },
          "small": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          }
        }
      ],
      "details": {
        "description": "string",
        "short_description": "string",
        "wiki_page_link": "string"
      },
      "geoname_id": 0,
      "grades": {
        "city_grade": 0,
        "yapq_grade": 0
      },
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "main_image": "string",
      "title": "string",
      "walk_time": 0
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Points of Interest Response from YapQ|[PointsOfInterestResponse](#schemapointsofinterestresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Rail-Station Information

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/rail-station/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/rail-station/{id} HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/rail-station/{id}',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/rail-station/{id}', params={

}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/rail-station/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/rail-station/{id}");
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

`GET /rail-station/{id}`

*Rail-Station Information - Retrieve the rail station information corresponding to an Amadeus UIC rail station ID. Currently only French and Italian stations are supported.*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|string|true|Station ID for which further information is required.


> Example responses

```json
{
  "country": "string",
  "id": "string",
  "location": {
    "google_maps_link": "string",
    "latitude": 0,
    "longitude": 0
  },
  "name": "string",
  "short_name": "string",
  "traffic": "string",
  "type": "string"
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Station Lookup Response|[RailStationResponse](#schemarailstationresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Rail-Station Autocomplete

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/rail-stations/autocomplete?term=Mi \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/rail-stations/autocomplete?term=Mi HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/rail-stations/autocomplete',
  method: 'get',
  data: '?term=Mi',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/rail-stations/autocomplete', params={
  'term': 'Mi'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/rail-stations/autocomplete',
  params: {
  'term' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/rail-stations/autocomplete?term=Mi");
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

`GET /rail-stations/autocomplete`

*Rail Station Autocomplete - Transform user input into a unique rail station code. Currently only French and Italian stations are supported.*

<p>Given the start of any word in a rail station's official name, as a term, this API provides the full name and rail station ID of a rail station for use in searches. The response provides an array of up to 20 possible matches, sorted by passenger traffic, in a JQuery Autocomplete compatible format.</p>

<p>The value returned is the UIC station code. The label returned is always in UTF-8 format, with the station's official name (which is often in the native language). Agglomeration station codes may also be returned.</p>

<p>Note that only French and Italian rail stations are supported by the Rail Station Autocomplete API</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
term|query|string|true|Search term that should represent some part of a station name. Not case sensitive, may be blank.


> Example responses

```json
[
  {
    "label": "string",
    "value": "string"
  }
]
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|Inline
default|Default|Client or server error|[Error](#schemaerror)

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[RailStationAutocompleteResponse](#schemarailstationautocompleteresponse)]|false|No description
» label|string|true|The full name of the station, in UTF-8 format.
» value|string|true|The unique identifier of the station. You can use this as an input parameter for a rail search.



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Train Extensive Search

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/trains/extensive-search?origin=7171801&destination=8768600&departure_date=2017-04-25 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/trains/extensive-search?origin=7171801&destination=8768600&departure_date=2017-04-25 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/trains/extensive-search',
  method: 'get',
  data: '?origin=7171801&destination=8768600&departure_date=2017-04-25',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/trains/extensive-search', params={
  'origin': '7171801',  'destination': '8768600',  'departure_date': '2017-04-25'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/trains/extensive-search',
  params: {
  'origin' => 'string',
'destination' => 'string',
'departure_date' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/trains/extensive-search?origin=7171801&destination=8768600&departure_date=2017-04-25");
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

`GET /trains/extensive-search`

*Train Extensive Search - Provides multi-day availability and a variety of schedule and pricing options to travel to your destination instantly. Supports SNCF French trains only.*

<p>This API allows you to search trains availability and prices for a single day or date range. It's based on our Rail Instant Search technology, providing you with immediate results from our rail search cache.</p>

<p>This API has content from SNCF (French trains).</p>
            
<p>The content is also restricted to single-leg trips - where a single train takes you directly from the origin to the destination.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
origin|query|string|true|Identifier of the rail station from which you would like to depart.
destination|query|string|true|Identifier of the rail station to which you would like to travel.
departure_date|query|string|true|The date or range of dates on which you would like to depart from the origin station to go to the destination.


> Example responses

```json
{
  "results": [
    {
      "destination": {
        "station_code": "string",
        "station_name": "string"
      },
      "itineraries": [
        {
          "trains": [
            {
              "arrival_station": {
                "airport": "string",
                "terminal": "string"
              },
              "arrives_at": "string",
              "departs_at": "string",
              "departure_station": {
                "station_code": "string",
                "station_name": "string"
              },
              "marketing_company": "string",
              "operating_company": "string",
              "prices": [
                {
                  "accomodation": "string",
                  "booking_code": "string",
                  "rate": {
                    "rate_code": "string",
                    "rate_name": "string",
                    "restrictions": "string"
                  },
                  "service_class": "string",
                  "total_price": {
                    "amount": "string",
                    "currency": "string"
                  }
                }
              ],
              "train_number": "string",
              "train_type": "string"
            }
          ]
        }
      ],
      "origin": {
        "station_code": "string",
        "station_name": "string"
      }
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[ExtensiveTrainSearchResponse](#schemaextensivetrainsearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Train Schedule Search

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/trains/schedule-search?origin=7171801&departure_date=2017-04-25 \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/trains/schedule-search?origin=7171801&departure_date=2017-04-25 HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/trains/schedule-search',
  method: 'get',
  data: '?origin=7171801&departure_date=2017-04-25',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/trains/schedule-search', params={
  'origin': '7171801',  'departure_date': '2017-04-25'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/trains/schedule-search',
  params: {
  'origin' => 'string',
'departure_date' => 'string(date)'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/trains/schedule-search?origin=7171801&departure_date=2017-04-25");
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

`GET /trains/schedule-search`

*Train Schedule Search - Suggest destinations from your chosen departure station. Supports SNCF French Rail only.*

<p>This API allows you to find all the possible destinations in the Rail Instant Search cache (used by Extensive Search above) from a given origin station on a given day. You can use this to help build network maps, journey planners or provide inspiration for rail travel.</p>

<p>This API has continuous content from <a href="http://www.sncf.com/">SNCF</a>.<br />
All the options returned are single-leg trips - where a single train takes you directly from the origin to the destination. In general, only departure dates up to 90 days in the future are supported</p>

<p>Currently agglomeration stations are not supported</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
origin|query|string|true|Identifier of the rail station where you would like to depart from.
departure_date|query|string(date)|true|The date on which you would like to depart from the origin station to go to the destination.


> Example responses

```json
{
  "results": [
    {
      "date": "2017-10-04",
      "origin_station_id": "string",
      "services": [
        {
          "destination_station_id": "string",
          "services": [
            "string"
          ]
        }
      ]
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search response|[TrainScheduleSearchResponse](#schematrainschedulesearchresponse)
default|Default|Client or server error response|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Flight Traffic API

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/travel-intelligence/flight-traffic?period=2014-09--2014-10&origin=BOS \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/travel-intelligence/flight-traffic?period=2014-09--2014-10&origin=BOS HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/travel-intelligence/flight-traffic',
  method: 'get',
  data: '?period=2014-09--2014-10&origin=BOS',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/travel-intelligence/flight-traffic', params={
  'period': '2014-09--2014-10',  'origin': 'BOS'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/travel-intelligence/flight-traffic',
  params: {
  'period' => 'string',
'origin' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/travel-intelligence/flight-traffic?period=2014-09--2014-10&origin=BOS");
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

`GET /travel-intelligence/flight-traffic`

*Flight Traffic API - Find the true origin and destination traffic summary between two journey points over a specified period. This can help you answer questions like "What cities are people coming from to visit Los Angeles between January through April of 2015"*

<p>The Flight Traffic API lets you find the origin and destination traffic summary between two journey points over a specified period.</p>
<p>The search returns number of flights & travelers for each origin and destination, ordered by popularity, for each month specified within the search period. This search can help you answer questions like "Where are people from Los Angeles traveling to between January and April of 2015?" or "Which is the most popular month for New Yorkers to travel last year?". </p>
<p>This search is based on Amadeus' Travel Intelligence Engine, a high performance scalable cloud-based platform, born in the age of Big Data and purposely built for the industry bringing total flexibility and speed to business intelligence for travel. Please see <a href="http://www.amadeus.com/travelintelligence">amadeus.com/travelintelligence</a> for more information.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
period|query|string|true|Range of periods for which flight traffic information is required. Ranges are inclusive and ranges of months will apply from the start to the end of the month. If just a single period is specified, only that period will be displayed. Only periods from 2011-01 up to previous month of the current year are valid. Future periods are not supported.
origin|query|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city from which the traveler will depart.
destination|query|string|false|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city to which the traveler is going.
number_of_results_per_period|query|integer|false|The maximum number of destinations to return for each period. Destinations are ordered by dates and number of travelers. The maximum number of destinations per period returned is 50


> Example responses

```json
[
  {
    "destination": "string",
    "flights": 0,
    "period": "string",
    "travelers": 0
  }
]
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|Inline
default|Default|Client or server error|[Error](#schemaerror)

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[FlightTrafficSearchResult](#schemaflighttrafficsearchresult)]|false|No description
» destination|string|true|The <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city or airport to which the traveler may go, from the provided origin
» flights|integer|false|Number of flights from origin to destination during the search period provided. This field is deprecated.
» period|string|true|The date period, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format YYYY-MM or YYYY
» travelers|integer|true|Number of passengers from origin to destination during the search period provided



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Top Flight Destinations

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-destinations?period=2016-09&origin=BOS \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-destinations?period=2016-09&origin=BOS HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-destinations',
  method: 'get',
  data: '?period=2016-09&origin=BOS',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-destinations', params={
  'period': '2016-09',  'origin': 'BOS'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-destinations',
  params: {
  'period' => 'string',
'origin' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-destinations?period=2016-09&origin=BOS");
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

`GET /travel-intelligence/top-destinations`

*Top Flight Destinations - Find the most popular flight destinations from an origin during a period. This can help you answer questions like "Where are most people going to from Paris during the month of September?"*

<p>The Top Flight Destinations API lets you find the most popular flight destinations from an origin during a period. This can help you answer questions like "Where are most people from Paris going to during the month of September?" The API is based on estimated flight traffic summary data from two journey points over a specific period. It returns up to 50 results, ordered by popularity, showing number of travelers as well as number of flights.</p>

<p>This estimated search is based on Amadeus' Travel Intelligence Engine, a high performance scalable cloud-based platform, born in the age of Big Data and purposely built for the industry bringing total flexibility and speed to business intelligence for travel. Please see <a href="http://www.amadeus.com/travelintelligence">amadeus.com/travelintelligence</a> for more information.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
period|query|string|true|Period, in month of the year (YYYY-MM), when consumers are traveling. Only periods from 2011-01 up to previous month of the current year are valid. Future dates are not supported.
origin|query|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city from which the traveler will depart.
number_of_results|query|integer|false|The maximum number of destinations to return in the results set. Destinations are ordered by number of travelers. The maximum number of destinations returned is 50


> Example responses

```json
{
  "origin": "string",
  "period": "string",
  "results": [
    {
      "destination": "string",
      "flights": 0,
      "travelers": 0
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[TopDestinationsSearchResponse](#schematopdestinationssearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Top Flight Searches

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-searches?period=2016-09&origin=BOS&country=US \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-searches?period=2016-09&origin=BOS&country=US HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-searches',
  method: 'get',
  data: '?period=2016-09&origin=BOS&country=US',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-searches', params={
  'period': '2016-09',  'origin': 'BOS',  'country': 'US'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-searches',
  params: {
  'period' => 'string',
'origin' => 'string',
'country' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/travel-intelligence/top-searches?period=2016-09&origin=BOS&country=US");
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

`GET /travel-intelligence/top-searches`

*Top Flight Searches - Find the most popular flight searches from an origin in a during given search period. This can help you answer questions like "Where are people looking to travel from Paris during the month of September?"*

<p>The Top Flight Search allows you to find number of estimated searches from an origin, optionally a destination, within a time period when travelers are performing the searches.</p> 
<p>The search is based on queries performed from within a country (also refers to as market) and returns up to 50 results, ordered by popularity, showing number of searches for most searched destination with its previous year comparison. This search also shows patterns on how travelers are searching for flights, revealing where, when and for how long theyâ€™re planning to travel. See
<ul><li>Trip Durations(How long are the trips planned for?) and</li>
<li> Advance Search Period (How long before departures do travelers start searching for their trips?)</li>
</ul></p>
<p>This estimated search is based on Amadeus' Travel Intelligence Engine, a high performance scalable cloud-based platform, born in the age of Big Data and purposely built for the industry bringing total flexibility and speed to business intelligence for travel. Please see <a href="http://www.amadeus.com/travelintelligence">amadeus.com/travelintelligence</a> for more information.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
period|query|string|true|Period of date (month or year) when consumers are searching to travel. Use YYYY-MM for month or YYYY for year. Only periods from year 2011-01 up to current year, previous month are valid. Future dates are not supported.
origin|query|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city from which the traveler will depart.
destination|query|string|false|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city to which the traveler is going
country|query|string|true|2-letter IATA country code of the country where the search queries originates from.
number_of_results|query|integer|false|The maximum number of destinations to return in the results set. Destinations are ordered by number of searches. The maximum number of destinations returned is 50


> Example responses

```json
{
  "destination": "string",
  "market": "string",
  "origin": "string",
  "period": "string",
  "results": [
    {
      "destination": "string",
      "searches": 0,
      "searches_prior_year": 0
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Search Response|[TopSearchesSearchResponse](#schematopsearchessearchresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## Travel Record Retrieve

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sandbox.amadeus.com/v1.2/travel-record/{record_locator}?last_name=LOPEZ \
  -H 'Accept: application/json'

```

```http
GET https://api.sandbox.amadeus.com/v1.2/travel-record/{record_locator}?last_name=LOPEZ HTTP/1.1
Host: api.sandbox.amadeus.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.sandbox.amadeus.com/v1.2/travel-record/{record_locator}',
  method: 'get',
  data: '?last_name=LOPEZ',
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

r = requests.get('https://api.sandbox.amadeus.com/v1.2/travel-record/{record_locator}', params={
  'last_name': 'LOPEZ'
}, headers = headers)

print r.json()
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.sandbox.amadeus.com/v1.2/travel-record/{record_locator}',
  params: {
  'last_name' => 'string'
}, headers: headers

p JSON.parse(result)
```

```java
URL obj = new URL("https://api.sandbox.amadeus.com/v1.2/travel-record/{record_locator}?last_name=LOPEZ");
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

`GET /travel-record/{record_locator}`

*Travel Record Retrieve - Enable travelers to explore the details of their journeys stored in the Amadeus system using our Retrieve Travel Record API.*

<p>Note: This API requires the use of HTTPS</p>

<p>This service retrieves a travel record (also sometimes referred to as a PNR) for a given journey when provided with Record Locator to identify a travel record, along with the last name of any traveler who is marked as a passenger on this record.</p>

<p>The API provides detailed information on a given record, including any air, car, hotel or rail reservations, as well as passenger details, and contact frequent traveler information for each passenger when available. You can use this to provide a wide variety of pre-trip or in-trip services.</p>

<p>Note that this API transmits sensitive personal data about a traveler's journey. We work hard to ensure that we comply with all the legal requirements this entails, and as an application owner, you need to do so too - we don't want you to get in trouble! This paragraph, or anything else in our documentation, does not constitute legal advice, it's just to give you an idea of some of the potential issues that you may encounter. Please check your legal obligations regarding the use of this data before implementing this API</p>

<p>In most countries, the data in the returned travel record is considered to be the property of the traveler. In order to ensure that you are acting on behalf of the traveler, we require you to provide the traveler's last name in addition to the record locator when you make a call to this API. You should ensure that you have consent from the traveler before retrieving this record, in some countries this is a legal requirement - please respect this appropriately.</p>

<p>Our data center is based in Europe, so there is a legal requirement that you to access this API over a secure connection. If you plan to store the information returned by this API, ensure you comply with storage requirements for European data, in addition to those of your local country. For example, there are strict requirements on the caching of retrieved travel records, so please ensure the cache control HTTP headers in the response are respected.</p>

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
record_locator|path|string|true|The Amadeus identifier of the given travel record. Usually printed at the top of an itinerary or boarding pass.
last_name|query|string|true|The last name of any traveler in this record, as written on their identification used for travel. This is required to ensure that applications retrieving the record are acting on behalf of the customer.
env|query|string|false|Indicates the Amadeus system from which this record should be retrieved.


> Example responses

```json
{
  "header": {
    "creation_office_id": "string",
    "owner_office_id": "string"
  },
  "messages": [
    {
      "message": "string",
      "severity": "string",
      "type": "string"
    }
  ],
  "record_locator": "string",
  "reservation": {
    "cars": [
      {
        "booking_info": {
          "reservation_code": "string",
          "status": "string"
        },
        "car": {
          "estimated_total": {
            "amount": "string",
            "currency": "string"
          },
          "images": [
            {
              "category": "string",
              "height": 0,
              "url": "string",
              "width": 0
            }
          ],
          "rates": [
            {
              "price": {
                "amount": "string",
                "currency": "string"
              },
              "type": "string"
            }
          ],
          "vehicle_info": {
            "acriss_code": "string",
            "air_conditioning": true,
            "category": "string",
            "fuel": "string",
            "transmission": "string",
            "type": "string"
          }
        },
        "drop_off": "string",
        "id": "string",
        "origin": "string",
        "pick_up": "string",
        "provider": {
          "company_code": "string",
          "company_name": "string"
        },
        "traveler_ids": [
          "string"
        ]
      }
    ],
    "flight_tickets": {
      "flight_bounds": [
        {
          "flights": [
            {
              "arrives_at": "string",
              "booking_info": {
                "airline_record_locator": "string",
                "booking_code": "string",
                "status": "string",
                "travel_class": "string"
              },
              "departs_at": "string",
              "destination": {
                "airport": "string",
                "terminal": "string"
              },
              "flight_number": "string",
              "id": "string",
              "marketing_airline": "string",
              "operating_airline": "string",
              "origin": {
                "airport": "string",
                "terminal": "string"
              },
              "traveler_ids": [
                "string"
              ]
            }
          ]
        }
      ],
      "id": "string",
      "price": {
        "amount": "string",
        "currency": "string"
      },
      "traveler_ids": [
        "string"
      ]
    },
    "hotels": [
      {
        "booking_info": {
          "reservation_code": "string",
          "status": "string"
        },
        "check_in": "2017-10-04",
        "check_out": "2017-10-04",
        "id": "string",
        "property_code": "string",
        "property_name": "string",
        "total_price": {
          "amount": "string",
          "currency": "string"
        },
        "traveler_ids": [
          "string"
        ]
      }
    ],
    "others": [
      {
        "booking_info": {
          "status": "string"
        },
        "date": "2017-10-04",
        "description": "string",
        "id": "string",
        "location": "string",
        "traveler_ids": [
          "string"
        ]
      }
    ],
    "unticketed_flights": [
      {
        "flights": [
          {
            "arrives_at": "string",
            "booking_info": {
              "airline_record_locator": "string",
              "booking_code": "string",
              "status": "string",
              "travel_class": "string"
            },
            "departs_at": "string",
            "destination": {
              "airport": "string",
              "terminal": "string"
            },
            "flight_number": "string",
            "id": "string",
            "marketing_airline": "string",
            "operating_airline": "string",
            "origin": {
              "airport": "string",
              "terminal": "string"
            },
            "traveler_ids": [
              "string"
            ]
          }
        ]
      }
    ]
  },
  "travelers": [
    {
      "contacts": [
        {
          "detail": "string",
          "purpose": "string",
          "type": "string"
        }
      ],
      "date_of_birth": "2017-10-04",
      "first_name": "string",
      "frequent_traveler_cards": [
        {
          "card_number": "string",
          "company_code": "string",
          "issuer_type": "string"
        }
      ],
      "id": "string",
      "infant": {
        "date_of_birth": "2017-10-04",
        "first_name": "string",
        "last_name": "string"
      },
      "last_name": "string",
      "traveler_type": "string"
    }
  ]
}
```
```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Valid Travel Record|[TravelRecordResponse](#schematravelrecordresponse)
default|Default|Client or server error|[Error](#schemaerror)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

# Schemas

## Address

<a name="schemaaddress"></a>

```json
{
  "city": "string",
  "country": "string",
  "line1": "string",
  "postal_code": "string",
  "region": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
city|string|true|The town or city in which place is located.
country|string|true|The <a href="http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">ISO 3166-1 alpha-2 country code</a> country code of this address.
line1|string|true|The first line of this place's address. Generally represents the basic street address.
postal_code|string|false|The postal or zip code of this address.
region|string|false|The state or region code in which the place is located.



## AffiliateFlightSearchPrice

<a name="schemaaffiliateflightsearchprice"></a>

```json
{
  "currency": "string",
  "price_per_adult": {
    "tax": "string",
    "total_fare": "string"
  },
  "price_per_child": {
    "tax": "string",
    "total_fare": "string"
  },
  "price_per_infant": {
    "tax": "string",
    "total_fare": "string"
  },
  "restrictions": {
    "change_penalties": true,
    "refundable": true
  },
  "total_price": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
currency|string|true|The <a href="https://en.wikipedia.org/wiki/ISO_4217">currency</a> code applicable to this fare
price_per_adult|[Fare](#schemafare)|true|No description
» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
price_per_child|[Fare](#schemafare)|false|No description
» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
price_per_infant|[Fare](#schemafare)|false|No description
» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
restrictions|[FareRestrictions](#schemafarerestrictions)|true|No description
» change_penalties|boolean|true|Indicates whether this fare allows the itinerary to be changed under some circumstances. Note that a change fee or penalty may apply
» refundable|boolean|true|Indicates whether this fare is refundable under some circumstances. Note that a refund charge or penalty may apply
total_price|string|true|The total price for all the requested passengers for this flight



## AffiliatePayout

<a name="schemaaffiliatepayout"></a>

```json
{
  "CPA": {
    "amount": "string",
    "currency": "string"
  },
  "CPC": {
    "amount": "string",
    "currency": "string"
  },
  "CPS": {
    "amount": "string",
    "currency": "string"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
CPA|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
CPC|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
CPS|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.



## AffiliateSearchMeta

<a name="schemaaffiliatesearchmeta"></a>

```json
{
  "carriers": {
    "property1": {
      "logos": {
        "medium": "string",
        "small": "string"
      },
      "name": "string"
    },
    "property2": {
      "logos": {
        "medium": "string",
        "small": "string"
      },
      "name": "string"
    }
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
carriers|[CarrierMeta](#schemacarriermeta)|true|No description
» logos|[Logos](#schemalogos)|true|No description
»» medium|string|false|URL to logo of resolution 60x60px
»» small|string|false|URL to logo of resolution 27x27px
» name|string|true|Display name of the airline



## AffiliateSearchResponse

<a name="schemaaffiliatesearchresponse"></a>

```json
{
  "meta": {
    "carriers": {
      "property1": {
        "logos": {
          "medium": "string",
          "small": "string"
        },
        "name": "string"
      },
      "property2": {
        "logos": {
          "medium": "string",
          "small": "string"
        },
        "name": "string"
      }
    }
  },
  "results": [
    {
      "airline": "string",
      "deep_link": "string",
      "fare": {
        "currency": "string",
        "price_per_adult": {
          "tax": "string",
          "total_fare": "string"
        },
        "price_per_child": {
          "tax": "string",
          "total_fare": "string"
        },
        "price_per_infant": {
          "tax": "string",
          "total_fare": "string"
        },
        "restrictions": {
          "change_penalties": true,
          "refundable": true
        },
        "total_price": "string"
      },
      "inbound": {
        "duration": "string",
        "flights": [
          {
            "aircraft": "string",
            "arrives_at": "string",
            "booking_info": {
              "booking_code": "string",
              "cabin_code": "string",
              "fare_basis": "string",
              "fare_family": "string",
              "seats_remaining": "string",
              "travel_class": "string"
            },
            "departs_at": "string",
            "destination": {
              "airport": "string",
              "terminal": "string"
            },
            "flight_number": "string",
            "marketing_airline": "string",
            "operating_airline": "string",
            "origin": {
              "airport": "string",
              "terminal": "string"
            }
          }
        ]
      },
      "outbound": {
        "duration": "string",
        "flights": [
          {
            "aircraft": "string",
            "arrives_at": "string",
            "booking_info": {
              "booking_code": "string",
              "cabin_code": "string",
              "fare_basis": "string",
              "fare_family": "string",
              "seats_remaining": "string",
              "travel_class": "string"
            },
            "departs_at": "string",
            "destination": {
              "airport": "string",
              "terminal": "string"
            },
            "flight_number": "string",
            "marketing_airline": "string",
            "operating_airline": "string",
            "origin": {
              "airport": "string",
              "terminal": "string"
            }
          }
        ]
      },
      "payout": {
        "CPA": {
          "amount": "string",
          "currency": "string"
        },
        "CPC": {
          "amount": "string",
          "currency": "string"
        },
        "CPS": {
          "amount": "string",
          "currency": "string"
        }
      }
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
meta|[AffiliateSearchMeta](#schemaaffiliatesearchmeta)|true|No description
» carriers|[CarrierMeta](#schemacarriermeta)|true|No description
»» logos|[Logos](#schemalogos)|true|No description
»»» medium|string|false|URL to logo of resolution 60x60px
»»» small|string|false|URL to logo of resolution 27x27px
»» name|string|true|Display name of the airline
results|[[AffiliateSearchResult](#schemaaffiliatesearchresult)]|false|No description
» airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is selling this result
» deep_link|string|true|A link to the page from which this result can be purchased from the affiliate
» fare|[AffiliateFlightSearchPrice](#schemaaffiliateflightsearchprice)|true|No description
»» currency|string|true|The <a href="https://en.wikipedia.org/wiki/ISO_4217">currency</a> code applicable to this fare
»» price_per_adult|[Fare](#schemafare)|true|No description
»»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
»» price_per_child|[Fare](#schemafare)|false|No description
»»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
»» price_per_infant|[Fare](#schemafare)|false|No description
»»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
»» restrictions|[FareRestrictions](#schemafarerestrictions)|true|No description
»»» change_penalties|boolean|true|Indicates whether this fare allows the itinerary to be changed under some circumstances. Note that a change fee or penalty may apply
»»» refundable|boolean|true|Indicates whether this fare is refundable under some circumstances. Note that a refund charge or penalty may apply
»» total_price|string|true|The total price for all the requested passengers for this flight
» inbound|[FlightSearchBound](#schemaflightsearchbound)|false|No description
»» duration|string|false|The duration of this bound, including layover time, expressed in the format hh:mm
»» flights|[[FlightSearchSegment](#schemaflightsearchsegment)]|false|No description
»»» aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
»»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»»» booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
»»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»»» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
»»»» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
»»»» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
»»»» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
»»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»»» destination|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»»» origin|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
» outbound|[FlightSearchBound](#schemaflightsearchbound)|true|No description
»» duration|string|false|The duration of this bound, including layover time, expressed in the format hh:mm
»» flights|[[FlightSearchSegment](#schemaflightsearchsegment)]|false|No description
»»» aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
»»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»»» booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
»»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»»» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
»»»» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
»»»» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
»»»» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
»»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»»» destination|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»»» origin|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
» payout|[AffiliatePayout](#schemaaffiliatepayout)|true|No description
»» CPA|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»» CPC|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»» CPS|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.



## AffiliateSearchResult

<a name="schemaaffiliatesearchresult"></a>

```json
{
  "airline": "string",
  "deep_link": "string",
  "fare": {
    "currency": "string",
    "price_per_adult": {
      "tax": "string",
      "total_fare": "string"
    },
    "price_per_child": {
      "tax": "string",
      "total_fare": "string"
    },
    "price_per_infant": {
      "tax": "string",
      "total_fare": "string"
    },
    "restrictions": {
      "change_penalties": true,
      "refundable": true
    },
    "total_price": "string"
  },
  "inbound": {
    "duration": "string",
    "flights": [
      {
        "aircraft": "string",
        "arrives_at": "string",
        "booking_info": {
          "booking_code": "string",
          "cabin_code": "string",
          "fare_basis": "string",
          "fare_family": "string",
          "seats_remaining": "string",
          "travel_class": "string"
        },
        "departs_at": "string",
        "destination": {
          "airport": "string",
          "terminal": "string"
        },
        "flight_number": "string",
        "marketing_airline": "string",
        "operating_airline": "string",
        "origin": {
          "airport": "string",
          "terminal": "string"
        }
      }
    ]
  },
  "outbound": {
    "duration": "string",
    "flights": [
      {
        "aircraft": "string",
        "arrives_at": "string",
        "booking_info": {
          "booking_code": "string",
          "cabin_code": "string",
          "fare_basis": "string",
          "fare_family": "string",
          "seats_remaining": "string",
          "travel_class": "string"
        },
        "departs_at": "string",
        "destination": {
          "airport": "string",
          "terminal": "string"
        },
        "flight_number": "string",
        "marketing_airline": "string",
        "operating_airline": "string",
        "origin": {
          "airport": "string",
          "terminal": "string"
        }
      }
    ]
  },
  "payout": {
    "CPA": {
      "amount": "string",
      "currency": "string"
    },
    "CPC": {
      "amount": "string",
      "currency": "string"
    },
    "CPS": {
      "amount": "string",
      "currency": "string"
    }
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is selling this result
deep_link|string|true|A link to the page from which this result can be purchased from the affiliate
fare|[AffiliateFlightSearchPrice](#schemaaffiliateflightsearchprice)|true|No description
» currency|string|true|The <a href="https://en.wikipedia.org/wiki/ISO_4217">currency</a> code applicable to this fare
» price_per_adult|[Fare](#schemafare)|true|No description
»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
» price_per_child|[Fare](#schemafare)|false|No description
»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
» price_per_infant|[Fare](#schemafare)|false|No description
»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
» restrictions|[FareRestrictions](#schemafarerestrictions)|true|No description
»» change_penalties|boolean|true|Indicates whether this fare allows the itinerary to be changed under some circumstances. Note that a change fee or penalty may apply
»» refundable|boolean|true|Indicates whether this fare is refundable under some circumstances. Note that a refund charge or penalty may apply
» total_price|string|true|The total price for all the requested passengers for this flight
inbound|[FlightSearchBound](#schemaflightsearchbound)|false|No description
» duration|string|false|The duration of this bound, including layover time, expressed in the format hh:mm
» flights|[[FlightSearchSegment](#schemaflightsearchsegment)]|false|No description
»» aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»» booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
»»» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
»»» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
»»» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»» destination|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»» origin|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
outbound|[FlightSearchBound](#schemaflightsearchbound)|true|No description
» duration|string|false|The duration of this bound, including layover time, expressed in the format hh:mm
» flights|[[FlightSearchSegment](#schemaflightsearchsegment)]|false|No description
»» aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»» booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
»»» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
»»» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
»»» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»» destination|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»» origin|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
payout|[AffiliatePayout](#schemaaffiliatepayout)|true|No description
» CPA|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
» CPC|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
» CPS|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.



## Airport

<a name="schemaairport"></a>

```json
{
  "airport": "string",
  "terminal": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport



## AirportAutocompleteResponse

<a name="schemaairportautocompleteresponse"></a>

```json
{
  "label": "string",
  "value": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
label|string|true|The name of this airport, in UTF-8 format, prefixed with the name of the city if it is not already incorporated in the name of the airport, and appended with the location's <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> (as in value), enclosed in square brackets.
value|string|true|The 3 letter IATA location code of the given city or airport. You can use this as an input parameter for a flight low-fare or inspiration search.



## AirportInformation

<a name="schemaairportinformation"></a>

```json
{
  "aircraft_movements": 0,
  "city_code": "string",
  "city_name": "string",
  "code": "string",
  "country": "string",
  "location": {
    "google_maps_link": "string",
    "latitude": 0,
    "longitude": 0
  },
  "name": "string",
  "state": "string",
  "timezone": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
aircraft_movements|integer|false|The annual number of aircraft movements at that airport.
city_code|string|true|The three letter <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city of the city in which this airport is located.
city_name|string|true|The English name of the city in which this airport is located
code|string|true|The 3 letter IATA airport code of this given airport. You can use this as an input parameter for a low-fare flight search, to get more specific results than the city code, but inspiration search works best using the city code.
country|string|true|The <a href="http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">ISO 3166-1 alpha-2 country code</a> in which this city can be found.
location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
name|string|true|The name of this airport, in UTF-8 format
state|string|false|The state code of this city, if applicable
timezone|string|true|The <a href="http://en.wikipedia.org/wiki/List_of_tz_database_time_zones">Olson format</a> name of the timezone in which this airport is located



## Amenity

<a name="schemaamenity"></a>

```json
{
  "amenity": "string",
  "description": "string",
  "ota_code": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
amenity|string|false|<a href="hotels-api-supported-amenities-filter">The amenity code</a>
description|string|false|The decoded text description for this amenity code, where available.
ota_code|string|false|The <a href="http://www.opentravel.org/">Open Travel Alliance</a> <a href="ota-hotel-amenity-code-table">Hotel Amenities Code</a> for this amenity.



## Amount

<a name="schemaamount"></a>

```json
{
  "amount": "string",
  "currency": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.



## Award

<a name="schemaaward"></a>

```json
{
  "provider": "string",
  "rating": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
provider|string|true|The organization that issued the award. For example&colon;. Local Star Rating, AAA.
rating|string|true|The level of the award that was awarded on the provider's scale. For example&colon; 4 or RECOMMENDED.



## CarReservation

<a name="schemacarreservation"></a>

```json
{
  "booking_info": {
    "reservation_code": "string",
    "status": "string"
  },
  "car": {
    "estimated_total": {
      "amount": "string",
      "currency": "string"
    },
    "images": [
      {
        "category": "string",
        "height": 0,
        "url": "string",
        "width": 0
      }
    ],
    "rates": [
      {
        "price": {
          "amount": "string",
          "currency": "string"
        },
        "type": "string"
      }
    ],
    "vehicle_info": {
      "acriss_code": "string",
      "air_conditioning": true,
      "category": "string",
      "fuel": "string",
      "transmission": "string",
      "type": "string"
    }
  },
  "drop_off": "string",
  "id": "string",
  "origin": "string",
  "pick_up": "string",
  "provider": {
    "company_code": "string",
    "company_name": "string"
  },
  "traveler_ids": [
    "string"
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
booking_info|[CarReservationBookingInfo](#schemacarreservationbookinginfo)|false|No description
» reservation_code|string|true|The identifier of this reservation in the car rental provider's system. This should be provided at the rental office to identify your reservation.
» status|string|true|An enumeration to represent the reservation status for this car rental. For example&colon; CONFIRMED, CANCELLED, REQUESTED, REJECTED, PENDING_CANCELLATION, PENDING_CONFIRMATION.
car|[Vehicle](#schemavehicle)|true|No description
» estimated_total|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
» vehicle_info|[VehicleInfo](#schemavehicleinfo)|true|No description
»» acriss_code|string|true|The 4 letter <a href="http://en.wikipedia.org/wiki/ACRISS_Car_Classification_Code">ACRISS code</a> that defines the properties of vehicle being rented.
»» air_conditioning|boolean|false|The decoded ACRISS air_conditioning information, to let you know if this vehicle has air conditioning
»» category|string|true|The decoded ACRISS vehicle category (For example&colon; Economy, Luxury, Standard).
»» fuel|string|false|The decoded ACRISS fuel type, to let you know if this vehicle is hybrid, electric, etc.
»» transmission|string|false|The decoded ACRISS transmission type, to let you know if this vehicle is Automatic or Manual Transmission (stick-shift).
»» type|string|false|The decoded ACRISS vehicle type, to let you know what kind of vehicle this is (For example&colon; Van, SUV, Pickup).
» images|[[Image](#schemaimage)]|false|An image to give an indication of what to expect when renting this vehicle.
»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»» height|integer|false|The pixel height of the image at the provided URL.
»» url|string|true|The URL of the hotel image of this given category and size, for display.
»» width|integer|false|The pixel width of the image at the provided URL.
» rates|[[Rate](#schemarate)]|false|Rates that will be applied during the duration of the car rental requested. These rates are generally not inclusive of tax and are used by the car rental company to compute the total cost at the end of the rental period.
»» price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»» type|string|true|The type or applicability period of rate being applied. For example&colon; DAILY, WEEKLY, WEEKEND.
drop_off|string|true|Date at which the car rental will end and the car will be returned to the rental location. <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-ddTHH.
id|string|true|Uniquely identifies this car rental reservation in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
origin|string|true|This car rental company office location ID. If this is an airport location, this will be the airport's <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a>. Otherwise, this is a custom value provided by the car rental provider.
pick_up|string|true|Date on which the car rental will be collected from the car rental location. <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-ddTHH.
provider|[Company](#schemacompany)|true|No description
» company_code|string|true|The Amadeus 2-character company code of this provider.
» company_name|string|true|The long name of the provider corresponding to the above code.
traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this car rental applies. Generally, only drivers of the vehicle will be marked in this array.



## CarReservationBookingInfo

<a name="schemacarreservationbookinginfo"></a>

```json
{
  "reservation_code": "string",
  "status": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
reservation_code|string|true|The identifier of this reservation in the car rental provider's system. This should be provided at the rental office to identify your reservation.
status|string|true|An enumeration to represent the reservation status for this car rental. For example&colon; CONFIRMED, CANCELLED, REQUESTED, REJECTED, PENDING_CANCELLATION, PENDING_CONFIRMATION.



## CarSearchResponse

<a name="schemacarsearchresponse"></a>

```json
{
  "results": [
    {
      "airport": "string",
      "cars": [
        {
          "estimated_total": {
            "amount": "string",
            "currency": "string"
          },
          "images": [
            {
              "category": "string",
              "height": 0,
              "url": "string",
              "width": 0
            }
          ],
          "rates": [
            {
              "price": {
                "amount": "string",
                "currency": "string"
              },
              "type": "string"
            }
          ],
          "vehicle_info": {
            "acriss_code": "string",
            "air_conditioning": true,
            "category": "string",
            "fuel": "string",
            "transmission": "string",
            "type": "string"
          }
        }
      ],
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "provider": {
        "company_code": "string",
        "company_name": "string"
      }
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
results|[[CarSearchResult](#schemacarsearchresult)]|false|No description
» airport|string|false|The exact quality of this parameter depends on the provider but it's usually quite accurate.
» location|[Geolocation](#schemageolocation)|false|An object to describe the coordinates of a map location
»» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
»» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
»» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
» provider|[Company](#schemacompany)|true|No description
»» company_code|string|true|The Amadeus 2-character company code of this provider.
»» company_name|string|true|The long name of the provider corresponding to the above code.
» cars|[[Vehicle](#schemavehicle)]|false|Further details about each of the vehicles offered by this car rental provider.
»» estimated_total|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»» vehicle_info|[VehicleInfo](#schemavehicleinfo)|true|No description
»»» acriss_code|string|true|The 4 letter <a href="http://en.wikipedia.org/wiki/ACRISS_Car_Classification_Code">ACRISS code</a> that defines the properties of vehicle being rented.
»»» air_conditioning|boolean|false|The decoded ACRISS air_conditioning information, to let you know if this vehicle has air conditioning
»»» category|string|true|The decoded ACRISS vehicle category (For example&colon; Economy, Luxury, Standard).
»»» fuel|string|false|The decoded ACRISS fuel type, to let you know if this vehicle is hybrid, electric, etc.
»»» transmission|string|false|The decoded ACRISS transmission type, to let you know if this vehicle is Automatic or Manual Transmission (stick-shift).
»»» type|string|false|The decoded ACRISS vehicle type, to let you know what kind of vehicle this is (For example&colon; Van, SUV, Pickup).
»» images|[[Image](#schemaimage)]|false|An image to give an indication of what to expect when renting this vehicle.
»»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»»» height|integer|false|The pixel height of the image at the provided URL.
»»» url|string|true|The URL of the hotel image of this given category and size, for display.
»»» width|integer|false|The pixel width of the image at the provided URL.
»» rates|[[Rate](#schemarate)]|false|Rates that will be applied during the duration of the car rental requested. These rates are generally not inclusive of tax and are used by the car rental company to compute the total cost at the end of the rental period.
»»» price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»»» type|string|true|The type or applicability period of rate being applied. For example&colon; DAILY, WEEKLY, WEEKEND.



## CarSearchResult

<a name="schemacarsearchresult"></a>

```json
{
  "airport": "string",
  "cars": [
    {
      "estimated_total": {
        "amount": "string",
        "currency": "string"
      },
      "images": [
        {
          "category": "string",
          "height": 0,
          "url": "string",
          "width": 0
        }
      ],
      "rates": [
        {
          "price": {
            "amount": "string",
            "currency": "string"
          },
          "type": "string"
        }
      ],
      "vehicle_info": {
        "acriss_code": "string",
        "air_conditioning": true,
        "category": "string",
        "fuel": "string",
        "transmission": "string",
        "type": "string"
      }
    }
  ],
  "location": {
    "google_maps_link": "string",
    "latitude": 0,
    "longitude": 0
  },
  "provider": {
    "company_code": "string",
    "company_name": "string"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
airport|string|false|The exact quality of this parameter depends on the provider but it's usually quite accurate.
location|[Geolocation](#schemageolocation)|false|An object to describe the coordinates of a map location
» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
provider|[Company](#schemacompany)|true|No description
» company_code|string|true|The Amadeus 2-character company code of this provider.
» company_name|string|true|The long name of the provider corresponding to the above code.
cars|[[Vehicle](#schemavehicle)]|false|Further details about each of the vehicles offered by this car rental provider.
» estimated_total|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
» vehicle_info|[VehicleInfo](#schemavehicleinfo)|true|No description
»» acriss_code|string|true|The 4 letter <a href="http://en.wikipedia.org/wiki/ACRISS_Car_Classification_Code">ACRISS code</a> that defines the properties of vehicle being rented.
»» air_conditioning|boolean|false|The decoded ACRISS air_conditioning information, to let you know if this vehicle has air conditioning
»» category|string|true|The decoded ACRISS vehicle category (For example&colon; Economy, Luxury, Standard).
»» fuel|string|false|The decoded ACRISS fuel type, to let you know if this vehicle is hybrid, electric, etc.
»» transmission|string|false|The decoded ACRISS transmission type, to let you know if this vehicle is Automatic or Manual Transmission (stick-shift).
»» type|string|false|The decoded ACRISS vehicle type, to let you know what kind of vehicle this is (For example&colon; Van, SUV, Pickup).
» images|[[Image](#schemaimage)]|false|An image to give an indication of what to expect when renting this vehicle.
»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»» height|integer|false|The pixel height of the image at the provided URL.
»» url|string|true|The URL of the hotel image of this given category and size, for display.
»» width|integer|false|The pixel width of the image at the provided URL.
» rates|[[Rate](#schemarate)]|false|Rates that will be applied during the duration of the car rental requested. These rates are generally not inclusive of tax and are used by the car rental company to compute the total cost at the end of the rental period.
»» price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»» type|string|true|The type or applicability period of rate being applied. For example&colon; DAILY, WEEKLY, WEEKEND.



## CarrierInfo

<a name="schemacarrierinfo"></a>

```json
{
  "logos": {
    "medium": "string",
    "small": "string"
  },
  "name": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
logos|[Logos](#schemalogos)|true|No description
» medium|string|false|URL to logo of resolution 60x60px
» small|string|false|URL to logo of resolution 27x27px
name|string|true|Display name of the airline



## CarrierMeta

<a name="schemacarriermeta"></a>

```json
{
  "property1": {
    "logos": {
      "medium": "string",
      "small": "string"
    },
    "name": "string"
  },
  "property2": {
    "logos": {
      "medium": "string",
      "small": "string"
    },
    "name": "string"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
additionalProperties|object|false|No description
logos|[Logos](#schemalogos)|true|No description
» medium|string|false|URL to logo of resolution 60x60px
» small|string|false|URL to logo of resolution 27x27px
name|string|true|Display name of the airline



## CityInformation

<a name="schemacityinformation"></a>

```json
{
  "code": "string",
  "country": "string",
  "currency": "string",
  "geonames_ID": "string",
  "location": {
    "google_maps_link": "string",
    "latitude": 0,
    "longitude": 0
  },
  "name": "string",
  "state": "string",
  "timezone": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
code|string|true|The <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of this city. If you intend to make a flight search from the output of this call, I recommend using this as your input parameter as it generally gives the best results.
country|string|true|The <a href="http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">ISO 3166-1 alpha-2 country code</a> in which this city can be found.
currency|string|false|The ISO-4217 currency code of the official local currency at this location
geonames_ID|string|true|The ID of this city in the open-sourced Geonames DB
location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
name|string|true|The name of this city, in English
state|string|false|The state code of this city, if applicable
timezone|string|true|The <a href="http://en.wikipedia.org/wiki/List_of_tz_database_time_zones">Olson format</a> name of the timezone in which this city is located



## Company

<a name="schemacompany"></a>

```json
{
  "company_code": "string",
  "company_name": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
company_code|string|true|The Amadeus 2-character company code of this provider.
company_name|string|true|The long name of the provider corresponding to the above code.



## Contact

<a name="schemacontact"></a>

```json
{
  "detail": "string",
  "purpose": "string",
  "type": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
detail|string|true|How that contact should be used, eg. a phone number
purpose|string|false|The reason or channel of that contact method. For example&colon; HOME, EMERGENCY, MOBILE.
type|string|true|The method of contact, such as phone or fax.



## Error

<a name="schemaerror"></a>

```json
{
  "message": "string",
  "more_info": "string",
  "status": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
message|string|true|No description
more_info|string|false|No description
status|integer|true|No description



## ExtensiveTrainSearchResponse

<a name="schemaextensivetrainsearchresponse"></a>

```json
{
  "results": [
    {
      "destination": {
        "station_code": "string",
        "station_name": "string"
      },
      "itineraries": [
        {
          "trains": [
            {
              "arrival_station": {
                "airport": "string",
                "terminal": "string"
              },
              "arrives_at": "string",
              "departs_at": "string",
              "departure_station": {
                "station_code": "string",
                "station_name": "string"
              },
              "marketing_company": "string",
              "operating_company": "string",
              "prices": [
                {
                  "accomodation": "string",
                  "booking_code": "string",
                  "rate": {
                    "rate_code": "string",
                    "rate_name": "string",
                    "restrictions": "string"
                  },
                  "service_class": "string",
                  "total_price": {
                    "amount": "string",
                    "currency": "string"
                  }
                }
              ],
              "train_number": "string",
              "train_type": "string"
            }
          ]
        }
      ],
      "origin": {
        "station_code": "string",
        "station_name": "string"
      }
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
results|[[ExtensiveTrainSearchResult](#schemaextensivetrainsearchresult)]|false|No description
» destination|[Station](#schemastation)|true|No description
»» station_code|string|true|ID of this rail station
»» station_name|string|true|Full name of this rail station.
» origin|[Station](#schemastation)|true|No description
»» station_code|string|true|ID of this rail station
»» station_name|string|true|Full name of this rail station.
» itineraries|[[TrainSearchItinerary](#schematrainsearchitinerary)]|false|Routes from the origin to the destination.
»» trains|[[TrainSearchSegment](#schematrainsearchsegment)]|false|The array of trains that will be required to complete the given itinerary. Since the cache currently only contains direct itineraries, there will be only one object in this array.
»»» arrival_station|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»» arrives_at|string|true|The <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date-time of the train's arrival in the local time zone of the arrival station, in the format YYYY-MM-DDTHH:mm.
»»» departs_at|string|true|The <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date-time of the train's departure in the local time zone of the departure station, in the format YYYY-MM-DDTHH:mm.
»»» departure_station|[Station](#schemastation)|true|No description
»»»» station_code|string|true|ID of this rail station
»»»» station_name|string|true|Full name of this rail station.
»»» marketing_company|string|true|The name of the train company selling this train journey. This is the name you should see printed on your ticket.
»»» operating_company|string|true|The name of the train company operating this train journey. This is the name you should see written on the train.
»»» train_number|string|true|The identifying number of this train service. Usually the marketing company will only operate on train per day with this train number.
»»» train_type|string|false|The type of train that you may expect for this journey. For example&colon; InterCity, Regional...
»»» prices|[[TrainSearchPricing](#schematrainsearchpricing)]|false|Possible pricing for this train journey.
»»»» accomodation|string|true|A standard enumeration of the mode in which the passenger is accommodated. For example&colon; SEAT, BERTH, CABIN, CARGO, UNKNOWN.
»»»» booking_code|string|true|A code the identifies the type of booking class being used.
»»»» rate|[RestrictedRate](#schemarestrictedrate)|true|No description
»»»»» rate_code|string|true|The unique identifier of this rate.
»»»»» rate_name|string|true|The name used by the company to describe this rate.
»»»»» restrictions|string|true|An enumeration of the type of restrictions associated with this rate.
»»»» service_class|string|true|A standard enumeration of the type of seat, bed or service the passenger can expect.
»»»» total_price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»»»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.



## ExtensiveTrainSearchResult

<a name="schemaextensivetrainsearchresult"></a>

```json
{
  "destination": {
    "station_code": "string",
    "station_name": "string"
  },
  "itineraries": [
    {
      "trains": [
        {
          "arrival_station": {
            "airport": "string",
            "terminal": "string"
          },
          "arrives_at": "string",
          "departs_at": "string",
          "departure_station": {
            "station_code": "string",
            "station_name": "string"
          },
          "marketing_company": "string",
          "operating_company": "string",
          "prices": [
            {
              "accomodation": "string",
              "booking_code": "string",
              "rate": {
                "rate_code": "string",
                "rate_name": "string",
                "restrictions": "string"
              },
              "service_class": "string",
              "total_price": {
                "amount": "string",
                "currency": "string"
              }
            }
          ],
          "train_number": "string",
          "train_type": "string"
        }
      ]
    }
  ],
  "origin": {
    "station_code": "string",
    "station_name": "string"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
destination|[Station](#schemastation)|true|No description
» station_code|string|true|ID of this rail station
» station_name|string|true|Full name of this rail station.
origin|[Station](#schemastation)|true|No description
» station_code|string|true|ID of this rail station
» station_name|string|true|Full name of this rail station.
itineraries|[[TrainSearchItinerary](#schematrainsearchitinerary)]|false|Routes from the origin to the destination.
» trains|[[TrainSearchSegment](#schematrainsearchsegment)]|false|The array of trains that will be required to complete the given itinerary. Since the cache currently only contains direct itineraries, there will be only one object in this array.
»» arrival_station|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»» arrives_at|string|true|The <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date-time of the train's arrival in the local time zone of the arrival station, in the format YYYY-MM-DDTHH:mm.
»» departs_at|string|true|The <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date-time of the train's departure in the local time zone of the departure station, in the format YYYY-MM-DDTHH:mm.
»» departure_station|[Station](#schemastation)|true|No description
»»» station_code|string|true|ID of this rail station
»»» station_name|string|true|Full name of this rail station.
»» marketing_company|string|true|The name of the train company selling this train journey. This is the name you should see printed on your ticket.
»» operating_company|string|true|The name of the train company operating this train journey. This is the name you should see written on the train.
»» train_number|string|true|The identifying number of this train service. Usually the marketing company will only operate on train per day with this train number.
»» train_type|string|false|The type of train that you may expect for this journey. For example&colon; InterCity, Regional...
»» prices|[[TrainSearchPricing](#schematrainsearchpricing)]|false|Possible pricing for this train journey.
»»» accomodation|string|true|A standard enumeration of the mode in which the passenger is accommodated. For example&colon; SEAT, BERTH, CABIN, CARGO, UNKNOWN.
»»» booking_code|string|true|A code the identifies the type of booking class being used.
»»» rate|[RestrictedRate](#schemarestrictedrate)|true|No description
»»»» rate_code|string|true|The unique identifier of this rate.
»»»» rate_name|string|true|The name used by the company to describe this rate.
»»»» restrictions|string|true|An enumeration of the type of restrictions associated with this rate.
»»» service_class|string|true|A standard enumeration of the type of seat, bed or service the passenger can expect.
»»» total_price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.



## ExtremeSearchResponse

<a name="schemaextremesearchresponse"></a>

```json
{
  "currency": "string",
  "origin": "string",
  "results": [
    {
      "airline": "string",
      "departure_date": "2017-10-04",
      "destination": "string",
      "price": "string",
      "return_date": "2017-10-04"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
origin|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a>
results|[[ExtremeSearchResult](#schemaextremesearchresult)]|false|No description
» airline|string|false|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for selling the traveler this flight - also known as the Validating Carrier. Airlines are specified using <a href="https://en.wikipedia.org/wiki/Airline_codes"><a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a>s</a>
» departure_date|string(date)|false|The date departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd, to go to the above destination
» destination|string|true|The <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city or airport to which the traveler may go, from the provided origin
» price|string|true|The minimum total price for one adult passenger for a round trip from the origin to the destination and back. Always a string, formatted correctly for the provided currency
» return_date|string(date)|false|The date at which the flight from the destination to the origin will depart from the destination. The date is in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd, in the local date of the origin. This field will not be present in the response if the one-way request parameter is set to true.



## ExtremeSearchResult

<a name="schemaextremesearchresult"></a>

```json
{
  "airline": "string",
  "departure_date": "2017-10-04",
  "destination": "string",
  "price": "string",
  "return_date": "2017-10-04"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
airline|string|false|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for selling the traveler this flight - also known as the Validating Carrier. Airlines are specified using <a href="https://en.wikipedia.org/wiki/Airline_codes"><a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a>s</a>
departure_date|string(date)|false|The date departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd, to go to the above destination
destination|string|true|The <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city or airport to which the traveler may go, from the provided origin
price|string|true|The minimum total price for one adult passenger for a round trip from the origin to the destination and back. Always a string, formatted correctly for the provided currency
return_date|string(date)|false|The date at which the flight from the destination to the origin will depart from the destination. The date is in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd, in the local date of the origin. This field will not be present in the response if the one-way request parameter is set to true.



## Fare

<a name="schemafare"></a>

```json
{
  "tax": "string",
  "total_fare": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency



## FareRestrictions

<a name="schemafarerestrictions"></a>

```json
{
  "change_penalties": true,
  "refundable": true
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
change_penalties|boolean|true|Indicates whether this fare allows the itinerary to be changed under some circumstances. Note that a change fee or penalty may apply
refundable|boolean|true|Indicates whether this fare is refundable under some circumstances. Note that a refund charge or penalty may apply



## Fees

<a name="schemafees"></a>

```json
{
  "creditcard_fees": "string",
  "service_fees": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
creditcard_fees|string|false|The cost of any fees for common credit cards, such as Visa or Mastercard, in addition to the total price
service_fees|string|false|The cost of any required service fees in addition to the total price



## FlightReservationBookingInfo

<a name="schemaflightreservationbookinginfo"></a>

```json
{
  "airline_record_locator": "string",
  "booking_code": "string",
  "status": "string",
  "travel_class": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
airline_record_locator|string|true|6 character identifier of this travel record on the airline's system. May be the same as the global record locator.
booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
status|string|true|An enumeration to represent the reservation status for this seat on this flight. For example&colon; CONFIRMED, CANCELLED, RESCHEDULED, FLIGHT_CANCELLED, WAITLISTED.
travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST



## FlightReservationBound

<a name="schemaflightreservationbound"></a>

```json
{
  "flights": [
    {
      "arrives_at": "string",
      "booking_info": {
        "airline_record_locator": "string",
        "booking_code": "string",
        "status": "string",
        "travel_class": "string"
      },
      "departs_at": "string",
      "destination": {
        "airport": "string",
        "terminal": "string"
      },
      "flight_number": "string",
      "id": "string",
      "marketing_airline": "string",
      "operating_airline": "string",
      "origin": {
        "airport": "string",
        "terminal": "string"
      },
      "traveler_ids": [
        "string"
      ]
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
flights|[[FlightReservationSegment](#schemaflightreservationsegment)]|false|The individual flights that make up this itinerary. These flights are presented in the order required to fly from the origin to the destination, and the array of flights represents a connection.
» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
» booking_info|[FlightReservationBookingInfo](#schemaflightreservationbookinginfo)|true|No description
»» airline_record_locator|string|true|6 character identifier of this travel record on the airline's system. May be the same as the global record locator.
»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»» status|string|true|An enumeration to represent the reservation status for this seat on this flight. For example&colon; CONFIRMED, CANCELLED, RESCHEDULED, FLIGHT_CANCELLED, WAITLISTED.
»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
» destination|[Airport](#schemaairport)|true|No description
»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
» id|string|true|Uniquely identifies this flight in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
» origin|[Airport](#schemaairport)|true|No description
»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this ticket applies.



## FlightReservationSegment

<a name="schemaflightreservationsegment"></a>

```json
{
  "arrives_at": "string",
  "booking_info": {
    "airline_record_locator": "string",
    "booking_code": "string",
    "status": "string",
    "travel_class": "string"
  },
  "departs_at": "string",
  "destination": {
    "airport": "string",
    "terminal": "string"
  },
  "flight_number": "string",
  "id": "string",
  "marketing_airline": "string",
  "operating_airline": "string",
  "origin": {
    "airport": "string",
    "terminal": "string"
  },
  "traveler_ids": [
    "string"
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
booking_info|[FlightReservationBookingInfo](#schemaflightreservationbookinginfo)|true|No description
» airline_record_locator|string|true|6 character identifier of this travel record on the airline's system. May be the same as the global record locator.
» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
» status|string|true|An enumeration to represent the reservation status for this seat on this flight. For example&colon; CONFIRMED, CANCELLED, RESCHEDULED, FLIGHT_CANCELLED, WAITLISTED.
» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
destination|[Airport](#schemaairport)|true|No description
» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
id|string|true|Uniquely identifies this flight in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
origin|[Airport](#schemaairport)|true|No description
» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this ticket applies.



## FlightSearchBookingInfo

<a name="schemaflightsearchbookinginfo"></a>

```json
{
  "booking_code": "string",
  "cabin_code": "string",
  "fare_basis": "string",
  "fare_family": "string",
  "seats_remaining": "string",
  "travel_class": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST



## FlightSearchBound

<a name="schemaflightsearchbound"></a>

```json
{
  "duration": "string",
  "flights": [
    {
      "aircraft": "string",
      "arrives_at": "string",
      "booking_info": {
        "booking_code": "string",
        "cabin_code": "string",
        "fare_basis": "string",
        "fare_family": "string",
        "seats_remaining": "string",
        "travel_class": "string"
      },
      "departs_at": "string",
      "destination": {
        "airport": "string",
        "terminal": "string"
      },
      "flight_number": "string",
      "marketing_airline": "string",
      "operating_airline": "string",
      "origin": {
        "airport": "string",
        "terminal": "string"
      }
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
duration|string|false|The duration of this bound, including layover time, expressed in the format hh:mm
flights|[[FlightSearchSegment](#schemaflightsearchsegment)]|false|No description
» aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
» booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
»» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
»» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
»» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
» destination|[Airport](#schemaairport)|true|No description
»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
» origin|[Airport](#schemaairport)|true|No description
»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport



## FlightSearchItinerary

<a name="schemaflightsearchitinerary"></a>

```json
{
  "inbound": {
    "duration": "string",
    "flights": [
      {
        "aircraft": "string",
        "arrives_at": "string",
        "booking_info": {
          "booking_code": "string",
          "cabin_code": "string",
          "fare_basis": "string",
          "fare_family": "string",
          "seats_remaining": "string",
          "travel_class": "string"
        },
        "departs_at": "string",
        "destination": {
          "airport": "string",
          "terminal": "string"
        },
        "flight_number": "string",
        "marketing_airline": "string",
        "operating_airline": "string",
        "origin": {
          "airport": "string",
          "terminal": "string"
        }
      }
    ]
  },
  "outbound": {
    "duration": "string",
    "flights": [
      {
        "aircraft": "string",
        "arrives_at": "string",
        "booking_info": {
          "booking_code": "string",
          "cabin_code": "string",
          "fare_basis": "string",
          "fare_family": "string",
          "seats_remaining": "string",
          "travel_class": "string"
        },
        "departs_at": "string",
        "destination": {
          "airport": "string",
          "terminal": "string"
        },
        "flight_number": "string",
        "marketing_airline": "string",
        "operating_airline": "string",
        "origin": {
          "airport": "string",
          "terminal": "string"
        }
      }
    ]
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
inbound|[FlightSearchBound](#schemaflightsearchbound)|false|No description
» duration|string|false|The duration of this bound, including layover time, expressed in the format hh:mm
» flights|[[FlightSearchSegment](#schemaflightsearchsegment)]|false|No description
»» aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»» booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
»»» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
»»» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
»»» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»» destination|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»» origin|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
outbound|[FlightSearchBound](#schemaflightsearchbound)|true|No description
» duration|string|false|The duration of this bound, including layover time, expressed in the format hh:mm
» flights|[[FlightSearchSegment](#schemaflightsearchsegment)]|false|No description
»» aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»» booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
»»» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
»»» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
»»» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»» destination|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»» origin|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport



## FlightSearchPrice

<a name="schemaflightsearchprice"></a>

```json
{
  "price_per_adult": {
    "tax": "string",
    "total_fare": "string"
  },
  "price_per_child": {
    "tax": "string",
    "total_fare": "string"
  },
  "price_per_infant": {
    "tax": "string",
    "total_fare": "string"
  },
  "restrictions": {
    "change_penalties": true,
    "refundable": true
  },
  "total_price": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
price_per_adult|[Fare](#schemafare)|true|No description
» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
price_per_child|[Fare](#schemafare)|false|No description
» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
price_per_infant|[Fare](#schemafare)|false|No description
» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
restrictions|[FareRestrictions](#schemafarerestrictions)|true|No description
» change_penalties|boolean|true|Indicates whether this fare allows the itinerary to be changed under some circumstances. Note that a change fee or penalty may apply
» refundable|boolean|true|Indicates whether this fare is refundable under some circumstances. Note that a refund charge or penalty may apply
total_price|string|true|The total price for all the requested passengers for this flight



## FlightSearchSegment

<a name="schemaflightsearchsegment"></a>

```json
{
  "aircraft": "string",
  "arrives_at": "string",
  "booking_info": {
    "booking_code": "string",
    "cabin_code": "string",
    "fare_basis": "string",
    "fare_family": "string",
    "seats_remaining": "string",
    "travel_class": "string"
  },
  "departs_at": "string",
  "destination": {
    "airport": "string",
    "terminal": "string"
  },
  "flight_number": "string",
  "marketing_airline": "string",
  "operating_airline": "string",
  "origin": {
    "airport": "string",
    "terminal": "string"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
destination|[Airport](#schemaairport)|true|No description
» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
origin|[Airport](#schemaairport)|true|No description
» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport



## FlightTicket

<a name="schemaflightticket"></a>

```json
{
  "flight_bounds": [
    {
      "flights": [
        {
          "arrives_at": "string",
          "booking_info": {
            "airline_record_locator": "string",
            "booking_code": "string",
            "status": "string",
            "travel_class": "string"
          },
          "departs_at": "string",
          "destination": {
            "airport": "string",
            "terminal": "string"
          },
          "flight_number": "string",
          "id": "string",
          "marketing_airline": "string",
          "operating_airline": "string",
          "origin": {
            "airport": "string",
            "terminal": "string"
          },
          "traveler_ids": [
            "string"
          ]
        }
      ]
    }
  ],
  "id": "string",
  "price": {
    "amount": "string",
    "currency": "string"
  },
  "traveler_ids": [
    "string"
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|true|Uniquely identifies this ticket in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
flight_bounds|[[FlightReservationBound](#schemaflightreservationbound)]|false|The flight itinerary for this ticket.
» flights|[[FlightReservationSegment](#schemaflightreservationsegment)]|false|The individual flights that make up this itinerary. These flights are presented in the order required to fly from the origin to the destination, and the array of flights represents a connection.
»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»» booking_info|[FlightReservationBookingInfo](#schemaflightreservationbookinginfo)|true|No description
»»» airline_record_locator|string|true|6 character identifier of this travel record on the airline's system. May be the same as the global record locator.
»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»» status|string|true|An enumeration to represent the reservation status for this seat on this flight. For example&colon; CONFIRMED, CANCELLED, RESCHEDULED, FLIGHT_CANCELLED, WAITLISTED.
»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»» destination|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»» id|string|true|Uniquely identifies this flight in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»» origin|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this ticket applies.
traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this ticket applies.



## FlightTrafficSearchResult

<a name="schemaflighttrafficsearchresult"></a>

```json
{
  "destination": "string",
  "flights": 0,
  "period": "string",
  "travelers": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
destination|string|true|The <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city or airport to which the traveler may go, from the provided origin
flights|integer|false|Number of flights from origin to destination during the search period provided. This field is deprecated.
period|string|true|The date period, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format YYYY-MM or YYYY
travelers|integer|true|Number of passengers from origin to destination during the search period provided



## FrequentTravelerCard

<a name="schemafrequenttravelercard"></a>

```json
{
  "card_number": "string",
  "company_code": "string",
  "issuer_type": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
card_number|string|true|The identifying number (or string) marked on the card. For example&colon; 12345678.
company_code|string|true|The identifying code of the issuer, within the context of its type. For example&colon; BA (and if the issuer type is AIRLINE, this indicates BA=British Airways).
issuer_type|string|true|The type of organization that issued the card. This is an enumeration, possible values are AIRLINE, HOTEL_CHAIN, RENTAL_CAR_PROVIDER, RAILWAY.



## Geolocation

<a name="schemageolocation"></a>

```json
{
  "google_maps_link": "string",
  "latitude": 0,
  "longitude": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180



## HotelPropertyResponse

<a name="schemahotelpropertyresponse"></a>

```json
{
  "address": {
    "city": "string",
    "country": "string",
    "line1": "string",
    "postal_code": "string",
    "region": "string"
  },
  "amenities": [
    {
      "amenity": "string",
      "description": "string",
      "ota_code": "string"
    }
  ],
  "awards": [
    {
      "provider": "string",
      "rating": "string"
    }
  ],
  "contacts": [
    {
      "detail": "string",
      "purpose": "string",
      "type": "string"
    }
  ],
  "images": [
    {
      "category": "string",
      "height": 0,
      "url": "string",
      "width": 0
    }
  ],
  "location": {
    "google_maps_link": "string",
    "latitude": 0,
    "longitude": 0
  },
  "min_daily_rate": {
    "amount": "string",
    "currency": "string"
  },
  "more_rooms_at_this_hotel": {
    "href": "string"
  },
  "property_code": "string",
  "property_name": "string",
  "rooms": [
    {
      "booking_code": "string",
      "descriptions": [
        "string"
      ],
      "rate_plan_code": "string",
      "rate_type_code": "string",
      "rates": [
        {
          "currency": "string",
          "end_date": "2017-10-04",
          "price": 0,
          "start_date": "2017-10-04"
        }
      ],
      "room_type_code": "string",
      "room_type_info": {
        "bed_type": "string",
        "number_of_beds": "string",
        "room_type": "string"
      },
      "total_amount": {
        "amount": "string",
        "currency": "string"
      }
    }
  ],
  "total_price": {
    "amount": "string",
    "currency": "string"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
address|[Address](#schemaaddress)|false|An object to describe a postal address.
» city|string|true|The town or city in which place is located.
» country|string|true|The <a href="http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">ISO 3166-1 alpha-2 country code</a> country code of this address.
» line1|string|true|The first line of this place's address. Generally represents the basic street address.
» postal_code|string|false|The postal or zip code of this address.
» region|string|false|The state or region code in which the place is located.
location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
min_daily_rate|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
more_rooms_at_this_hotel|[Link](#schemalink)|false|No description
» href|string(url)|true|Hyperlink reference URL to the target
property_code|string|true|The 8 character property code of this given hotel. The first 2 characters of this code are the chain code that can be specified in the input. The remaining elements are proprietary to each hotel chain.
property_name|string|true|The name of this hotel.
total_price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
amenities|[[Amenity](#schemaamenity)]|false|An array of amenity objects to the user what facilities this hotel might provide, such as a pool or parking.  If this array is empty, it does not necessarily mean that there are no amenities available at this hotel, it could also mean that the hotel does not list their amenities in our search! 
» amenity|string|false|<a href="hotels-api-supported-amenities-filter">The amenity code</a>
» description|string|false|The decoded text description for this amenity code, where available.
» ota_code|string|false|The <a href="http://www.opentravel.org/">Open Travel Alliance</a> <a href="ota-hotel-amenity-code-table">Hotel Amenities Code</a> for this amenity.
awards|[[Award](#schemaaward)]|false|An array of hotel award objects to give the user an expectation of the service quality at this hotel. This can be used to indicate, for example, the star rating of a hotel. If this array is empty, it does not necessarily mean that the hotel has no awards, it could simply mean that they didn't tell us about them!
» provider|string|true|The organization that issued the award. For example&colon;. Local Star Rating, AAA.
» rating|string|true|The level of the award that was awarded on the provider's scale. For example&colon; 4 or RECOMMENDED.
contacts|[[Contact](#schemacontact)]|false|An array of contact objects to tell the user how to contact the hotel. Typically includes a phone and fax number
» detail|string|true|How that contact should be used, eg. a phone number
» purpose|string|false|The reason or channel of that contact method. For example&colon; HOME, EMERGENCY, MOBILE.
» type|string|true|The method of contact, such as phone or fax.
images|[[Image](#schemaimage)]|false|A selection of image objects, showing pictures of the hotel building, the entrance or some rooms, to give an indication of what to expect at this hotel. Note that redistribution of images outside Amadeus products requires licensing from our image providers: Leonardo and Ice Portal. Thus image links are returned for whitelisted Amadeus users only.
» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
» height|integer|false|The pixel height of the image at the provided URL.
» url|string|true|The URL of the hotel image of this given category and size, for display.
» width|integer|false|The pixel width of the image at the provided URL.
rooms|[[HotelRoom](#schemahotelroom)]|false|Information on currently available rooms at this hotel.
» booking_code|string|true|The booking code identifies a product at the hotel. It can be used to book a room.
» rate_plan_code|string|false|A 3 letter code to designate different rates base on traveler type.
» rate_type_code|string|false|The unique rate code used by the hotel chain to price this room's rate
» room_type_code|string|false|A 3-letter code to identify a specific room type.
» room_type_info|[RoomInfo](#schemaroominfo)|false|More detailed structured information about the room.
»» bed_type|string|true|The type of bed or beds in the room, such as Double, or King.
»» number_of_beds|string|true|The number of beds in the room. May be an integer or a free-text dessciption, as provided by the hotel
»» room_type|string|true|Free-text indicating the type of room - such Smoking, No Smoking, Suite, etc..
» total_amount|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
» descriptions|[string]|false|An array of description strings describing room and rate types features
» rates|[[PeriodRate](#schemaperiodrate)]|false|The total price of staying in this room from the given check-in date to the given check-out date
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code of this rate.
»» end_date|string(date)|true|The date on which this rate ends, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
»» price|number|true|Total amount in the given currency per day of this rate, formatted appropriately. For example&colon; 194.99.
»» start_date|string(date)|true|The start date of this rate, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.



## HotelReservation

<a name="schemahotelreservation"></a>

```json
{
  "booking_info": {
    "reservation_code": "string",
    "status": "string"
  },
  "check_in": "2017-10-04",
  "check_out": "2017-10-04",
  "id": "string",
  "property_code": "string",
  "property_name": "string",
  "total_price": {
    "amount": "string",
    "currency": "string"
  },
  "traveler_ids": [
    "string"
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
booking_info|[HotelReservationBookingInfo](#schemahotelreservationbookinginfo)|true|No description
» reservation_code|string|true|The identifier of this reservation in the hotel chain's system. This should be provided at the check-in desk to identify your reservation.
» status|string|true|An enumeration to represent the reservation status for this hotel reservation. For example&colon; CONFIRMED, CANCELLED, REQUESTED.
check_in|string(date)|true|Date on which the guest will begin their stay in the hotel, in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
check_out|string(date)|true|Date on which the guest will end their stay in the hotel, in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
id|string|true|Uniquely identifies this hotel room reservation in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
property_code|string|true|The 8 character property code of this given hotel. The first 2 characters of this code are the chain code that can be specified in the input. The remaining elements are proprietary to each hotel chain.
property_name|string|true|The name of this hotel.
total_price|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this hotel room reservation applies. Generally all non-infant room occupants will be marked in this array.



## HotelReservationBookingInfo

<a name="schemahotelreservationbookinginfo"></a>

```json
{
  "reservation_code": "string",
  "status": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
reservation_code|string|true|The identifier of this reservation in the hotel chain's system. This should be provided at the check-in desk to identify your reservation.
status|string|true|An enumeration to represent the reservation status for this hotel reservation. For example&colon; CONFIRMED, CANCELLED, REQUESTED.



## HotelRoom

<a name="schemahotelroom"></a>

```json
{
  "booking_code": "string",
  "descriptions": [
    "string"
  ],
  "rate_plan_code": "string",
  "rate_type_code": "string",
  "rates": [
    {
      "currency": "string",
      "end_date": "2017-10-04",
      "price": 0,
      "start_date": "2017-10-04"
    }
  ],
  "room_type_code": "string",
  "room_type_info": {
    "bed_type": "string",
    "number_of_beds": "string",
    "room_type": "string"
  },
  "total_amount": {
    "amount": "string",
    "currency": "string"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
booking_code|string|true|The booking code identifies a product at the hotel. It can be used to book a room.
rate_plan_code|string|false|A 3 letter code to designate different rates base on traveler type.
rate_type_code|string|false|The unique rate code used by the hotel chain to price this room's rate
room_type_code|string|false|A 3-letter code to identify a specific room type.
room_type_info|[RoomInfo](#schemaroominfo)|false|More detailed structured information about the room.
» bed_type|string|true|The type of bed or beds in the room, such as Double, or King.
» number_of_beds|string|true|The number of beds in the room. May be an integer or a free-text dessciption, as provided by the hotel
» room_type|string|true|Free-text indicating the type of room - such Smoking, No Smoking, Suite, etc..
total_amount|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
descriptions|[string]|false|An array of description strings describing room and rate types features
rates|[[PeriodRate](#schemaperiodrate)]|false|The total price of staying in this room from the given check-in date to the given check-out date
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code of this rate.
» end_date|string(date)|true|The date on which this rate ends, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
» price|number|true|Total amount in the given currency per day of this rate, formatted appropriately. For example&colon; 194.99.
» start_date|string(date)|true|The start date of this rate, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.



## HotelSearchResponse

<a name="schemahotelsearchresponse"></a>

```json
{
  "results": [
    {
      "address": {
        "city": "string",
        "country": "string",
        "line1": "string",
        "postal_code": "string",
        "region": "string"
      },
      "amenities": [
        {
          "amenity": "string",
          "description": "string",
          "ota_code": "string"
        }
      ],
      "awards": [
        {
          "provider": "string",
          "rating": "string"
        }
      ],
      "contacts": [
        {
          "detail": "string",
          "purpose": "string",
          "type": "string"
        }
      ],
      "images": [
        {
          "category": "string",
          "height": 0,
          "url": "string",
          "width": 0
        }
      ],
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "min_daily_rate": {
        "amount": "string",
        "currency": "string"
      },
      "more_rooms_at_this_hotel": {
        "href": "string"
      },
      "property_code": "string",
      "property_name": "string",
      "rooms": [
        {
          "booking_code": "string",
          "descriptions": [
            "string"
          ],
          "rate_plan_code": "string",
          "rate_type_code": "string",
          "rates": [
            {
              "currency": "string",
              "end_date": "2017-10-04",
              "price": 0,
              "start_date": "2017-10-04"
            }
          ],
          "room_type_code": "string",
          "room_type_info": {
            "bed_type": "string",
            "number_of_beds": "string",
            "room_type": "string"
          },
          "total_amount": {
            "amount": "string",
            "currency": "string"
          }
        }
      ],
      "total_price": {
        "amount": "string",
        "currency": "string"
      }
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
results|[[HotelPropertyResponse](#schemahotelpropertyresponse)]|false|No description
» address|[Address](#schemaaddress)|false|An object to describe a postal address.
»» city|string|true|The town or city in which place is located.
»» country|string|true|The <a href="http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">ISO 3166-1 alpha-2 country code</a> country code of this address.
»» line1|string|true|The first line of this place's address. Generally represents the basic street address.
»» postal_code|string|false|The postal or zip code of this address.
»» region|string|false|The state or region code in which the place is located.
» location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
»» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
»» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
»» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
» min_daily_rate|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
» more_rooms_at_this_hotel|[Link](#schemalink)|false|No description
»» href|string(url)|true|Hyperlink reference URL to the target
» property_code|string|true|The 8 character property code of this given hotel. The first 2 characters of this code are the chain code that can be specified in the input. The remaining elements are proprietary to each hotel chain.
» property_name|string|true|The name of this hotel.
» total_price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
» amenities|[[Amenity](#schemaamenity)]|false|An array of amenity objects to the user what facilities this hotel might provide, such as a pool or parking.  If this array is empty, it does not necessarily mean that there are no amenities available at this hotel, it could also mean that the hotel does not list their amenities in our search! 
»» amenity|string|false|<a href="hotels-api-supported-amenities-filter">The amenity code</a>
»» description|string|false|The decoded text description for this amenity code, where available.
»» ota_code|string|false|The <a href="http://www.opentravel.org/">Open Travel Alliance</a> <a href="ota-hotel-amenity-code-table">Hotel Amenities Code</a> for this amenity.
» awards|[[Award](#schemaaward)]|false|An array of hotel award objects to give the user an expectation of the service quality at this hotel. This can be used to indicate, for example, the star rating of a hotel. If this array is empty, it does not necessarily mean that the hotel has no awards, it could simply mean that they didn't tell us about them!
»» provider|string|true|The organization that issued the award. For example&colon;. Local Star Rating, AAA.
»» rating|string|true|The level of the award that was awarded on the provider's scale. For example&colon; 4 or RECOMMENDED.
» contacts|[[Contact](#schemacontact)]|false|An array of contact objects to tell the user how to contact the hotel. Typically includes a phone and fax number
»» detail|string|true|How that contact should be used, eg. a phone number
»» purpose|string|false|The reason or channel of that contact method. For example&colon; HOME, EMERGENCY, MOBILE.
»» type|string|true|The method of contact, such as phone or fax.
» images|[[Image](#schemaimage)]|false|A selection of image objects, showing pictures of the hotel building, the entrance or some rooms, to give an indication of what to expect at this hotel. Note that redistribution of images outside Amadeus products requires licensing from our image providers: Leonardo and Ice Portal. Thus image links are returned for whitelisted Amadeus users only.
»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»» height|integer|false|The pixel height of the image at the provided URL.
»» url|string|true|The URL of the hotel image of this given category and size, for display.
»» width|integer|false|The pixel width of the image at the provided URL.
» rooms|[[HotelRoom](#schemahotelroom)]|false|Information on currently available rooms at this hotel.
»» booking_code|string|true|The booking code identifies a product at the hotel. It can be used to book a room.
»» rate_plan_code|string|false|A 3 letter code to designate different rates base on traveler type.
»» rate_type_code|string|false|The unique rate code used by the hotel chain to price this room's rate
»» room_type_code|string|false|A 3-letter code to identify a specific room type.
»» room_type_info|[RoomInfo](#schemaroominfo)|false|More detailed structured information about the room.
»»» bed_type|string|true|The type of bed or beds in the room, such as Double, or King.
»»» number_of_beds|string|true|The number of beds in the room. May be an integer or a free-text dessciption, as provided by the hotel
»»» room_type|string|true|Free-text indicating the type of room - such Smoking, No Smoking, Suite, etc..
»» total_amount|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»» descriptions|[string]|false|An array of description strings describing room and rate types features
»» rates|[[PeriodRate](#schemaperiodrate)]|false|The total price of staying in this room from the given check-in date to the given check-out date
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code of this rate.
»»» end_date|string(date)|true|The date on which this rate ends, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
»»» price|number|true|Total amount in the given currency per day of this rate, formatted appropriately. For example&colon; 194.99.
»»» start_date|string(date)|true|The start date of this rate, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.



## Image

<a name="schemaimage"></a>

```json
{
  "category": "string",
  "height": 0,
  "url": "string",
  "width": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
height|integer|false|The pixel height of the image at the provided URL.
url|string|true|The URL of the hotel image of this given category and size, for display.
width|integer|false|The pixel width of the image at the provided URL.



## ImageSize

<a name="schemaimagesize"></a>

```json
{
  "hd": {
    "category": "string",
    "height": 0,
    "url": "string",
    "width": 0
  },
  "large": {
    "category": "string",
    "height": 0,
    "url": "string",
    "width": 0
  },
  "medium": {
    "category": "string",
    "height": 0,
    "url": "string",
    "width": 0
  },
  "small": {
    "category": "string",
    "height": 0,
    "url": "string",
    "width": 0
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
hd|[Image](#schemaimage)|false|No description
» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
» height|integer|false|The pixel height of the image at the provided URL.
» url|string|true|The URL of the hotel image of this given category and size, for display.
» width|integer|false|The pixel width of the image at the provided URL.
large|[Image](#schemaimage)|false|No description
» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
» height|integer|false|The pixel height of the image at the provided URL.
» url|string|true|The URL of the hotel image of this given category and size, for display.
» width|integer|false|The pixel width of the image at the provided URL.
medium|[Image](#schemaimage)|false|No description
» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
» height|integer|false|The pixel height of the image at the provided URL.
» url|string|true|The URL of the hotel image of this given category and size, for display.
» width|integer|false|The pixel width of the image at the provided URL.
small|[Image](#schemaimage)|false|No description
» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
» height|integer|false|The pixel height of the image at the provided URL.
» url|string|true|The URL of the hotel image of this given category and size, for display.
» width|integer|false|The pixel width of the image at the provided URL.



## Infant

<a name="schemainfant"></a>

```json
{
  "date_of_birth": "2017-10-04",
  "first_name": "string",
  "last_name": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
date_of_birth|string(date)|false|An optional <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date indicating the birth date of the infant, as provided by the agent. For example&colon; 1972-02-19.
first_name|string|false|The first name of the infant, as entered by the agent, in upper-case. May include middle names, initials or prefixes.
last_name|string|false|The last name of the infant, as entered by the agent, in upper-case. If no value is provided, the last name of the infant can generally be assumed to be the same as that of the traveler which whom they are associated.



## Link

<a name="schemalink"></a>

```json
{
  "href": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
href|string(url)|true|Hyperlink reference URL to the target



## LocationResponse

<a name="schemalocationresponse"></a>

```json
{
  "airports": [
    {
      "aircraft_movements": 0,
      "city_code": "string",
      "city_name": "string",
      "code": "string",
      "country": "string",
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "name": "string",
      "state": "string",
      "timezone": "string"
    }
  ],
  "city": {
    "code": "string",
    "country": "string",
    "currency": "string",
    "geonames_ID": "string",
    "location": {
      "google_maps_link": "string",
      "latitude": 0,
      "longitude": 0
    },
    "name": "string",
    "state": "string",
    "timezone": "string"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
city|[CityInformation](#schemacityinformation)|false|No description
» code|string|true|The <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of this city. If you intend to make a flight search from the output of this call, I recommend using this as your input parameter as it generally gives the best results.
» country|string|true|The <a href="http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">ISO 3166-1 alpha-2 country code</a> in which this city can be found.
» currency|string|false|The ISO-4217 currency code of the official local currency at this location
» geonames_ID|string|true|The ID of this city in the open-sourced Geonames DB
» location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
»» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
»» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
»» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
» name|string|true|The name of this city, in English
» state|string|false|The state code of this city, if applicable
» timezone|string|true|The <a href="http://en.wikipedia.org/wiki/List_of_tz_database_time_zones">Olson format</a> name of the timezone in which this city is located
airports|[[AirportInformation](#schemaairportinformation)]|false|Information for any IATA airport located in the provided <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city or which corresponds to the provided code
» aircraft_movements|integer|false|The annual number of aircraft movements at that airport.
» city_code|string|true|The three letter <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city of the city in which this airport is located.
» city_name|string|true|The English name of the city in which this airport is located
» code|string|true|The 3 letter IATA airport code of this given airport. You can use this as an input parameter for a low-fare flight search, to get more specific results than the city code, but inspiration search works best using the city code.
» country|string|true|The <a href="http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">ISO 3166-1 alpha-2 country code</a> in which this city can be found.
» location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
»» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
»» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
»» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
» name|string|true|The name of this airport, in UTF-8 format
» state|string|false|The state code of this city, if applicable
» timezone|string|true|The <a href="http://en.wikipedia.org/wiki/List_of_tz_database_time_zones">Olson format</a> name of the timezone in which this airport is located



## Logos

<a name="schemalogos"></a>

```json
{
  "medium": "string",
  "small": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
medium|string|false|URL to logo of resolution 60x60px
small|string|false|URL to logo of resolution 27x27px



## LowFareSearchResponse

<a name="schemalowfaresearchresponse"></a>

```json
{
  "currency": "string",
  "results": [
    {
      "fare": {
        "price_per_adult": {
          "tax": "string",
          "total_fare": "string"
        },
        "price_per_child": {
          "tax": "string",
          "total_fare": "string"
        },
        "price_per_infant": {
          "tax": "string",
          "total_fare": "string"
        },
        "restrictions": {
          "change_penalties": true,
          "refundable": true
        },
        "total_price": "string"
      },
      "itineraries": [
        {
          "inbound": {
            "duration": "string",
            "flights": [
              {
                "aircraft": "string",
                "arrives_at": "string",
                "booking_info": {
                  "booking_code": "string",
                  "cabin_code": "string",
                  "fare_basis": "string",
                  "fare_family": "string",
                  "seats_remaining": "string",
                  "travel_class": "string"
                },
                "departs_at": "string",
                "destination": {
                  "airport": "string",
                  "terminal": "string"
                },
                "flight_number": "string",
                "marketing_airline": "string",
                "operating_airline": "string",
                "origin": {
                  "airport": "string",
                  "terminal": "string"
                }
              }
            ]
          },
          "outbound": {
            "duration": "string",
            "flights": [
              {
                "aircraft": "string",
                "arrives_at": "string",
                "booking_info": {
                  "booking_code": "string",
                  "cabin_code": "string",
                  "fare_basis": "string",
                  "fare_family": "string",
                  "seats_remaining": "string",
                  "travel_class": "string"
                },
                "departs_at": "string",
                "destination": {
                  "airport": "string",
                  "terminal": "string"
                },
                "flight_number": "string",
                "marketing_airline": "string",
                "operating_airline": "string",
                "origin": {
                  "airport": "string",
                  "terminal": "string"
                }
              }
            ]
          }
        }
      ]
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
results|[[LowFareSearchResult](#schemalowfaresearchresult)]|false|No description
» fare|[FlightSearchPrice](#schemaflightsearchprice)|true|No description
»» price_per_adult|[Fare](#schemafare)|true|No description
»»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
»» price_per_child|[Fare](#schemafare)|false|No description
»»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
»» price_per_infant|[Fare](#schemafare)|false|No description
»»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
»» restrictions|[FareRestrictions](#schemafarerestrictions)|true|No description
»»» change_penalties|boolean|true|Indicates whether this fare allows the itinerary to be changed under some circumstances. Note that a change fee or penalty may apply
»»» refundable|boolean|true|Indicates whether this fare is refundable under some circumstances. Note that a refund charge or penalty may apply
»» total_price|string|true|The total price for all the requested passengers for this flight
» itineraries|[[FlightSearchItinerary](#schemaflightsearchitinerary)]|false|No description
»» inbound|[FlightSearchBound](#schemaflightsearchbound)|false|No description
»»» duration|string|false|The duration of this bound, including layover time, expressed in the format hh:mm
»»» flights|[[FlightSearchSegment](#schemaflightsearchsegment)]|false|No description
»»»» aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
»»»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»»»» booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
»»»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»»»» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
»»»»» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
»»»»» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
»»»»» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
»»»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»»»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»»»» destination|[Airport](#schemaairport)|true|No description
»»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»»»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»»»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»»»» origin|[Airport](#schemaairport)|true|No description
»»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»» outbound|[FlightSearchBound](#schemaflightsearchbound)|true|No description
»»» duration|string|false|The duration of this bound, including layover time, expressed in the format hh:mm
»»» flights|[[FlightSearchSegment](#schemaflightsearchsegment)]|false|No description
»»»» aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
»»»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»»»» booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
»»»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»»»» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
»»»»» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
»»»»» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
»»»»» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
»»»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»»»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»»»» destination|[Airport](#schemaairport)|true|No description
»»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»»»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»»»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»»»» origin|[Airport](#schemaairport)|true|No description
»»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport



## LowFareSearchResult

<a name="schemalowfaresearchresult"></a>

```json
{
  "fare": {
    "price_per_adult": {
      "tax": "string",
      "total_fare": "string"
    },
    "price_per_child": {
      "tax": "string",
      "total_fare": "string"
    },
    "price_per_infant": {
      "tax": "string",
      "total_fare": "string"
    },
    "restrictions": {
      "change_penalties": true,
      "refundable": true
    },
    "total_price": "string"
  },
  "itineraries": [
    {
      "inbound": {
        "duration": "string",
        "flights": [
          {
            "aircraft": "string",
            "arrives_at": "string",
            "booking_info": {
              "booking_code": "string",
              "cabin_code": "string",
              "fare_basis": "string",
              "fare_family": "string",
              "seats_remaining": "string",
              "travel_class": "string"
            },
            "departs_at": "string",
            "destination": {
              "airport": "string",
              "terminal": "string"
            },
            "flight_number": "string",
            "marketing_airline": "string",
            "operating_airline": "string",
            "origin": {
              "airport": "string",
              "terminal": "string"
            }
          }
        ]
      },
      "outbound": {
        "duration": "string",
        "flights": [
          {
            "aircraft": "string",
            "arrives_at": "string",
            "booking_info": {
              "booking_code": "string",
              "cabin_code": "string",
              "fare_basis": "string",
              "fare_family": "string",
              "seats_remaining": "string",
              "travel_class": "string"
            },
            "departs_at": "string",
            "destination": {
              "airport": "string",
              "terminal": "string"
            },
            "flight_number": "string",
            "marketing_airline": "string",
            "operating_airline": "string",
            "origin": {
              "airport": "string",
              "terminal": "string"
            }
          }
        ]
      }
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
fare|[FlightSearchPrice](#schemaflightsearchprice)|true|No description
» price_per_adult|[Fare](#schemafare)|true|No description
»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
» price_per_child|[Fare](#schemafare)|false|No description
»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
» price_per_infant|[Fare](#schemafare)|false|No description
»» tax|string|true|The tax applied per-passenger, for this passenger type, for this itinerary. Some of this tax may be refundable in the event of cancellation.
»» total_fare|string|true|The total price, including taxes per-passenger, for this passenger type, for this itinerary. Always a string, formatted correctly for the given currency
» restrictions|[FareRestrictions](#schemafarerestrictions)|true|No description
»» change_penalties|boolean|true|Indicates whether this fare allows the itinerary to be changed under some circumstances. Note that a change fee or penalty may apply
»» refundable|boolean|true|Indicates whether this fare is refundable under some circumstances. Note that a refund charge or penalty may apply
» total_price|string|true|The total price for all the requested passengers for this flight
itineraries|[[FlightSearchItinerary](#schemaflightsearchitinerary)]|false|No description
» inbound|[FlightSearchBound](#schemaflightsearchbound)|false|No description
»» duration|string|false|The duration of this bound, including layover time, expressed in the format hh:mm
»» flights|[[FlightSearchSegment](#schemaflightsearchsegment)]|false|No description
»»» aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
»»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»»» booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
»»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»»» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
»»»» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
»»»» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
»»»» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
»»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»»» destination|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»»» origin|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
» outbound|[FlightSearchBound](#schemaflightsearchbound)|true|No description
»» duration|string|false|The duration of this bound, including layover time, expressed in the format hh:mm
»» flights|[[FlightSearchSegment](#schemaflightsearchsegment)]|false|No description
»»» aircraft|string|false|The <a href="http://www.jacanaent.com/JacTechLib/07Aviation/AircraftTypeCodes.txt">IATA aircraft type designator</a> of aircraft that will be used for this flight
»»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»»» booking_info|[FlightSearchBookingInfo](#schemaflightsearchbookinginfo)|true|No description
»»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»»» cabin_code|string|false|A single character encoding of the travel_class, generally only available on responses from affiliates.
»»»» fare_basis|string|false|See https://en.wikipedia.org/wiki/Fare_basis_code for the fare being offered.
»»»» fare_family|string|false|Enumeration of the type of fare which this airline is providing, eg. VALUE. This is generally only available for affiliate responses.
»»»» seats_remaining|string|true|The minimum number of seats that are still available for this price at the time of search. If the value is a 4 or above, there are often more than this number of seats still available.
»»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»»» destination|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»»» origin|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport



## Message

<a name="schemamessage"></a>

```json
{
  "message": "string",
  "severity": "string",
  "type": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
message|string|true|A free text message that provides more information.
severity|string|true|An indicator of the importance of this message as part of the flow. May be ERROR or INFO.
type|string|true|An indicator of the source or type of message that has been generated. May be USER or SYSTEM.



## NearestAirport

<a name="schemanearestairport"></a>

```json
{
  "aircraft_movements": 0,
  "airport": "string",
  "airport_name": "string",
  "city": "string",
  "city_name": "string",
  "distance": 0,
  "location": {
    "google_maps_link": "string",
    "latitude": 0,
    "longitude": 0
  },
  "state": "string",
  "timezone": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
aircraft_movements|integer|false|The annual number of aircraft movements at that airport.
airport|string|true|The 3 letter IATA airport code of this given airport. You can use this as an input parameter for a low-fare flight search, to get more specific results than the city code, but inspiration search works best using the city code.
airport_name|string|true|The name of this airport, in UTF-8 format
city|string|true|The three letter <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city of the city in which this airport is located.
city_name|string|true|The English name of the city in which this airport is located
distance|number|true|The distance in km from the point specified in the query, to this location
location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
state|string|false|The state code of this city, if applicable
timezone|string|true|The <a href="http://en.wikipedia.org/wiki/List_of_tz_database_time_zones">Olson format</a> name of the timezone in which this airport is located



## OtherReservation

<a name="schemaotherreservation"></a>

```json
{
  "booking_info": {
    "status": "string"
  },
  "date": "2017-10-04",
  "description": "string",
  "id": "string",
  "location": "string",
  "traveler_ids": [
    "string"
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
booking_info|[OtherReservationBookingInfo](#schemaotherreservationbookinginfo)|true|No description
» status|string|true|An enumeration to represent the reservation status for this hotel reservation. For example&colon; CONFIRMED, CANCELLED, REQUESTED, REJECTED, PENDING_CANCELLATION, PENDING_CONFIRMATION.
date|string(date)|true|Date on which this other reservation will begin, in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
description|string|false|A free-text description of this reservation, that will inform you of its functional meaning.
id|string|true|Uniquely identifies this other reservation in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
location|string|true|A 3 letter <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> that identifies where this other reservation will occur.
traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this reservation applies.



## OtherReservationBookingInfo

<a name="schemaotherreservationbookinginfo"></a>

```json
{
  "status": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
status|string|true|An enumeration to represent the reservation status for this hotel reservation. For example&colon; CONFIRMED, CANCELLED, REQUESTED, REJECTED, PENDING_CANCELLATION, PENDING_CONFIRMATION.



## PeriodRate

<a name="schemaperiodrate"></a>

```json
{
  "currency": "string",
  "end_date": "2017-10-04",
  "price": 0,
  "start_date": "2017-10-04"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code of this rate.
end_date|string(date)|true|The date on which this rate ends, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
price|number|true|Total amount in the given currency per day of this rate, formatted appropriately. For example&colon; 194.99.
start_date|string(date)|true|The start date of this rate, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.



## PointOfInterestCity

<a name="schemapointofinterestcity"></a>

```json
{
  "geoname_id": "string",
  "location": {
    "google_maps_link": "string",
    "latitude": 0,
    "longitude": 0
  },
  "name": "string",
  "total_points_of_interest": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
geoname_id|string|false|The Geonames ID of the location that was searched for
location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
name|string|true|The name of the location that was searched for
total_points_of_interest|integer|true|The total number of points_of_interest that YapQ has indexed for this city



## PointOfInterestDetails

<a name="schemapointofinterestdetails"></a>

```json
{
  "description": "string",
  "short_description": "string",
  "wiki_page_link": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
description|string|true|A paragraph describing this point of interest
short_description|string|true|A summary of the given point
wiki_page_link|string|true|A link to this point of interest&quot;s wikipedia page



## PointOfInterestResult

<a name="schemapointofinterestresult"></a>

```json
{
  "categories": [
    "string"
  ],
  "contextual_images": [
    {
      "hd": {
        "category": "string",
        "height": 0,
        "url": "string",
        "width": 0
      },
      "large": {
        "category": "string",
        "height": 0,
        "url": "string",
        "width": 0
      },
      "medium": {
        "category": "string",
        "height": 0,
        "url": "string",
        "width": 0
      },
      "small": {
        "category": "string",
        "height": 0,
        "url": "string",
        "width": 0
      }
    }
  ],
  "details": {
    "description": "string",
    "short_description": "string",
    "wiki_page_link": "string"
  },
  "geoname_id": 0,
  "grades": {
    "city_grade": 0,
    "yapq_grade": 0
  },
  "location": {
    "google_maps_link": "string",
    "latitude": 0,
    "longitude": 0
  },
  "main_image": "string",
  "title": "string",
  "walk_time": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
details|[PointOfInterestDetails](#schemapointofinterestdetails)|false|No description
» description|string|true|A paragraph describing this point of interest
» short_description|string|true|A summary of the given point
» wiki_page_link|string|true|A link to this point of interest&quot;s wikipedia page
geoname_id|integer|false|The GeonamesID of this point of interest, if available
grades|object|true|Result availble grades.
» city_grade|integer|false|The ranking of this point of interest compared to other points in this city. 1 is the highest rated.
» yapq_grade|integer|false|Main YAPQ grade. A grade out of 5 for this point, rated against all points in the world and normalized among selected group of points. 5 is best, 0 is worst.
location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
main_image|string|true|A link to an image of the given location
title|string|true|Display name of a given point of interest
walk_time|number|false|Time in minutes that it takes to walk from the searched coordinates to this Point of Interest
categories|[string]|false|Array of descriptions indicating what type of point of interest this is. You can filter the results to include only certain categories of point of interest using the category input parameter.
contextual_images|[[ImageSize](#schemaimagesize)]|false|Images taken at this point of interest. Note that these images might have nothing to do with the point itself, particularly if you have enabled the social_media parameter
» hd|[Image](#schemaimage)|false|No description
»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»» height|integer|false|The pixel height of the image at the provided URL.
»» url|string|true|The URL of the hotel image of this given category and size, for display.
»» width|integer|false|The pixel width of the image at the provided URL.
» large|[Image](#schemaimage)|false|No description
»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»» height|integer|false|The pixel height of the image at the provided URL.
»» url|string|true|The URL of the hotel image of this given category and size, for display.
»» width|integer|false|The pixel width of the image at the provided URL.
» medium|[Image](#schemaimage)|false|No description
»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»» height|integer|false|The pixel height of the image at the provided URL.
»» url|string|true|The URL of the hotel image of this given category and size, for display.
»» width|integer|false|The pixel width of the image at the provided URL.
» small|[Image](#schemaimage)|false|No description
»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»» height|integer|false|The pixel height of the image at the provided URL.
»» url|string|true|The URL of the hotel image of this given category and size, for display.
»» width|integer|false|The pixel width of the image at the provided URL.



## PointsOfInterestResponse

<a name="schemapointsofinterestresponse"></a>

```json
{
  "current_city": {
    "geoname_id": "string",
    "location": {
      "google_maps_link": "string",
      "latitude": 0,
      "longitude": 0
    },
    "name": "string",
    "total_points_of_interest": 0
  },
  "points_of_interest": [
    {
      "categories": [
        "string"
      ],
      "contextual_images": [
        {
          "hd": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          },
          "large": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          },
          "medium": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          },
          "small": {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          }
        }
      ],
      "details": {
        "description": "string",
        "short_description": "string",
        "wiki_page_link": "string"
      },
      "geoname_id": 0,
      "grades": {
        "city_grade": 0,
        "yapq_grade": 0
      },
      "location": {
        "google_maps_link": "string",
        "latitude": 0,
        "longitude": 0
      },
      "main_image": "string",
      "title": "string",
      "walk_time": 0
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
current_city|[PointOfInterestCity](#schemapointofinterestcity)|false|No description
» geoname_id|string|false|The Geonames ID of the location that was searched for
» location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
»» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
»» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
»» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
» name|string|true|The name of the location that was searched for
» total_points_of_interest|integer|true|The total number of points_of_interest that YapQ has indexed for this city
points_of_interest|[[PointOfInterestResult](#schemapointofinterestresult)]|false|No description
» details|[PointOfInterestDetails](#schemapointofinterestdetails)|false|No description
»» description|string|true|A paragraph describing this point of interest
»» short_description|string|true|A summary of the given point
»» wiki_page_link|string|true|A link to this point of interest&quot;s wikipedia page
» geoname_id|integer|false|The GeonamesID of this point of interest, if available
» grades|object|true|Result availble grades.
»» city_grade|integer|false|The ranking of this point of interest compared to other points in this city. 1 is the highest rated.
»» yapq_grade|integer|false|Main YAPQ grade. A grade out of 5 for this point, rated against all points in the world and normalized among selected group of points. 5 is best, 0 is worst.
» location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
»» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
»» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
»» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
» main_image|string|true|A link to an image of the given location
» title|string|true|Display name of a given point of interest
» walk_time|number|false|Time in minutes that it takes to walk from the searched coordinates to this Point of Interest
» categories|[string]|false|Array of descriptions indicating what type of point of interest this is. You can filter the results to include only certain categories of point of interest using the category input parameter.
» contextual_images|[[ImageSize](#schemaimagesize)]|false|Images taken at this point of interest. Note that these images might have nothing to do with the point itself, particularly if you have enabled the social_media parameter
»» hd|[Image](#schemaimage)|false|No description
»»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»»» height|integer|false|The pixel height of the image at the provided URL.
»»» url|string|true|The URL of the hotel image of this given category and size, for display.
»»» width|integer|false|The pixel width of the image at the provided URL.
»» large|[Image](#schemaimage)|false|No description
»»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»»» height|integer|false|The pixel height of the image at the provided URL.
»»» url|string|true|The URL of the hotel image of this given category and size, for display.
»»» width|integer|false|The pixel width of the image at the provided URL.
»» medium|[Image](#schemaimage)|false|No description
»»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»»» height|integer|false|The pixel height of the image at the provided URL.
»»» url|string|true|The URL of the hotel image of this given category and size, for display.
»»» width|integer|false|The pixel width of the image at the provided URL.
»» small|[Image](#schemaimage)|false|No description
»»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»»» height|integer|false|The pixel height of the image at the provided URL.
»»» url|string|true|The URL of the hotel image of this given category and size, for display.
»»» width|integer|false|The pixel width of the image at the provided URL.



## RailService

<a name="schemarailservice"></a>

```json
{
  "destination_station_id": "string",
  "services": [
    "string"
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
destination_station_id|string|true|ID of the destination rail station.
services|[string]|false|An array of departure times at which trains depart from the origin station to this destination station. Times are in the ISO 8601 YYYY-MM-DDTHH:mm format.



## RailStationAutocompleteResponse

<a name="schemarailstationautocompleteresponse"></a>

```json
{
  "label": "string",
  "value": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
label|string|true|The full name of the station, in UTF-8 format.
value|string|true|The unique identifier of the station. You can use this as an input parameter for a rail search.



## RailStationResponse

<a name="schemarailstationresponse"></a>

```json
{
  "country": "string",
  "id": "string",
  "location": {
    "google_maps_link": "string",
    "latitude": 0,
    "longitude": 0
  },
  "name": "string",
  "short_name": "string",
  "traffic": "string",
  "type": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
country|string|true|The <a href="http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">ISO 3166-1 alpha-2 country code</a> in which this station can be found.
id|string|true|The ID of this station, as provided in the request
location|[Geolocation](#schemageolocation)|true|An object to describe the coordinates of a map location
» google_maps_link|string|false|For YapQ APIs only  - a link to a google map rendering of this location.
» latitude|number|true|The north-south coordinate of this location, in decimal degrees, between -90 and 90
» longitude|number|true|The east-west coordinate of this location, in decimal degrees, between -180 and 180
name|string|true|The name of this station.
short_name|string|true|The shortened name of this station (20 characters max) which may be used in certain cases.
traffic|string|true|An indication of the level of Intercity traffic passing through this station.
type|string|true|The type of code to which this station refers. Some codes represent agglomeration of multiple stations, whereas others represent an individual station. Possible values are AGGLOMERATION and STATION.



## Rate

<a name="schemarate"></a>

```json
{
  "price": {
    "amount": "string",
    "currency": "string"
  },
  "type": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
type|string|true|The type or applicability period of rate being applied. For example&colon; DAILY, WEEKLY, WEEKEND.



## Reservation

<a name="schemareservation"></a>

```json
{
  "cars": [
    {
      "booking_info": {
        "reservation_code": "string",
        "status": "string"
      },
      "car": {
        "estimated_total": {
          "amount": "string",
          "currency": "string"
        },
        "images": [
          {
            "category": "string",
            "height": 0,
            "url": "string",
            "width": 0
          }
        ],
        "rates": [
          {
            "price": {
              "amount": "string",
              "currency": "string"
            },
            "type": "string"
          }
        ],
        "vehicle_info": {
          "acriss_code": "string",
          "air_conditioning": true,
          "category": "string",
          "fuel": "string",
          "transmission": "string",
          "type": "string"
        }
      },
      "drop_off": "string",
      "id": "string",
      "origin": "string",
      "pick_up": "string",
      "provider": {
        "company_code": "string",
        "company_name": "string"
      },
      "traveler_ids": [
        "string"
      ]
    }
  ],
  "flight_tickets": {
    "flight_bounds": [
      {
        "flights": [
          {
            "arrives_at": "string",
            "booking_info": {
              "airline_record_locator": "string",
              "booking_code": "string",
              "status": "string",
              "travel_class": "string"
            },
            "departs_at": "string",
            "destination": {
              "airport": "string",
              "terminal": "string"
            },
            "flight_number": "string",
            "id": "string",
            "marketing_airline": "string",
            "operating_airline": "string",
            "origin": {
              "airport": "string",
              "terminal": "string"
            },
            "traveler_ids": [
              "string"
            ]
          }
        ]
      }
    ],
    "id": "string",
    "price": {
      "amount": "string",
      "currency": "string"
    },
    "traveler_ids": [
      "string"
    ]
  },
  "hotels": [
    {
      "booking_info": {
        "reservation_code": "string",
        "status": "string"
      },
      "check_in": "2017-10-04",
      "check_out": "2017-10-04",
      "id": "string",
      "property_code": "string",
      "property_name": "string",
      "total_price": {
        "amount": "string",
        "currency": "string"
      },
      "traveler_ids": [
        "string"
      ]
    }
  ],
  "others": [
    {
      "booking_info": {
        "status": "string"
      },
      "date": "2017-10-04",
      "description": "string",
      "id": "string",
      "location": "string",
      "traveler_ids": [
        "string"
      ]
    }
  ],
  "unticketed_flights": [
    {
      "flights": [
        {
          "arrives_at": "string",
          "booking_info": {
            "airline_record_locator": "string",
            "booking_code": "string",
            "status": "string",
            "travel_class": "string"
          },
          "departs_at": "string",
          "destination": {
            "airport": "string",
            "terminal": "string"
          },
          "flight_number": "string",
          "id": "string",
          "marketing_airline": "string",
          "operating_airline": "string",
          "origin": {
            "airport": "string",
            "terminal": "string"
          },
          "traveler_ids": [
            "string"
          ]
        }
      ]
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
flight_tickets|[FlightTicket](#schemaflightticket)|false|The flight itineraries with a ticket or transitional stored ticket (TST) in this reservation, and their prices.
» id|string|true|Uniquely identifies this ticket in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
» price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
» flight_bounds|[[FlightReservationBound](#schemaflightreservationbound)]|false|The flight itinerary for this ticket.
»» flights|[[FlightReservationSegment](#schemaflightreservationsegment)]|false|The individual flights that make up this itinerary. These flights are presented in the order required to fly from the origin to the destination, and the array of flights represents a connection.
»»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»»» booking_info|[FlightReservationBookingInfo](#schemaflightreservationbookinginfo)|true|No description
»»»» airline_record_locator|string|true|6 character identifier of this travel record on the airline's system. May be the same as the global record locator.
»»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»»» status|string|true|An enumeration to represent the reservation status for this seat on this flight. For example&colon; CONFIRMED, CANCELLED, RESCHEDULED, FLIGHT_CANCELLED, WAITLISTED.
»»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»»» destination|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»»» id|string|true|Uniquely identifies this flight in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
»»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»»» origin|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this ticket applies.
» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this ticket applies.
cars|[[CarReservation](#schemacarreservation)]|false|The rental cars reserved.
» booking_info|[CarReservationBookingInfo](#schemacarreservationbookinginfo)|false|No description
»» reservation_code|string|true|The identifier of this reservation in the car rental provider's system. This should be provided at the rental office to identify your reservation.
»» status|string|true|An enumeration to represent the reservation status for this car rental. For example&colon; CONFIRMED, CANCELLED, REQUESTED, REJECTED, PENDING_CANCELLATION, PENDING_CONFIRMATION.
» car|[Vehicle](#schemavehicle)|true|No description
»» estimated_total|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»» vehicle_info|[VehicleInfo](#schemavehicleinfo)|true|No description
»»» acriss_code|string|true|The 4 letter <a href="http://en.wikipedia.org/wiki/ACRISS_Car_Classification_Code">ACRISS code</a> that defines the properties of vehicle being rented.
»»» air_conditioning|boolean|false|The decoded ACRISS air_conditioning information, to let you know if this vehicle has air conditioning
»»» category|string|true|The decoded ACRISS vehicle category (For example&colon; Economy, Luxury, Standard).
»»» fuel|string|false|The decoded ACRISS fuel type, to let you know if this vehicle is hybrid, electric, etc.
»»» transmission|string|false|The decoded ACRISS transmission type, to let you know if this vehicle is Automatic or Manual Transmission (stick-shift).
»»» type|string|false|The decoded ACRISS vehicle type, to let you know what kind of vehicle this is (For example&colon; Van, SUV, Pickup).
»» images|[[Image](#schemaimage)]|false|An image to give an indication of what to expect when renting this vehicle.
»»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»»» height|integer|false|The pixel height of the image at the provided URL.
»»» url|string|true|The URL of the hotel image of this given category and size, for display.
»»» width|integer|false|The pixel width of the image at the provided URL.
»» rates|[[Rate](#schemarate)]|false|Rates that will be applied during the duration of the car rental requested. These rates are generally not inclusive of tax and are used by the car rental company to compute the total cost at the end of the rental period.
»»» price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»»» type|string|true|The type or applicability period of rate being applied. For example&colon; DAILY, WEEKLY, WEEKEND.
» drop_off|string|true|Date at which the car rental will end and the car will be returned to the rental location. <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-ddTHH.
» id|string|true|Uniquely identifies this car rental reservation in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
» origin|string|true|This car rental company office location ID. If this is an airport location, this will be the airport's <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a>. Otherwise, this is a custom value provided by the car rental provider.
» pick_up|string|true|Date on which the car rental will be collected from the car rental location. <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-ddTHH.
» provider|[Company](#schemacompany)|true|No description
»» company_code|string|true|The Amadeus 2-character company code of this provider.
»» company_name|string|true|The long name of the provider corresponding to the above code.
» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this car rental applies. Generally, only drivers of the vehicle will be marked in this array.
hotels|[[HotelReservation](#schemahotelreservation)]|false|The hotel room bookings in this reservation.
» booking_info|[HotelReservationBookingInfo](#schemahotelreservationbookinginfo)|true|No description
»» reservation_code|string|true|The identifier of this reservation in the hotel chain's system. This should be provided at the check-in desk to identify your reservation.
»» status|string|true|An enumeration to represent the reservation status for this hotel reservation. For example&colon; CONFIRMED, CANCELLED, REQUESTED.
» check_in|string(date)|true|Date on which the guest will begin their stay in the hotel, in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
» check_out|string(date)|true|Date on which the guest will end their stay in the hotel, in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
» id|string|true|Uniquely identifies this hotel room reservation in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
» property_code|string|true|The 8 character property code of this given hotel. The first 2 characters of this code are the chain code that can be specified in the input. The remaining elements are proprietary to each hotel chain.
» property_name|string|true|The name of this hotel.
» total_price|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this hotel room reservation applies. Generally all non-infant room occupants will be marked in this array.
others|[[OtherReservation](#schemaotherreservation)]|false|Free text information to represent other travel items that may be considered part of the travel itinerary in this reservation.
» booking_info|[OtherReservationBookingInfo](#schemaotherreservationbookinginfo)|true|No description
»» status|string|true|An enumeration to represent the reservation status for this hotel reservation. For example&colon; CONFIRMED, CANCELLED, REQUESTED, REJECTED, PENDING_CANCELLATION, PENDING_CONFIRMATION.
» date|string(date)|true|Date on which this other reservation will begin, in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
» description|string|false|A free-text description of this reservation, that will inform you of its functional meaning.
» id|string|true|Uniquely identifies this other reservation in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
» location|string|true|A 3 letter <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> that identifies where this other reservation will occur.
» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this reservation applies.
unticketed_flights|[[FlightReservationBound](#schemaflightreservationbound)]|false|The flight itineraries in this reservation that have not yet been ticketed or priced.
» flights|[[FlightReservationSegment](#schemaflightreservationsegment)]|false|The individual flights that make up this itinerary. These flights are presented in the order required to fly from the origin to the destination, and the array of flights represents a connection.
»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»» booking_info|[FlightReservationBookingInfo](#schemaflightreservationbookinginfo)|true|No description
»»» airline_record_locator|string|true|6 character identifier of this travel record on the airline's system. May be the same as the global record locator.
»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»» status|string|true|An enumeration to represent the reservation status for this seat on this flight. For example&colon; CONFIRMED, CANCELLED, RESCHEDULED, FLIGHT_CANCELLED, WAITLISTED.
»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»» destination|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»» id|string|true|Uniquely identifies this flight in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»» origin|[Airport](#schemaairport)|true|No description
»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this ticket applies.



## RestrictedRate

<a name="schemarestrictedrate"></a>

```json
{
  "rate_code": "string",
  "rate_name": "string",
  "restrictions": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
rate_code|string|true|The unique identifier of this rate.
rate_name|string|true|The name used by the company to describe this rate.
restrictions|string|true|An enumeration of the type of restrictions associated with this rate.



## RoomInfo

<a name="schemaroominfo"></a>

```json
{
  "bed_type": "string",
  "number_of_beds": "string",
  "room_type": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
bed_type|string|true|The type of bed or beds in the room, such as Double, or King.
number_of_beds|string|true|The number of beds in the room. May be an integer or a free-text dessciption, as provided by the hotel
room_type|string|true|Free-text indicating the type of room - such Smoking, No Smoking, Suite, etc..



## Station

<a name="schemastation"></a>

```json
{
  "station_code": "string",
  "station_name": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
station_code|string|true|ID of this rail station
station_name|string|true|Full name of this rail station.



## TopDestinationsSearchResponse

<a name="schematopdestinationssearchresponse"></a>

```json
{
  "origin": "string",
  "period": "string",
  "results": [
    {
      "destination": "string",
      "flights": 0,
      "travelers": 0
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
origin|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a>
period|string|true|The date period, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format YYYY-MM or YYYY
results|[[TopDestinationsSearchResult](#schematopdestinationssearchresult)]|false|No description
» destination|string|true|The <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city or airport to which the traveler may go, from the provided origin
» flights|integer|false|Number of flights from origin to destination during the search period provided. This field is deprecated.
» travelers|integer|true|Number of passengers from origin to destination during the search period provided



## TopDestinationsSearchResult

<a name="schematopdestinationssearchresult"></a>

```json
{
  "destination": "string",
  "flights": 0,
  "travelers": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
destination|string|true|The <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city or airport to which the traveler may go, from the provided origin
flights|integer|false|Number of flights from origin to destination during the search period provided. This field is deprecated.
travelers|integer|true|Number of passengers from origin to destination during the search period provided



## TopSearchesSearchResponse

<a name="schematopsearchessearchresponse"></a>

```json
{
  "destination": "string",
  "market": "string",
  "origin": "string",
  "period": "string",
  "results": [
    {
      "destination": "string",
      "searches": 0,
      "searches_prior_year": 0
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
destination|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a>
market|string|true|Country code
origin|string|true|<a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a>
period|string|true|The date period, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format YYYY-MM or YYYY
results|[[TopSearchesSearchResult](#schematopsearchessearchresult)]|false|No description
» destination|string|true|The <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city or airport to which the traveler may go, from the provided origin
» searches|integer|true|Average number of daily searches for the destination during the search period provided
» searches_prior_year|integer|true|Prior year average number of daily searches for the destination during the search period provided



## TopSearchesSearchResult

<a name="schematopsearchessearchresult"></a>

```json
{
  "destination": "string",
  "searches": 0,
  "searches_prior_year": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
destination|string|true|The <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> of the city or airport to which the traveler may go, from the provided origin
searches|integer|true|Average number of daily searches for the destination during the search period provided
searches_prior_year|integer|true|Prior year average number of daily searches for the destination during the search period provided



## TrainScheduleSearchResponse

<a name="schematrainschedulesearchresponse"></a>

```json
{
  "results": [
    {
      "date": "2017-10-04",
      "origin_station_id": "string",
      "services": [
        {
          "destination_station_id": "string",
          "services": [
            "string"
          ]
        }
      ]
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
results|[[TrainScheduleSearchResult](#schematrainschedulesearchresult)]|false|No description
» date|string(date)|true|The search date provided in the input.
» origin_station_id|string|true|Station ID of the origin station for this search.
» services|[[RailService](#schemarailservice)]|false|Array to describe service to the destinations.
»» destination_station_id|string|true|ID of the destination rail station.
»» services|[string]|false|An array of departure times at which trains depart from the origin station to this destination station. Times are in the ISO 8601 YYYY-MM-DDTHH:mm format.



## TrainScheduleSearchResult

<a name="schematrainschedulesearchresult"></a>

```json
{
  "date": "2017-10-04",
  "origin_station_id": "string",
  "services": [
    {
      "destination_station_id": "string",
      "services": [
        "string"
      ]
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
date|string(date)|true|The search date provided in the input.
origin_station_id|string|true|Station ID of the origin station for this search.
services|[[RailService](#schemarailservice)]|false|Array to describe service to the destinations.
» destination_station_id|string|true|ID of the destination rail station.
» services|[string]|false|An array of departure times at which trains depart from the origin station to this destination station. Times are in the ISO 8601 YYYY-MM-DDTHH:mm format.



## TrainSearchItinerary

<a name="schematrainsearchitinerary"></a>

```json
{
  "trains": [
    {
      "arrival_station": {
        "airport": "string",
        "terminal": "string"
      },
      "arrives_at": "string",
      "departs_at": "string",
      "departure_station": {
        "station_code": "string",
        "station_name": "string"
      },
      "marketing_company": "string",
      "operating_company": "string",
      "prices": [
        {
          "accomodation": "string",
          "booking_code": "string",
          "rate": {
            "rate_code": "string",
            "rate_name": "string",
            "restrictions": "string"
          },
          "service_class": "string",
          "total_price": {
            "amount": "string",
            "currency": "string"
          }
        }
      ],
      "train_number": "string",
      "train_type": "string"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
trains|[[TrainSearchSegment](#schematrainsearchsegment)]|false|The array of trains that will be required to complete the given itinerary. Since the cache currently only contains direct itineraries, there will be only one object in this array.
» arrival_station|[Airport](#schemaairport)|true|No description
»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
» arrives_at|string|true|The <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date-time of the train's arrival in the local time zone of the arrival station, in the format YYYY-MM-DDTHH:mm.
» departs_at|string|true|The <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date-time of the train's departure in the local time zone of the departure station, in the format YYYY-MM-DDTHH:mm.
» departure_station|[Station](#schemastation)|true|No description
»» station_code|string|true|ID of this rail station
»» station_name|string|true|Full name of this rail station.
» marketing_company|string|true|The name of the train company selling this train journey. This is the name you should see printed on your ticket.
» operating_company|string|true|The name of the train company operating this train journey. This is the name you should see written on the train.
» train_number|string|true|The identifying number of this train service. Usually the marketing company will only operate on train per day with this train number.
» train_type|string|false|The type of train that you may expect for this journey. For example&colon; InterCity, Regional...
» prices|[[TrainSearchPricing](#schematrainsearchpricing)]|false|Possible pricing for this train journey.
»» accomodation|string|true|A standard enumeration of the mode in which the passenger is accommodated. For example&colon; SEAT, BERTH, CABIN, CARGO, UNKNOWN.
»» booking_code|string|true|A code the identifies the type of booking class being used.
»» rate|[RestrictedRate](#schemarestrictedrate)|true|No description
»»» rate_code|string|true|The unique identifier of this rate.
»»» rate_name|string|true|The name used by the company to describe this rate.
»»» restrictions|string|true|An enumeration of the type of restrictions associated with this rate.
»» service_class|string|true|A standard enumeration of the type of seat, bed or service the passenger can expect.
»» total_price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.



## TrainSearchPricing

<a name="schematrainsearchpricing"></a>

```json
{
  "accomodation": "string",
  "booking_code": "string",
  "rate": {
    "rate_code": "string",
    "rate_name": "string",
    "restrictions": "string"
  },
  "service_class": "string",
  "total_price": {
    "amount": "string",
    "currency": "string"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
accomodation|string|true|A standard enumeration of the mode in which the passenger is accommodated. For example&colon; SEAT, BERTH, CABIN, CARGO, UNKNOWN.
booking_code|string|true|A code the identifies the type of booking class being used.
rate|[RestrictedRate](#schemarestrictedrate)|true|No description
» rate_code|string|true|The unique identifier of this rate.
» rate_name|string|true|The name used by the company to describe this rate.
» restrictions|string|true|An enumeration of the type of restrictions associated with this rate.
service_class|string|true|A standard enumeration of the type of seat, bed or service the passenger can expect.
total_price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.



## TrainSearchSegment

<a name="schematrainsearchsegment"></a>

```json
{
  "arrival_station": {
    "airport": "string",
    "terminal": "string"
  },
  "arrives_at": "string",
  "departs_at": "string",
  "departure_station": {
    "station_code": "string",
    "station_name": "string"
  },
  "marketing_company": "string",
  "operating_company": "string",
  "prices": [
    {
      "accomodation": "string",
      "booking_code": "string",
      "rate": {
        "rate_code": "string",
        "rate_name": "string",
        "restrictions": "string"
      },
      "service_class": "string",
      "total_price": {
        "amount": "string",
        "currency": "string"
      }
    }
  ],
  "train_number": "string",
  "train_type": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
arrival_station|[Airport](#schemaairport)|true|No description
» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
arrives_at|string|true|The <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date-time of the train's arrival in the local time zone of the arrival station, in the format YYYY-MM-DDTHH:mm.
departs_at|string|true|The <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date-time of the train's departure in the local time zone of the departure station, in the format YYYY-MM-DDTHH:mm.
departure_station|[Station](#schemastation)|true|No description
» station_code|string|true|ID of this rail station
» station_name|string|true|Full name of this rail station.
marketing_company|string|true|The name of the train company selling this train journey. This is the name you should see printed on your ticket.
operating_company|string|true|The name of the train company operating this train journey. This is the name you should see written on the train.
train_number|string|true|The identifying number of this train service. Usually the marketing company will only operate on train per day with this train number.
train_type|string|false|The type of train that you may expect for this journey. For example&colon; InterCity, Regional...
prices|[[TrainSearchPricing](#schematrainsearchpricing)]|false|Possible pricing for this train journey.
» accomodation|string|true|A standard enumeration of the mode in which the passenger is accommodated. For example&colon; SEAT, BERTH, CABIN, CARGO, UNKNOWN.
» booking_code|string|true|A code the identifies the type of booking class being used.
» rate|[RestrictedRate](#schemarestrictedrate)|true|No description
»» rate_code|string|true|The unique identifier of this rate.
»» rate_name|string|true|The name used by the company to describe this rate.
»» restrictions|string|true|An enumeration of the type of restrictions associated with this rate.
» service_class|string|true|A standard enumeration of the type of seat, bed or service the passenger can expect.
» total_price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.



## TravelRecordHeader

<a name="schematravelrecordheader"></a>

```json
{
  "creation_office_id": "string",
  "owner_office_id": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
creation_office_id|string|true|9 character Amadeus office identifier of the travel agency that created this travel record. An office ID may be considered as equivalent to a <a href="https://en.wikipedia.org/wiki/Pseudo_city_code">PCC</a> in other reservation systems.
owner_office_id|string|true|9 character Amadeus office identifier of the travel agency that owns and manages this travel record.



## TravelRecordResponse

<a name="schematravelrecordresponse"></a>

```json
{
  "header": {
    "creation_office_id": "string",
    "owner_office_id": "string"
  },
  "messages": [
    {
      "message": "string",
      "severity": "string",
      "type": "string"
    }
  ],
  "record_locator": "string",
  "reservation": {
    "cars": [
      {
        "booking_info": {
          "reservation_code": "string",
          "status": "string"
        },
        "car": {
          "estimated_total": {
            "amount": "string",
            "currency": "string"
          },
          "images": [
            {
              "category": "string",
              "height": 0,
              "url": "string",
              "width": 0
            }
          ],
          "rates": [
            {
              "price": {
                "amount": "string",
                "currency": "string"
              },
              "type": "string"
            }
          ],
          "vehicle_info": {
            "acriss_code": "string",
            "air_conditioning": true,
            "category": "string",
            "fuel": "string",
            "transmission": "string",
            "type": "string"
          }
        },
        "drop_off": "string",
        "id": "string",
        "origin": "string",
        "pick_up": "string",
        "provider": {
          "company_code": "string",
          "company_name": "string"
        },
        "traveler_ids": [
          "string"
        ]
      }
    ],
    "flight_tickets": {
      "flight_bounds": [
        {
          "flights": [
            {
              "arrives_at": "string",
              "booking_info": {
                "airline_record_locator": "string",
                "booking_code": "string",
                "status": "string",
                "travel_class": "string"
              },
              "departs_at": "string",
              "destination": {
                "airport": "string",
                "terminal": "string"
              },
              "flight_number": "string",
              "id": "string",
              "marketing_airline": "string",
              "operating_airline": "string",
              "origin": {
                "airport": "string",
                "terminal": "string"
              },
              "traveler_ids": [
                "string"
              ]
            }
          ]
        }
      ],
      "id": "string",
      "price": {
        "amount": "string",
        "currency": "string"
      },
      "traveler_ids": [
        "string"
      ]
    },
    "hotels": [
      {
        "booking_info": {
          "reservation_code": "string",
          "status": "string"
        },
        "check_in": "2017-10-04",
        "check_out": "2017-10-04",
        "id": "string",
        "property_code": "string",
        "property_name": "string",
        "total_price": {
          "amount": "string",
          "currency": "string"
        },
        "traveler_ids": [
          "string"
        ]
      }
    ],
    "others": [
      {
        "booking_info": {
          "status": "string"
        },
        "date": "2017-10-04",
        "description": "string",
        "id": "string",
        "location": "string",
        "traveler_ids": [
          "string"
        ]
      }
    ],
    "unticketed_flights": [
      {
        "flights": [
          {
            "arrives_at": "string",
            "booking_info": {
              "airline_record_locator": "string",
              "booking_code": "string",
              "status": "string",
              "travel_class": "string"
            },
            "departs_at": "string",
            "destination": {
              "airport": "string",
              "terminal": "string"
            },
            "flight_number": "string",
            "id": "string",
            "marketing_airline": "string",
            "operating_airline": "string",
            "origin": {
              "airport": "string",
              "terminal": "string"
            },
            "traveler_ids": [
              "string"
            ]
          }
        ]
      }
    ]
  },
  "travelers": [
    {
      "contacts": [
        {
          "detail": "string",
          "purpose": "string",
          "type": "string"
        }
      ],
      "date_of_birth": "2017-10-04",
      "first_name": "string",
      "frequent_traveler_cards": [
        {
          "card_number": "string",
          "company_code": "string",
          "issuer_type": "string"
        }
      ],
      "id": "string",
      "infant": {
        "date_of_birth": "2017-10-04",
        "first_name": "string",
        "last_name": "string"
      },
      "last_name": "string",
      "traveler_type": "string"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
header|[TravelRecordHeader](#schematravelrecordheader)|false|No description
» creation_office_id|string|true|9 character Amadeus office identifier of the travel agency that created this travel record. An office ID may be considered as equivalent to a <a href="https://en.wikipedia.org/wiki/Pseudo_city_code">PCC</a> in other reservation systems.
» owner_office_id|string|true|9 character Amadeus office identifier of the travel agency that owns and manages this travel record.
record_locator|string|true|6 character identifier of this travel record on the Amadeus system.
reservation|[Reservation](#schemareservation)|false|No description
» flight_tickets|[FlightTicket](#schemaflightticket)|false|The flight itineraries with a ticket or transitional stored ticket (TST) in this reservation, and their prices.
»» id|string|true|Uniquely identifies this ticket in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
»» price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»» flight_bounds|[[FlightReservationBound](#schemaflightreservationbound)]|false|The flight itinerary for this ticket.
»»» flights|[[FlightReservationSegment](#schemaflightreservationsegment)]|false|The individual flights that make up this itinerary. These flights are presented in the order required to fly from the origin to the destination, and the array of flights represents a connection.
»»»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»»»» booking_info|[FlightReservationBookingInfo](#schemaflightreservationbookinginfo)|true|No description
»»»»» airline_record_locator|string|true|6 character identifier of this travel record on the airline's system. May be the same as the global record locator.
»»»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»»»» status|string|true|An enumeration to represent the reservation status for this seat on this flight. For example&colon; CONFIRMED, CANCELLED, RESCHEDULED, FLIGHT_CANCELLED, WAITLISTED.
»»»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»»»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»»»» destination|[Airport](#schemaairport)|true|No description
»»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»»»» id|string|true|Uniquely identifies this flight in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
»»»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»»»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»»»» origin|[Airport](#schemaairport)|true|No description
»»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»»» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this ticket applies.
»» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this ticket applies.
» cars|[[CarReservation](#schemacarreservation)]|false|The rental cars reserved.
»» booking_info|[CarReservationBookingInfo](#schemacarreservationbookinginfo)|false|No description
»»» reservation_code|string|true|The identifier of this reservation in the car rental provider's system. This should be provided at the rental office to identify your reservation.
»»» status|string|true|An enumeration to represent the reservation status for this car rental. For example&colon; CONFIRMED, CANCELLED, REQUESTED, REJECTED, PENDING_CANCELLATION, PENDING_CONFIRMATION.
»» car|[Vehicle](#schemavehicle)|true|No description
»»» estimated_total|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»»» vehicle_info|[VehicleInfo](#schemavehicleinfo)|true|No description
»»»» acriss_code|string|true|The 4 letter <a href="http://en.wikipedia.org/wiki/ACRISS_Car_Classification_Code">ACRISS code</a> that defines the properties of vehicle being rented.
»»»» air_conditioning|boolean|false|The decoded ACRISS air_conditioning information, to let you know if this vehicle has air conditioning
»»»» category|string|true|The decoded ACRISS vehicle category (For example&colon; Economy, Luxury, Standard).
»»»» fuel|string|false|The decoded ACRISS fuel type, to let you know if this vehicle is hybrid, electric, etc.
»»»» transmission|string|false|The decoded ACRISS transmission type, to let you know if this vehicle is Automatic or Manual Transmission (stick-shift).
»»»» type|string|false|The decoded ACRISS vehicle type, to let you know what kind of vehicle this is (For example&colon; Van, SUV, Pickup).
»»» images|[[Image](#schemaimage)]|false|An image to give an indication of what to expect when renting this vehicle.
»»»» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
»»»» height|integer|false|The pixel height of the image at the provided URL.
»»»» url|string|true|The URL of the hotel image of this given category and size, for display.
»»»» width|integer|false|The pixel width of the image at the provided URL.
»»» rates|[[Rate](#schemarate)]|false|Rates that will be applied during the duration of the car rental requested. These rates are generally not inclusive of tax and are used by the car rental company to compute the total cost at the end of the rental period.
»»»» price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»»»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»»»» type|string|true|The type or applicability period of rate being applied. For example&colon; DAILY, WEEKLY, WEEKEND.
»» drop_off|string|true|Date at which the car rental will end and the car will be returned to the rental location. <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-ddTHH.
»» id|string|true|Uniquely identifies this car rental reservation in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
»» origin|string|true|This car rental company office location ID. If this is an airport location, this will be the airport's <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a>. Otherwise, this is a custom value provided by the car rental provider.
»» pick_up|string|true|Date on which the car rental will be collected from the car rental location. <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-ddTHH.
»» provider|[Company](#schemacompany)|true|No description
»»» company_code|string|true|The Amadeus 2-character company code of this provider.
»»» company_name|string|true|The long name of the provider corresponding to the above code.
»» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this car rental applies. Generally, only drivers of the vehicle will be marked in this array.
» hotels|[[HotelReservation](#schemahotelreservation)]|false|The hotel room bookings in this reservation.
»» booking_info|[HotelReservationBookingInfo](#schemahotelreservationbookinginfo)|true|No description
»»» reservation_code|string|true|The identifier of this reservation in the hotel chain's system. This should be provided at the check-in desk to identify your reservation.
»»» status|string|true|An enumeration to represent the reservation status for this hotel reservation. For example&colon; CONFIRMED, CANCELLED, REQUESTED.
»» check_in|string(date)|true|Date on which the guest will begin their stay in the hotel, in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
»» check_out|string(date)|true|Date on which the guest will end their stay in the hotel, in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
»» id|string|true|Uniquely identifies this hotel room reservation in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
»» property_code|string|true|The 8 character property code of this given hotel. The first 2 characters of this code are the chain code that can be specified in the input. The remaining elements are proprietary to each hotel chain.
»» property_name|string|true|The name of this hotel.
»» total_price|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
»»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
»» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this hotel room reservation applies. Generally all non-infant room occupants will be marked in this array.
» others|[[OtherReservation](#schemaotherreservation)]|false|Free text information to represent other travel items that may be considered part of the travel itinerary in this reservation.
»» booking_info|[OtherReservationBookingInfo](#schemaotherreservationbookinginfo)|true|No description
»»» status|string|true|An enumeration to represent the reservation status for this hotel reservation. For example&colon; CONFIRMED, CANCELLED, REQUESTED, REJECTED, PENDING_CANCELLATION, PENDING_CONFIRMATION.
»» date|string(date)|true|Date on which this other reservation will begin, in the <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date format yyyy-MM-dd.
»» description|string|false|A free-text description of this reservation, that will inform you of its functional meaning.
»» id|string|true|Uniquely identifies this other reservation in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
»» location|string|true|A 3 letter <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA code</a> that identifies where this other reservation will occur.
»» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this reservation applies.
» unticketed_flights|[[FlightReservationBound](#schemaflightreservationbound)]|false|The flight itineraries in this reservation that have not yet been ticketed or priced.
»» flights|[[FlightReservationSegment](#schemaflightreservationsegment)]|false|The individual flights that make up this itinerary. These flights are presented in the order required to fly from the origin to the destination, and the array of flights represents a connection.
»»» arrives_at|string|true|Date and time of departure at the destination, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the destination airport
»»» booking_info|[FlightReservationBookingInfo](#schemaflightreservationbookinginfo)|true|No description
»»»» airline_record_locator|string|true|6 character identifier of this travel record on the airline's system. May be the same as the global record locator.
»»»» booking_code|string|true|The Reservation Booking Designator code that determines the quality and terms of the flight offered for the given price. A single letter from A..Z
»»»» status|string|true|An enumeration to represent the reservation status for this seat on this flight. For example&colon; CONFIRMED, CANCELLED, RESCHEDULED, FLIGHT_CANCELLED, WAITLISTED.
»»»» travel_class|string|true|The cabin class offered on this flight. An enumeration that will read either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST
»»» departs_at|string|true|Date and time of departure at the origin, in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a>  date format yyyy-MM-ddTHH:mm in the local time at the origin airport
»»» destination|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»» flight_number|string|true|The identifier that the airline uses for this flight route. This is most commonly - but not always - a number. When combined with the airline and date, it identifies an individual aircraft's flight
»»» id|string|true|Uniquely identifies this flight in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
»»» marketing_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is responsible for the traveller this flight
»»» operating_airline|string|true|The 2 character alphanumeric <a href="https://en.wikipedia.org/wiki/Airline_codes">IATA airline code</a> of the airline that is providing the aircraft for this flight. Note that in the USA, if the marketing and operating carrier are different, you are legally required to display this in your application.
»»» origin|[Airport](#schemaairport)|true|No description
»»»» airport|string|true|The 3 character <a href="https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code">IATA airport code</a> of the airport in question for this flight
»»»» terminal|string|false|The terminal identifier at which this flight will arrive or depart in the given airport
»»» traveler_ids|[string]|false|Traveler identifiers to indicate the travelers to whom this ticket applies.
messages|[[Message](#schemamessage)]|false|Functional or technical messages associated with the retrieval of this travel record.
» message|string|true|A free text message that provides more information.
» severity|string|true|An indicator of the importance of this message as part of the flow. May be ERROR or INFO.
» type|string|true|An indicator of the source or type of message that has been generated. May be USER or SYSTEM.
travelers|[[Traveler](#schematraveler)]|false|Information about each traveler who may be included as part of this travel record.
» date_of_birth|string(date)|false|An <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date indicating the birth date of the traveler, as provided by the agent. For example&colon; 1972-02-19.
» first_name|string|true|The first name of the passenger, as entered by the agent, in upper-case. May include middle names, initials or prefixes. The total combined length of the first name and last name must be between 2 and 57 characters. For example&colon; ALEXANDRA, JOSE-ANTONIO MR, ELAINE T DR.
» id|string|true|Uniquely identifies this traveler in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
» infant|[Infant](#schemainfant)|false|No description
»» date_of_birth|string(date)|false|An optional <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date indicating the birth date of the infant, as provided by the agent. For example&colon; 1972-02-19.
»» first_name|string|false|The first name of the infant, as entered by the agent, in upper-case. May include middle names, initials or prefixes.
»» last_name|string|false|The last name of the infant, as entered by the agent, in upper-case. If no value is provided, the last name of the infant can generally be assumed to be the same as that of the traveler which whom they are associated.
» last_name|string|true|The last name of the passenger, as entered by the agent, in upper-case. May include suffixes. For example&colon; THACKSTON, KING III, LU.
» traveler_type|string|true|Enumeration of the type of traveler. May be ADULT or CHILD.
» contacts|[[Contact](#schemacontact)]|false|Details on how to contact this traveler. At least one traveler in a travel-record will have a contact element.
»» detail|string|true|How that contact should be used, eg. a phone number
»» purpose|string|false|The reason or channel of that contact method. For example&colon; HOME, EMERGENCY, MOBILE.
»» type|string|true|The method of contact, such as phone or fax.
» frequent_traveler_cards|[[FrequentTravelerCard](#schemafrequenttravelercard)]|false|Information regarding loyalty cards that the traveler would like to use to accrue benefits as part of this travel record. Where possible, the system will attempt to validate that the frequent traveler card is eligible for use in the context of this travel record.
»» card_number|string|true|The identifying number (or string) marked on the card. For example&colon; 12345678.
»» company_code|string|true|The identifying code of the issuer, within the context of its type. For example&colon; BA (and if the issuer type is AIRLINE, this indicates BA=British Airways).
»» issuer_type|string|true|The type of organization that issued the card. This is an enumeration, possible values are AIRLINE, HOTEL_CHAIN, RENTAL_CAR_PROVIDER, RAILWAY.



## Traveler

<a name="schematraveler"></a>

```json
{
  "contacts": [
    {
      "detail": "string",
      "purpose": "string",
      "type": "string"
    }
  ],
  "date_of_birth": "2017-10-04",
  "first_name": "string",
  "frequent_traveler_cards": [
    {
      "card_number": "string",
      "company_code": "string",
      "issuer_type": "string"
    }
  ],
  "id": "string",
  "infant": {
    "date_of_birth": "2017-10-04",
    "first_name": "string",
    "last_name": "string"
  },
  "last_name": "string",
  "traveler_type": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
date_of_birth|string(date)|false|An <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date indicating the birth date of the traveler, as provided by the agent. For example&colon; 1972-02-19.
first_name|string|true|The first name of the passenger, as entered by the agent, in upper-case. May include middle names, initials or prefixes. The total combined length of the first name and last name must be between 2 and 57 characters. For example&colon; ALEXANDRA, JOSE-ANTONIO MR, ELAINE T DR.
id|string|true|Uniquely identifies this traveler in this travel record. This ID is persistent, and remains the same for the lifetime of the travel record.
infant|[Infant](#schemainfant)|false|No description
» date_of_birth|string(date)|false|An optional <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> date indicating the birth date of the infant, as provided by the agent. For example&colon; 1972-02-19.
» first_name|string|false|The first name of the infant, as entered by the agent, in upper-case. May include middle names, initials or prefixes.
» last_name|string|false|The last name of the infant, as entered by the agent, in upper-case. If no value is provided, the last name of the infant can generally be assumed to be the same as that of the traveler which whom they are associated.
last_name|string|true|The last name of the passenger, as entered by the agent, in upper-case. May include suffixes. For example&colon; THACKSTON, KING III, LU.
traveler_type|string|true|Enumeration of the type of traveler. May be ADULT or CHILD.
contacts|[[Contact](#schemacontact)]|false|Details on how to contact this traveler. At least one traveler in a travel-record will have a contact element.
» detail|string|true|How that contact should be used, eg. a phone number
» purpose|string|false|The reason or channel of that contact method. For example&colon; HOME, EMERGENCY, MOBILE.
» type|string|true|The method of contact, such as phone or fax.
frequent_traveler_cards|[[FrequentTravelerCard](#schemafrequenttravelercard)]|false|Information regarding loyalty cards that the traveler would like to use to accrue benefits as part of this travel record. Where possible, the system will attempt to validate that the frequent traveler card is eligible for use in the context of this travel record.
» card_number|string|true|The identifying number (or string) marked on the card. For example&colon; 12345678.
» company_code|string|true|The identifying code of the issuer, within the context of its type. For example&colon; BA (and if the issuer type is AIRLINE, this indicates BA=British Airways).
» issuer_type|string|true|The type of organization that issued the card. This is an enumeration, possible values are AIRLINE, HOTEL_CHAIN, RENTAL_CAR_PROVIDER, RAILWAY.



## Vehicle

<a name="schemavehicle"></a>

```json
{
  "estimated_total": {
    "amount": "string",
    "currency": "string"
  },
  "images": [
    {
      "category": "string",
      "height": 0,
      "url": "string",
      "width": 0
    }
  ],
  "rates": [
    {
      "price": {
        "amount": "string",
        "currency": "string"
      },
      "type": "string"
    }
  ],
  "vehicle_info": {
    "acriss_code": "string",
    "air_conditioning": true,
    "category": "string",
    "fuel": "string",
    "transmission": "string",
    "type": "string"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
estimated_total|[Amount](#schemaamount)|false|A monetary amount with a price and a currency
» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
vehicle_info|[VehicleInfo](#schemavehicleinfo)|true|No description
» acriss_code|string|true|The 4 letter <a href="http://en.wikipedia.org/wiki/ACRISS_Car_Classification_Code">ACRISS code</a> that defines the properties of vehicle being rented.
» air_conditioning|boolean|false|The decoded ACRISS air_conditioning information, to let you know if this vehicle has air conditioning
» category|string|true|The decoded ACRISS vehicle category (For example&colon; Economy, Luxury, Standard).
» fuel|string|false|The decoded ACRISS fuel type, to let you know if this vehicle is hybrid, electric, etc.
» transmission|string|false|The decoded ACRISS transmission type, to let you know if this vehicle is Automatic or Manual Transmission (stick-shift).
» type|string|false|The decoded ACRISS vehicle type, to let you know what kind of vehicle this is (For example&colon; Van, SUV, Pickup).
images|[[Image](#schemaimage)]|false|An image to give an indication of what to expect when renting this vehicle.
» category|string|false|The enumerated category of this image type. Common values include EXTERIOR, GUEST_ROOM, SUITE, LOBBY, RESTAURANT, LOUNGE, LOGO, MAP, MISC and UNKNOWN.
» height|integer|false|The pixel height of the image at the provided URL.
» url|string|true|The URL of the hotel image of this given category and size, for display.
» width|integer|false|The pixel width of the image at the provided URL.
rates|[[Rate](#schemarate)]|false|Rates that will be applied during the duration of the car rental requested. These rates are generally not inclusive of tax and are used by the car rental company to compute the total cost at the end of the rental period.
» price|[Amount](#schemaamount)|true|A monetary amount with a price and a currency
»» amount|string|true|Total amount in the given currency, formatted appropriately. For example&colon; 194.99
»» currency|string|true|<a href="http://en.wikipedia.org/wiki/ISO_4217">ISO 4217</a> currency code.
» type|string|true|The type or applicability period of rate being applied. For example&colon; DAILY, WEEKLY, WEEKEND.



## VehicleInfo

<a name="schemavehicleinfo"></a>

```json
{
  "acriss_code": "string",
  "air_conditioning": true,
  "category": "string",
  "fuel": "string",
  "transmission": "string",
  "type": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
acriss_code|string|true|The 4 letter <a href="http://en.wikipedia.org/wiki/ACRISS_Car_Classification_Code">ACRISS code</a> that defines the properties of vehicle being rented.
air_conditioning|boolean|false|The decoded ACRISS air_conditioning information, to let you know if this vehicle has air conditioning
category|string|true|The decoded ACRISS vehicle category (For example&colon; Economy, Luxury, Standard).
fuel|string|false|The decoded ACRISS fuel type, to let you know if this vehicle is hybrid, electric, etc.
transmission|string|false|The decoded ACRISS transmission type, to let you know if this vehicle is Automatic or Manual Transmission (stick-shift).
type|string|false|The decoded ACRISS vehicle type, to let you know what kind of vehicle this is (For example&colon; Van, SUV, Pickup).





