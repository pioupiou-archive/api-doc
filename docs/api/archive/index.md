# Archive API

The Archive API provides access to historical measurements from one station.

A single request can retrieve data for up to 31 days.

Output format can be either **JSON**, **csv** or tab-separated **text file**.

## License
To use data from Pioupiou stations, you must comply with the license available on the [Data Licensing](../../data-licensing.md) page.

## Endpoint
```bash
GET http://api.pioupiou.fr/v1/archive/{station_id}?start={start}&stop={stop}&format={format}
```
## Arguments

Name | Description |
-----|----------- |---
{station_id} | Numeric ID of the station | (Required)
{start} | Start date (see below) or "**last-hour**"  or "**last-day**" or "**last-week**" or "**last-month**" | (Required)
{stop} | Stop date (see below) or "**now**" |(Required)
{format} | Output format : "**json**" (default) or "**csv**" or "**txt**" |(Optionnal)

### Dates format

We support the [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) format for passing dates and times. Not specifying a timezone defaults the timezone to UTC.

The full representation is of the format:
```
yyyy-MM-ddTHH:mm:ss.SSSZ
```

This table illustrates some example valid dates and times:

Sample | Description
-------| -----------
2015 | Amounts to 2015-01-01T00:00:00.000Z
2015-08 | Amounts to 2015-08-01T00:00:00.000Z
2015-08-23 | Amounts to 2015-08-23T00:00:00.000Z
2015-08-23T18 | Amounts to 2015-08-23T18:00:00.000Z
2015-08-23T18:45 | Amounts to 2015-08-23T18:45:00.000Z
2015-08-23T18:45Z | Amounts to 2015-08-23T18:45:00.000Z (UTC)
2015-08-23T18:45+0200 | Amounts to 2015-08-23T18:45:00.000+0200 (Paris, CET − Summer DST)
2015-01-01T18:45+0100 | Amounts to 2015-01-01T18:45:00.000+0100 (Paris, CET − Winter DST)

To avoid errors, we recommend always use UTC dates and times.

