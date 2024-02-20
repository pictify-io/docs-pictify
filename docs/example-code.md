# Example Code

To get started quickly, you can use the following code snippets to generate images and gifs using the Pictify API.

## Table of Contents

* [Javascript](#javascript)
* [Python](#python)
* [PHP](#php)
* [Ruby](#ruby)
* [Java](#java)
* [C#](#c)
* [Go](#go)
* [Curl](#curl)

Endpoint for generating Image -:
    
```
POST https://api.pictify.io/image
```

Endpoint for generating Gif -:
    
```
POST https://api.pictify.io/gif
```

All the other parameters are same for both the endpoints.

## Javascript

```javascript
const axios = require('axios');
const data = JSON.stringify({
	"html": "<html><body><h1>Hello World</h1></body></html>"
});
const header = {
	Authorization: 'Bearer access_token',
}
const config = {
	method: 'post',
	url: 'https://api.pictify.io/image',
	headers: header,
	data: data
};
const image = await axios(config);
```


## Python

```python
import requests
import json

url = "https://api.pictify.io/image"

payload = {'html': 'Hello World'}
headers = {'Authorization': 'Bearer access_token', 'Content-Type': 'application/json'}
response = requests.post(url, data=json.dumps(payload), headers=headers)

image = response.json()
```

## PHP

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.pictify.io/image',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "html": "<html><body><h1>Hello World</h1></body></html>"
}',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Bearer access_token',
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);

$image = json_decode($response, true);

?>
```

## Ruby

```ruby

require 'net/http'
require 'uri'
require 'json'

uri = URI.parse("https://api.pictify.io/image")
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true

request = Net::HTTP::Post.new(uri.request_uri)
request["Authorization"] = "Bearer access_token"
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  "html" => "<html><body><h1>Hello World</h1></body></html>"
})

response = http.request(request)
image = JSON.parse(response.body)

```

## Java

```java

import java.io.*;
import java.net.*;
import java.util.*;

public class Main {
  public static void main(String[] args) throws IOException {
    URL url = new URL("https://api.pictify.io/image");
    HttpURLConnection con = (HttpURLConnection) url.openConnection();
    con.setRequestMethod("POST");
    con.setRequestProperty("Authorization", "Bearer access_token");
    con.setRequestProperty("Content-Type", "application/json");
    con.setDoOutput(true);
    String jsonInputString = "{\"html\": \"<html><body><h1>Hello World</h1></body></html>\"}";
    try(OutputStream os = con.getOutputStream()) {
        byte[] input = jsonInputString.getBytes("utf-8");
        os.write(input, 0, input.length);           
    }
    try(BufferedReader br = new BufferedReader(
        new InputStreamReader(con.getInputStream(), "utf-8"))) {
        StringBuilder response = new StringBuilder();
        String responseLine = null;
        while ((responseLine = br.readLine()) != null) {
            response.append(responseLine.trim());
        }
        System.out.println(response.toString());
    }
  }
}

```

## <span>C#</span>



```csharp

using System;
using System.IO;
using System.Net;
using System.Text;

class Program
{
    static readonly HttpClient client = new HttpClient();

    static async Task Main()
    {
        var url = "https://api.pictify.io/image";
        var data = new StringContent("{\"html\": \"<h1>Hello World</h1>\"}", Encoding.UTF8, "application/json");

        client.DefaultRequestHeaders.Add("Authorization", "Bearer access_token");

        var response = await client.PostAsync(url, data);

        string image = await response.Content.ReadAsStringAsync();
    }
}
    
```

## Go

```go

package main
import (
    "bytes"
    "fmt"
    "net/http"
)
func main() {
    url := "https://api.pictify.io/image"
    payload := []byte("{"html": "<html><body><h1>Hello World</h1></body></html>"}")
    req, _ := http.NewRequest("POST", url, bytes.NewBuffer(payload))
    req.Header.Set("Authorization", "Bearer access_token")
    req.Header.Set("Content-Type", "application/json")
    client := &http.Client{}
    resp, err := client.Do(req)
    if err != nil {
        fmt.Println(err)
        return
    }
    defer resp.Body.Close()
    body, _ := ioutil.ReadAll(resp.Body)
}

```

## Curl

```bash
curl --location --request POST 'https://api.pictify.io/image' \
--header 'Authorization: Bearer access_token' \
--header 'Content-Type: application/json' \
--data-raw '{"html": "<h1>Hello World</h1>"}'
```




