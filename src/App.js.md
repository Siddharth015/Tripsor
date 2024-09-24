##  App.js 🗺️🌎

### Table of Contents

| Section                  | Page |
|---------------------------|------|
| Introduction             | 1    |
| States                     | 2    |
| Effects                   | 3    |
| Functions                | 4    |
| Rendering                 | 5    |


### Introduction

This file implements the main component of the travel application, `App`. It utilizes the Material-UI library for styling and layout, and leverages custom components (`Header`, `List`, and `Map`) for specific functionality. The component fetches data from the `travelAdvisorAPI` for places and weather information, and renders them on the UI.

### States

The component uses the following state variables to manage its data and behavior:

| State Variable         | Type            | Description                                                                                                                                                                                                                                                        |
|---------------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `type`                  | `string`         | Represents the current type of places to display (e.g., "restaurants", "hotels").                                                                                                                                                                                                |
| `rating`                | `string`         | Represents the minimum rating filter applied to the displayed places.                                                                                                                                                                                                   |
| `coords`                | `object`         | Stores the current latitude and longitude coordinates.                                                                                                                                                                                                                   |
| `bounds`                 | `object`         | Represents the geographical bounds of the map, used for fetching places within a specific area.                                                                                                                                                                                  |
| `weatherData`            | `array`          | Stores the weather data for the current location.                                                                                                                                                                                                                           |
| `filteredPlaces`        | `array`          | Stores the places filtered based on the current rating.                                                                                                                                                                                                                          |
| `places`                 | `array`          | Stores all the fetched places data.                                                                                                                                                                                                                                   |
| `autocomplete`          | `object`         | Stores the reference to the Google Maps autocomplete object.                                                                                                                                                                                                                   |
| `childClicked`          | `object`         | Stores the data of the place that was clicked on the map.                                                                                                                                                                                                              |
| `isLoading`             | `boolean`        | Indicates whether data is currently being fetched.                                                                                                                                                                                                                              |

### Effects

The component uses `useEffect` hooks to handle various side effects:

* **Fetching user location:** On component mount, it fetches the user's current location using `navigator.geolocation.getCurrentPosition`.
* **Filtering places based on rating:** It updates the `filteredPlaces` state whenever the `rating` state changes, filtering the places based on the provided rating.
* **Fetching places and weather data:** When the `bounds` state changes, it fetches both places and weather data. It first uses `getWeatherData` to retrieve weather data based on the current coordinates, then uses `getPlacesData` to retrieve places data within the provided bounds.

### Functions

The component defines the following functions:

* **`onLoad`:** This function receives the Google Maps autocomplete object and updates the `autocomplete` state.
* **`onPlaceChanged`:** This function is triggered when the user selects a place from the autocomplete suggestions. It retrieves the coordinates of the selected place and updates the `coords` state.

### Rendering

The component renders the following UI elements:

* **`CssBaseline`:** Provides basic styles for the application.
* **`Header`:** Displays the header component, which includes the search bar and autocomplete functionality.
* **`Grid`:** Uses Material-UI's `Grid` component to divide the screen into two sections.
* **`List`:** Renders the list of places, displaying either the filtered places or all places based on the current state.
* **`Map`:** Renders the map component, displaying markers for the places and weather data.

The component passes relevant state variables and functions to the child components (`Header`, `List`, and `Map`) through props. This allows the child components to interact with the parent component and update the state accordingly.

### Code Example

```jsx
import React, { useState, useEffect } from 'react';
import { CssBaseline, Grid } from '@material-ui/core';

import { getPlacesData, getWeatherData } from './api/travelAdvisorAPI';
import Header from './components/Header/Header';
import List from './components/List/List';
import Map from './components/Map/Map';

const App = () => {
  const [type, setType] = useState('restaurants');
  const [rating, setRating] = useState('');

  const [coords, setCoords] = useState({});
  const [bounds, setBounds] = useState(null);

  const [weatherData, setWeatherData] = useState([]);
  const [filteredPlaces, setFilteredPlaces] = useState([]);
  const [places, setPlaces] = useState([]);

  const [autocomplete, setAutocomplete] = useState(null);
  const [childClicked, setChildClicked] = useState(null);
  const [isLoading, setIsLoading] = useState(false);

  useEffect(() => {
    navigator.geolocation.getCurrentPosition(({ coords: { latitude, longitude } }) => {
      setCoords({ lat: latitude, lng: longitude });
    });
  }, []);

  useEffect(() => {
    const filtered = places.filter((place) => Number(place.rating) > rating);

    setFilteredPlaces(filtered);
  // eslint-disable-next-line react-hooks/exhaustive-deps
  }, [rating]);

  useEffect(() => {
    if (bounds) {
      setIsLoading(true);

      getWeatherData(coords.lat, coords.lng)
        .then((data) => setWeatherData(data));

      getPlacesData(type, bounds.sw, bounds.ne)
        .then((data) => {
          setPlaces(data.filter((place) => place.name && place.num_reviews > 0));
          setFilteredPlaces([]);
          setRating('');
          setIsLoading(false);
        });
    }
  // eslint-disable-next-line react-hooks/exhaustive-deps
  }, [bounds, type]);

  const onLoad = (autoC) => setAutocomplete(autoC);

  const onPlaceChanged = () => {
    const lat = autocomplete.getPlace().geometry.location.lat();
    const lng = autocomplete.getPlace().geometry.location.lng();

    setCoords({ lat, lng });
  };

  return (
    <>
      <CssBaseline />
      <Header onPlaceChanged={onPlaceChanged} onLoad={onLoad} />
      <Grid container spacing={3} style={{ width: '100%' }}>
        <Grid item xs={12} md={4}>
          <List
            isLoading={isLoading}
            childClicked={childClicked}
            places={filteredPlaces.length ? filteredPlaces : places}
            type={type}
            setType={setType}
            rating={rating}
            setRating={setRating}
          />
        </Grid>
        <Grid item xs={12} md={8} style={{ display: 'flex', justifyContent: 'center', alignItems: 'center' }}>
          <Map
            setChildClicked={setChildClicked}
            setBounds={setBounds}
            setCoords={setCoords}
            coords={coords}
            places={filteredPlaces.length ? filteredPlaces : places}
            weatherData={weatherData}
          />
        </Grid>
      </Grid>
    </>
  );
};

export default App;

```
