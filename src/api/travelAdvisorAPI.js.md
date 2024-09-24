##  API Service Documentation

This document provides a detailed overview of the API service functions implemented in this code.

### Table of Contents

| Section | Description | 
|---|---|
| [**getPlacesData**](#getplacesdata) | Retrieves data for places within a specified boundary. |
| [**getWeatherData**](#getweatherdata) | Retrieves weather data for a given latitude and longitude. |

### <a name="getplacesData"></a> **getPlacesData**

This function fetches data for places within a specified boundary using the Travel Advisor API. 

**Input Parameters:**

| Parameter | Data Type | Description |
|---|---|---|
| `type` | String | The type of places to retrieve (e.g., `hotels`, `restaurants`). |
| `sw` | Object | An object representing the southwest corner of the boundary.  The object should have `lat` and `lng` properties representing latitude and longitude, respectively. |
| `ne` | Object | An object representing the northeast corner of the boundary.  The object should have `lat` and `lng` properties representing latitude and longitude, respectively. |

**Returns:**

*  An array of place data if the request is successful.
*  `undefined` if the request fails.

**Example Usage:**

```javascript
import { getPlacesData } from './api';

const southwest = { lat: 40.7128, lng: -74.0060 };
const northeast = { lat: 40.7739, lng: -73.9680 };

getPlacesData('hotels', southwest, northeast)
  .then(placesData => {
    // Process the places data 
    console.log(placesData);
  })
  .catch(error => {
    console.error('Error fetching places data:', error);
  });
```

**Implementation Details:**

* The function uses the `axios` library to make a GET request to the Travel Advisor API. 
* The request includes the following parameters:
    * `bl_latitude`: Latitude of the southwest corner.
    * `bl_longitude`: Longitude of the southwest corner.
    * `tr_longitude`: Longitude of the northeast corner.
    * `tr_latitude`: Latitude of the northeast corner.
* The function also sets the necessary headers, including the RapidAPI key and host. 
* The `data` property of the API response is returned as the result.
* If the request fails, the function logs the error to the console.

### <a name="getWeatherData"></a> **getWeatherData**

This function retrieves weather data for a specific location using the OpenWeatherMap API. 

**Input Parameters:**

| Parameter | Data Type | Description |
|---|---|---|
| `lat` | Number | Latitude of the location. |
| `lng` | Number | Longitude of the location. |

**Returns:**

* An object containing weather data if the request is successful.
* `undefined` if the request fails or if latitude and longitude are not provided.

**Example Usage:**

```javascript
import { getWeatherData } from './api';

const latitude = 34.0522;
const longitude = -118.2437;

getWeatherData(latitude, longitude)
  .then(weatherData => {
    // Process the weather data
    console.log(weatherData);
  })
  .catch(error => {
    console.error('Error fetching weather data:', error);
  });
```

**Implementation Details:**

* The function uses the `axios` library to make a GET request to the OpenWeatherMap API.
* The request includes the following parameters:
    * `lat`: Latitude of the location.
    * `lon`: Longitude of the location.
* The function also sets the necessary headers, including the RapidAPI key and host.
* If the request is successful, the `data` property of the API response is returned.
* If the request fails or if latitude and longitude are not provided, the function logs the error to the console and returns `undefined`.
