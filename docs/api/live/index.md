# Live API

The Live API provides access to the latest measurements from **one station** or **all stations**.

## License
To use data from Pioupiou stations, you must comply with the license available on the [Data Licensing](../../data-licensing.md) page.

## Endpoints
```bash
# latest measurements only
GET http://api.pioupiou.fr/v1/live/{station_id}
```
```bash
# latest measurements with complete metadata
GET http://api.pioupiou.fr/v1/live-with-meta/{station_id}
```
## Arguments
```bash
# for a single station
{station_id} : Numeric ID of the station
```

```bash
# for all stations
{station_id} : "all"
```

## Responses

The **Live** API provides JSON responses.

### Response examples
#### Single station, latest measurements only

```bash
$ curl "http://api.pioupiou.fr/v1/live/110"
```
```json
{
  "doc": "http://developers.pioupiou.fr/api/live/",
  "license": "http://developers.pioupiou.fr/data-licensing",
  "attribution": "(c) contributors of the Pioupiou wind network <http://pioupiou.fr>",
  "data": {
    "id": 110,
    "meta": {
      "name": "Pioupiou 110"
    },
    "location": {
      "latitude": 51.368464,
      "longitude": 3.458852,
      "date": "2015-08-16T14:26:01.000Z",
      "success": true
    },
    "measurements": {
      "date": "2015-08-17T22:07:27.000Z",
      "pressure": null,
      "wind_heading": 292.5,
      "wind_speed_avg": 14,
      "wind_speed_max": 22.5,
      "wind_speed_min": 7
    },
    "status": {
      "date": "2015-08-17T22:07:27.000Z",
      "snr": 23.03,
      "state": "on"
    }
  }
}
```


#### Single station, latest measurements with complete metadata

```bash
$ curl "http://api.pioupiou.fr/v1/live-with-meta/110"
```
```json
{
  "doc": "http://developers.pioupiou.fr/api/live/",
  "license": "http://developers.pioupiou.fr/data-licensing",
  "attribution": "(c) contributors of the Pioupiou wind network <http://pioupiou.fr>",
  "data": {
    "id": 110,
    "meta": {
      "name": "Pioupiou 110",
      "description": null,
      "picture": null,
      "date": null,
      "rating": {
        "upvotes": 0,
        "downvotes": 0
      }
    },
    "location": {
      "latitude": 51.368464,
      "longitude": 3.458852,
      "date": "2015-08-16T14:26:01.000Z",
      "success": true
    },
    "measurements": {
      "date": "2015-08-17T22:19:31.000Z",
      "pressure": null,
      "wind_heading": 292.5,
      "wind_speed_avg": 12,
      "wind_speed_max": 21,
      "wind_speed_min": 6.5
    },
    "status": {
      "date": "2015-08-17T22:19:31.000Z",
      "snr": 23.01,
      "state": "on"
    }
  }
}
```
#### All stations, latest measurements only

```bash
$ curl "http://api.pioupiou.fr/v1/live/all"
```
```json
{
  "doc": "http://developers.pioupiou.fr/api/live/",
  "license": "http://developers.pioupiou.fr/data-licensing",
  "attribution": "(c) contributors of the Pioupiou wind network <http://pioupiou.fr>",
  "data": [
    {
      "id": 1,
      "meta": {
        "name": "Pioupiou 1",
      },
      "location": {
        "latitude": 0,
        "longitude": 0,
        "date": null,
        "success": false
      },
      "measurements": {
        "date": "2015-08-18T08:19:46.000Z",
        "pressure": null,
        "wind_heading": 157.5,
        "wind_speed_avg": 2,
        "wind_speed_max": 4,
        "wind_speed_min": 0
      },
      "status": {
        "date": "2015-08-18T08:19:46.000Z",
        "snr": 23.24,
        "state": "on"
      }
    },
    {
      "id": 27,
      "meta": {
        "name": "Pioupiou 27",
      },
      "location": {
        "latitude": 44.907284,
        "longitude": 5.677965,
        "date": "2015-08-15T13:48:38.000Z",
        "success": true
      },
      "measurements": {
        "date": "2015-08-18T08:18:26.000Z",
        "pressure": null,
        "wind_heading": 45,
        "wind_speed_avg": 15,
        "wind_speed_max": 17.5,
        "wind_speed_min": 10.5
      },
      "status": {
        "date": "2015-08-18T08:18:26.000Z",
        "snr": 12.01,
        "state": "on"
      }
    },
    {...more stations...},
    {...more stations...}
  ]
}
```


#### All stations, latest measurements with complete metadata

