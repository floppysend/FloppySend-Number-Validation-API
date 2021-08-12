## FloppySend Number Validation API

FloppySend’s Number Validation offers a full-featured yet simple RESTful JSON API for national and international phone number validation and information lookup for a total of 232 countries around the world.

Request Types
 - GET: If the request is get method you need to append params as query string inside the params section
 - POST: If request is post method you need to append params as x-www-form-urlencoded inside the body of the request

```
https://api.floppy.ai/numbervalidation
```
```
{
    X-api-key:"Your x-api-key" (string required)
    X-Secret-Hash:"Your x-secret-hash" 
    (string required if added from dashboard)
}
```
You can get your X-Api-Key And X-Secret-Hash from your [account setting](https://app.floppysend.com/) page in Api Keys section

#### Parameters
  | Parameter | Type | Required | Description |
  | --------- | ---- | -------- | ----------- |
  | Msisdn | String | Yes | number sending to |

#### Number Validation API Responses
```JSON
{
    "Result": "Success",
    "Datainfo": [
        {
            "MSISDN": "{phone_number}",
            "Type": "{number_device_type}",
            "Net": "{number_network}",
            "NetType": "{network_internet_type}",
            "Oop": "{number_operetor}",
            "HCountry": "{number_country}",
            "Ciso": "{number_country}",
            "CC": "{CC}",
            "MCC": "{MCC}",
            "MNC": "{MNC}",
            "Date": "{cheking_date}",
            "Cost": "{cheking_cost}"
        }
    ]
}
```

#### Number Validation API Code Sample

You need to add your "X-Secret-Hash" in the header if you have one.

```PHP
//PHP

<?php

$curl = curl_init();
curl_setopt_array($curl, array(
        CURLOPT_URL => 'https://api.floppy.ai/numbervalidation',
        CURLOPT_RETURNTRANSFER => true,
        CURLOPT_ENCODING => '',
        CURLOPT_MAXREDIRS => 10,
        CURLOPT_TIMEOUT => 0,
        CURLOPT_FOLLOWLOCATION => true,
        CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
        CURLOPT_CUSTOMREQUEST => 'POST',
        CURLOPT_POSTFIELDS => 'Msisdn={phone_number}',
        CURLOPT_HTTPHEADER => array(
        'x-api-key: "Your x-api-key"',
        'Content-Type: application/x-www-form-urlencoded'
        ),
    ));
$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

```ruby
//Ruby

require "uri"
require "net/http"
url = URI("https://api.floppy.ai/numbervalidation")
https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true
request = Net::HTTP::Post.new(url)
request["x-api-key"] = "Your x-api-key"
request["Content-Type"] = "application/x-www-form-urlencoded"
request.body = "Msisdn={phone_number}"
response = https.request(request)
puts response.read_body
```

```Java
//JAVA

//The OkHttpClient is an external package, you need to install it before making the request, 
//And don't forget to add user permission for the internet inside "\MyApplication\app\src\main\AndroidManifest.xml"
//Also, you need to add required dependencies inside "MyApplication\app\build.gradle"

OkHttpClient client = new OkHttpClient().newBuilder()
.build();
MediaType mediaType = MediaType.parse("application/x-www-form-urlencoded");
RequestBody body = RequestBody.create(mediaType, "Msisdn={phone_number}");
Request request = new Request.Builder()
.url("https://api.floppy.ai/numbervalidation")
.method("POST", body)
.addHeader("x-api-key", "Your x-api-key")
.addHeader("Content-Type", "application/x-www-form-urlencoded")
.build();
Response response = client.newCall(request).execute();
```

```C#
//C#

var client = new RestClient("https://api.floppy.ai/numbervalidation");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("x-api-key", "Your x-api-key");
request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddParameter("Msisdn", "{phone_number}");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```JavaScript
//NodeJs
//Make sure to import Axios and install npm packages before doing the request

var axios = require('axios');
var qs = require('qs');
var data = qs.stringify({
 'Msisdn': 'NUMBER' 
});
var config = {
  method: 'post',
  url: 'https://api.floppy.ai/numbervalidation',
  headers: { 
    'x-api-key': 'YOUR-API-KEY',
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  data : data
};

axios(config)
    .then(function (response) {
      console.log(JSON.stringify(response.data));
    })
    .catch(function (error) {
      console.log(error);
    });
```
