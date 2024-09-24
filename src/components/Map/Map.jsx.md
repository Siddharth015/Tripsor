## 🗺️  Map Component Documentation

**Table of Contents**

* [1. Overview](#1-overview)
* [2. Usage](#2-usage)
* [3. Props](#3-props)
* [4. Example Usage](#4-example-usage)
* [5. Implementation Details](#5-implementation-details)
    * [5.1. Google Maps API Integration](#51-google-maps-api-integration)
    * [5.2. Marker Rendering](#52-marker-rendering)
    * [5.3. Weather Data Display](#53-weather-data-display)
* [6. Styling](#6-styling)

### 1. Overview

The `Map` component is responsible for displaying a Google Map with markers representing places and weather data. It utilizes the `google-map-react` library for seamless map integration and rendering. The component dynamically adapts its marker display based on the screen size, switching between simple icons and detailed information panels.

### 2. Usage

The `Map` component is designed to be used within a React application. It requires several props to function correctly, including:

* `coords`: An object containing the latitude and longitude of the map's center point.
* `places`: An array of place objects containing information like name, latitude, longitude, and photo URL.
* `setCoords`: A function to update the map's center coordinates.
* `setBounds`: A function to update the map's bounding box.
* `setChildClicked`: A function to handle marker click events.
* `weatherData`: An object containing weather data for the specified region.

### 3. Props

| Prop Name | Type | Description |
|---|---|---|
| `coords` | Object | Latitude and longitude of the map center. |
| `places` | Array | Array of place objects containing information like name, latitude, longitude, and photo URL. |
| `setCoords` | Function | Function to update the map's center coordinates. |
| `setBounds` | Function | Function to update the map's bounding box. |
| `setChildClicked` | Function | Function to handle marker click events. |
| `weatherData` | Object | Object containing weather data for the specified region. |

### 4. Example Usage

```javascript
import Map from './Map';

const App = () => {
  const [coords, setCoords] = useState({ lat: 40.7128, lng: -74.0060 });
  const [places, setPlaces] = useState([]);
  const [bounds, setBounds] = useState({});
  const [childClicked, setChildClicked] = useState(null);
  const [weatherData, setWeatherData] = useState(null);

  return (
    <div>
      <Map
        coords={coords}
        places={places}
        setCoords={setCoords}
        setBounds={setBounds}
        setChildClicked={setChildClicked}
        weatherData={weatherData}
      />
    </div>
  );
};
```

### 5. Implementation Details

#### 5.1. Google Maps API Integration

The component leverages the `GoogleMapReact` library to integrate with Google Maps. The API key is obtained from the environment variable `REACT_APP_GOOGLE_MAPS_API_KEY`. The map is configured with default options, such as disabling the default UI elements and enabling zoom control.

#### 5.2. Marker Rendering

The component dynamically renders markers based on the provided `places` array. The `onChange` event handler updates the map's center and bounds when the user interacts with the map. The `onChildClick` handler triggers the `setChildClicked` function, providing information about the clicked marker.

The marker display varies based on screen size. On smaller screens, a simple `LocationOnOutlinedIcon` is used. On larger screens, a detailed information panel is rendered within a `Paper` component, including the place name, photo, and rating.

#### 5.3. Weather Data Display

If `weatherData` is provided, the component displays weather icons for each weather data point. The icons are fetched from OpenWeatherMap.org using the provided weather data.

### 6. Styling

The `Map` component uses Material-UI's `useStyles` hook to apply custom styles. The styles are defined in the `styles.js` file, providing a visually appealing map interface. 