```bash
$ curl "http://api.pioupiou.fr/v1/live-with-meta/all"
```
```json
{
  "doc": "http://developers.pioupiou.fr/api/live/",
  "license": "http://developers.pioupiou.fr/data-licensing",
  "attribution": "(c) contributors of the Pioupiou wind network <http://pioupiou.fr>",
  "data": [
    {
      "id": 1,
      "meta": {
        "name": "Pioupiou 1",
        "description": null,
        "picture": null,
        "date": null,
        "rating": {
          "upvotes": 0,
          "downvotes": 0
        }
      },
      "location": {
        "latitude": 0,
        "longitude": 0,
        "date": null,
        "success": false
      },
      "measurements": {
        "date": "2015-08-18T08:19:46.000Z",
        "pressure": null,
        "wind_heading": 157.5,
        "wind_speed_avg": 2,
        "wind_speed_max": 4,
        "wind_speed_min": 0
      },
      "status": {
        "date": "2015-08-18T08:19:46.000Z",
        "snr": 23.24,
        "state": "on"
      }
    },
    {
      "id": 27,
      "meta": {
        "name": "Pioupiou 27",
        "description": null,
        "picture": null,
        "date": null,
        "rating": {
          "upvotes": 0,
          "downvotes": 0
        }
      },
      "location": {
        "latitude": 44.907284,
        "longitude": 5.677965,
        "date": "2015-08-15T13:48:38.000Z",
        "success": true
      },
      "measurements": {
        "date": "2015-08-18T08:18:26.000Z",
        "pressure": null,
        "wind_heading": 45,
        "wind_speed_avg": 15,
        "wind_speed_max": 17.5,
        "wind_speed_min": 10.5
      },
      "status": {
        "date": "2015-08-18T08:18:26.000Z",
        "snr": 12.01,
        "state": "on"
      }
    },
    {...more stations...},
    {...more stations...}
  ]
}
```

### Responses parameters details

A ```data``` object is returned. It contains a single station ```{}``` or an array of all stations```[{},{}..{},{}]```.

Every station contains the following parameters :

Name | live | live-with-meta | Description | Unit
---- | ---- | -------------- | ----------- | ----
id | x | x | Numeric ID of the station
meta.name | x | x | Name of the station
meta.description | | x | Description of the station, or **null**
meta.picture | | x | URL of station's picture, or **null**
meta.date | | x | Date of last metadata update, or **null** | ISO 8601, UTC
meta.rating.upvotes | | x | Station rating : Positive votes count
meta.rating.downvotes | | x | Station rating : Negative votes count
location.latitude | x | x | Last known Latitude of the station, or **null** | WGS84
location.longitude | x | x | Last known Longitude of the station, or **null** | WGS84
location.date | x | x | Date of last location update (succeed or failed), or **null** | ISO 8601, UTC
location.success | x | x | Is the last known position still valid ? **true** or **false**
measurements.date | x | x | Date of last measurements, or **null** | ISO 8601, UTC
measurements.pressure | x | x | **null** (deprecated)
measurements.wind_heading | x | x | Wind heading, or **null** (0° means the wind is blowing from North to Sud) | degrees
measurements.wind_speed_avg | x | x | Wind speed average, or **null** (over the last 4 minutes before measurements.date, divide by 1.852 for converting to knots) | km/h
measurements.wind_speed_min | x | x | Minimum wind speed, or **null** (over the last 4 minutes before measurements.date, divide by 1.852 for converting to knots) | km/h
measurements.wind_speed_max | x | x | Maximum wind speed, or **null** (over the last 4 minutes before measurements.date, divide by 1.852 for converting to knots) | km/h
status.date | x | x | Date of the last contact with the station, or **null**  | ISO 8601, UTC
status.snr | x | x | Signal-to-Noise ratio = radio link quality, or **null** (<10 : bad, >20: very good) | dB
status.state | x | x | Station power state, **"on"**, **"off"** or **null**. "off" means that the station have been shutdown by pressing it's power switch.

## Error codes

An ```HTTP/1.1 200 OK``` header is sent on successful request.
HTTP status code other than ```200``` means that an error has occured.

In most cases the application will return a JSON object, including details about the error.

```bash
$ curl -i "http://api.pioupiou.fr/v1/live/999999"
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
missing_argument | 400 | The station ID is missing or invalid

!!! note "Error detection:"
    For reliable error detection, your application must monitor the HTTP code instead of the JSON response.

## JSONP and CORS

The API supports cross-origin requests.

### Cross-Origin Resource Sharing
An ```Access-Control-Allow-Origin: *``` header is sent with all responses. It means that you can call the API directly from your javascript page.

### JSONP
JSONP is also supported, even if its use is no longer encouraged.

The name of the callback function must be placed in query string ```callback``` argument:

```bash
$ curl -i "http://api.pioupiou.fr/v1/live/1?callback=myCallBackFunction"
```
```json
HTTP/1.1 200 OK
Content-Type: text/javascript; charset=utf-8

/**/ typeof myCallBackFunction === 'function' && myCallBackFunction({
  "doc": "http://developers.pioupiou.fr/api/live/",
  "license": "http://pioupiou.fr/license/data",
  "attribution": "(c) contributors of the Pioupiou wind network <http://pioupiou.fr>",
  "data": {
    "id": 1,
    "meta": {
      "name": "Pioupiou 1"
    },
    "location": {
      "latitude": 0,
      "longitude": 0,
      "date": null,
      "success": false
    },
    "measurements": {
      "date": "2015-08-18T08:55:46.000Z",
      "pressure": null,
      "wind_heading": 157.5,
      "wind_speed_avg": 2,
      "wind_speed_max": 3,
      "wind_speed_min": 1
    },
    "status": {
      "date": "2015-08-18T08:55:46.000Z",
      "snr": 23.31,
      "state": "on"
    }
  }
});
```

## Limitations

Updates for **all stations** or a **single station** should not be requested more often than every 60 seconds. If you need real-time information, please use the [Push API](../push/).

If you use this API for a high-traffic application, you have to set-up your own cache server.