You can directly use date from [Javascript](http://www.w3schools.com/jsref/jsref_toisostring.asp)'s ```new Date().toISOString()``` or [PHP](http://php.net/manual/en/function.date.php)'s ```date("c")```.

## Responses

The **Live** API provides JSON respo[nses.

### Response examples
#### May 2015, JSON

```bash
$ curl "http://api.pioupiou.fr/v1/archive/1?start=2015-05&stop=2015-06"
```
```json
{
  "doc": "http://developers.pioupiou.fr/api/archive/",
  "license": "http://developers.pioupiou.fr/data-licensing",
  "attribution": "(c) contributors of the Pioupiou wind network <http://pioupiou.fr>",
  "legend": ["time","latitude","longitude","wind_speed_min","wind_speed_avg","wind_speed_max","wind_heading","pressure"],
  "units": ["utc","degrees","degrees","km/h","km/h","km/h","degrees","hPa"],
  "data": [
    ["2015-05-01T00:03:54.000Z",45.30314,5.906867,3,4,5,45,986.9],
    ["2015-05-01T00:07:54.000Z",45.30314,5.906867,1,2,4,67.5,986.8],
    ["2015-05-01T00:11:54.000Z",45.30314,5.906867,0,0,0,67.5,986.8],
    ["2015-05-01T00:15:54.000Z",45.30314,5.906867,0,0,1,67.5,986.8],
    ["2015-05-01T00:19:54.000Z",45.30314,5.906867,0,0,0,0,986.8],
    ["2015-05-01T00:23:54.000Z",45.30314,5.906867,0,1,4,67.5,986.8],
    ...,
    ["2015-05-31T23:37:03.000Z",45.30314,5.906867,1,2,2,90,989.7],
    ["2015-05-31T23:41:03.000Z",45.30314,5.906867,0,0,1,90,989.7],
    ["2015-05-31T23:45:03.000Z",45.30314,5.906867,0,1,2,90,989.9],
    ["2015-05-31T23:49:03.000Z",45.30314,5.906867,0,0,1,90,989.9],
    ["2015-05-31T23:53:03.000Z",45.30314,5.906867,0,0,0,90,989.9],
    ["2015-05-31T23:57:03.000Z",45.30314,5.906867,0,0,0,0,989.8]
  ]
}
```
#### Last hour, JSON

```bash
$ curl "http://api.pioupiou.fr/v1/archive/110?start=last-hour&stop=now"
```
```json
{
  "doc": "http://developers.pioupiou.fr/api/archive/",
  "license": "http://developers.pioupiou.fr/data-licensing",
  "attribution": "(c) contributors of the Pioupiou wind network <http://pioupiou.fr>",
  "legend": ["time","latitude","longitude","wind_speed_min","wind_speed_avg","wind_speed_max","wind_heading","pressure"],
  "units": ["utc","degrees","degrees","km/h","km/h","km/h","degrees","hPa"],
  "data": [
    ["2015-08-18T12:48:23.000Z",51.368464,3.458852,1,10,17.5,247.5,1020.3],
    ["2015-08-18T12:52:27.000Z",51.368464,3.458852,1,10.5,21,247.5,1020.5],
    ["2015-08-18T12:56:27.000Z",51.368464,3.458852,7,15,26,247.5,1020.5],
    ["2015-08-18T13:00:27.000Z",51.368464,3.458852,9.75,18.5,27,247.5,1020.5],
    ["2015-08-18T13:04:33.000Z",51.368464,3.458852,8,17.5,27,247.5,1020.6],
    ["2015-08-18T13:08:33.000Z",51.368464,3.458852,8.25,14,21,247.5,1020.6],
    ["2015-08-18T13:12:33.000Z",51.368464,3.458852,7.25,14,23,247.5,1020.6],
    ["2015-08-18T13:16:35.000Z",51.368464,3.458852,7.25,15.5,22.5,270,1020.8],
    ["2015-08-18T13:20:35.000Z",51.368464,3.458852,8.25,17,24.5,247.5,1020.8],
    ["2015-08-18T13:24:35.000Z",51.368464,3.458852,8,17,24.5,270,1020.8],
    ["2015-08-18T13:28:39.000Z",51.368464,3.458852,9.75,17,24,247.5,1020.9],
    ["2015-08-18T13:32:39.000Z",51.368464,3.458852,4.75,14.5,28,247.5,1020.9],
    ["2015-08-18T13:36:39.000Z",51.368464,3.458852,6.25,15.5,27.5,247.5,1020.9]
  ]
}
```
#### Last hour, csv

```bash
$ curl "http://api.pioupiou.fr/v1/archive/110?start=last-hour&stop=now&format=csv"
```
```no-highlight
"License","http://developers.pioupiou.fr/data-licensing"
"Attribution","(c) contributors of the Pioupiou wind network <http://pioupiou.fr>"
"time","latitude","longitude","wind_speed_min","wind_speed_avg","wind_speed_max","wind_heading","pressure"
"utc","degrees","degrees","km/h","km/h","km/h","degrees","hPa"
"2015-08-18T12:48:23.000Z",51.368464,3.458852,1,10,17.5,247.5,1020.3
"2015-08-18T12:52:27.000Z",51.368464,3.458852,1,10.5,21,247.5,1020.5
"2015-08-18T12:56:27.000Z",51.368464,3.458852,7,15,26,247.5,1020.5
"2015-08-18T13:00:27.000Z",51.368464,3.458852,9.75,18.5,27,247.5,1020.5
"2015-08-18T13:04:33.000Z",51.368464,3.458852,8,17.5,27,247.5,1020.6
"2015-08-18T13:08:33.000Z",51.368464,3.458852,8.25,14,21,247.5,1020.6
"2015-08-18T13:12:33.000Z",51.368464,3.458852,7.25,14,23,247.5,1020.6
"2015-08-18T13:16:35.000Z",51.368464,3.458852,7.25,15.5,22.5,270,1020.8
"2015-08-18T13:20:35.000Z",51.368464,3.458852,8.25,17,24.5,247.5,1020.8
"2015-08-18T13:24:35.000Z",51.368464,3.458852,8,17,24.5,270,1020.8
"2015-08-18T13:28:39.000Z",51.368464,3.458852,9.75,17,24,247.5,1020.9
"2015-08-18T13:32:39.000Z",51.368464,3.458852,4.75,14.5,28,247.5,1020.9
"2015-08-18T13:36:39.000Z",51.368464,3.458852,6.25,15.5,27.5,247.5,1020.9
```

#### Last hour, tabulation-separated text

```bash
$ curl "http://api.pioupiou.fr/v1/archive/110?start=last-hour&stop=now&format=txt"
```
```no-highlight
License:        http://developers.pioupiou.fr/data-licensing
Attribution:    (c) contributors of the Pioupiou wind network <http://pioupiou.fr>
time    latitude        longitude       wind_speed_min  wind_speed_avg  wind_speed_max  wind_heading    pressure
utc     degrees degrees km/h    km/h    km/h    degrees hPa
2015-08-18T12:48:23.000Z        51.368464       3.458852        1       10      17.5    247.5   1020.3
2015-08-18T12:52:27.000Z        51.368464       3.458852        1       10.5    21      247.5   1020.5
2015-08-18T12:56:27.000Z        51.368464       3.458852        7       15      26      247.5   1020.5
2015-08-18T13:00:27.000Z        51.368464       3.458852        9.75    18.5    27      247.5   1020.5
2015-08-18T13:04:33.000Z        51.368464       3.458852        8       17.5    27      247.5   1020.6
2015-08-18T13:08:33.000Z        51.368464       3.458852        8.25    14      21      247.5   1020.6
2015-08-18T13:12:33.000Z        51.368464       3.458852        7.25    14      23      247.5   1020.6
2015-08-18T13:16:35.000Z        51.368464       3.458852        7.25    15.5    22.5    270     1020.8
2015-08-18T13:20:35.000Z        51.368464       3.458852        8.25    17      24.5    247.5   1020.8
2015-08-18T13:24:35.000Z        51.368464       3.458852        8       17      24.5    270     1020.8
2015-08-18T13:28:39.000Z        51.368464       3.458852        9.75    17      24      247.5   1020.9
2015-08-18T13:32:39.000Z        51.368464       3.458852        4.75    14.5    28      247.5   1020.9
2015-08-18T13:36:39.000Z        51.368464       3.458852        6.25    15.5    27.5    247.5   1020.9
```

## Error codes

An ```HTTP/1.1 200 OK``` header is sent when the request is successful.
HTTP status code other than ```200``` means that an error has occured.

In most case, the application will return a JSON object, containing details about the error.

```bash
$ curl -i "http://api.pioupiou.fr/v1/archive/999999?start=last-hour&stop=now"
```
```json
HTTP/1.1 404 Not Found

{
  "error_code": "station_not_found",
  "error_message": "unable to find station with this {station_id}"
}
```

error_code | HTTP code | description
---------- | --------- | -----------
station_not_found | 404 | The requested station is not in the database
missing_argument | 400 | A query argument is missing
invalid_argument | 400 | A query argument is invalid
request_too_large | 413 | You asked for more than 31 days

!!! note "Error detection:"
    For reliable error detection, your application must monitor the HTTP code instead of the JSON response.

## JSONP and CORS

The API supports cross-origin requests.

### Cross-Origin Resource Sharing
An ```Access-Control-Allow-Origin: *``` header is sent with all responses. It means that you can call the API directly from your javascript page.

### JSONP
When output format is JSON, JSONP is also supported, even if it's use is no longer encouraged.

The name of the callback function must be placed in query string ```callback``` argument :

```bash
curl -i "http://api.pioupiou.fr/v1/archive/110?start=last-hour&stop=now&callback=myCallBackFunction"
```
```json
HTTP/1.1 200 OK
Content-Type: text/javascript; charset=utf-8

/**/ typeof myCallBackFunction === 'function' && myCallBackFunction({
  "doc": "http://developers.pioupiou.fr/api/archive/",
  "license": "http://developers.pioupiou.fr/data-licensing",
  "attribution": "(c) contributors of the Pioupiou wind network <http://pioupiou.fr>",
  "legend": ["time","latitude","longitude","wind_speed_min","wind_speed_avg","wind_speed_max","wind_heading","pressure"],
  "units": ["utc","degrees","degrees","km/h","km/h","km/h","degrees","hPa"],
  "data": [
    ["2015-08-18T13:36:39.000Z",51.368464,3.458852,6.25,15.5,27.5,247.5,1020.9],
    ["2015-08-18T13:40:48.000Z",51.368464,3.458852,9,15.5,22.5,247.5,1020.9],
    ["2015-08-18T13:44:48.000Z",51.368464,3.458852,7.75,15.5,27,247.5,1020.9],
    ["2015-08-18T13:48:48.000Z",51.368464,3.458852,6.5,14,21.5,247.5,1020.9],
    ["2015-08-18T13:52:47.000Z",51.368464,3.458852,10,17.5,27.5,247.5,1021],
    ["2015-08-18T13:56:47.000Z",51.368464,3.458852,6.25,17,25.5,247.5,1021],
    ["2015-08-18T14:00:47.000Z",51.368464,3.458852,12,18,28,247.5,1021],
    ["2015-08-18T14:04:51.000Z",51.368464,3.458852,9.75,18.5,26.5,247.5,1021.2],
    ["2015-08-18T14:08:51.000Z",51.368464,3.458852,10.5,19.5,30,225,1021.2],
    ["2015-08-18T14:12:51.000Z",51.368464,3.458852,8.75,18.5,30.5,247.5,1021.2],
    ["2015-08-18T14:16:55.000Z",51.368464,3.458852,7.25,16.5,24.5,247.5,1021.3],
    ["2015-08-18T14:20:55.000Z",51.368464,3.458852,12,20,27.5,247.5,1021.3],
    ["2015-08-18T14:24:55.000Z",51.368464,3.458852,7.25,16.5,24.5,247.5,1021.3]
  ]
});
```

## Limitations

Maximum request size is 31 days.
You can only request one station at a time.

The Archive API might be slower than the other APIs.