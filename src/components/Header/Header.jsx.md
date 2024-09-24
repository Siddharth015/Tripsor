## Header Component Documentation 

### Table of Contents 
* [Overview](#overview) 
* [Component Props](#component-props) 
* [Component Structure](#component-structure)
* [Usage Example](#usage-example)

### Overview 

The `Header` component renders the application's header, which includes the application title, a search bar, and a "Explore new places" prompt. 

### Component Props

| Prop | Type | Description | 
|---|---|---|
| `onPlaceChanged` | Function | A callback function triggered when a place is selected in the search bar. |
| `onLoad` | Function | A callback function triggered when the autocomplete service is loaded. |

### Component Structure 

The `Header` component uses Material UI components for the header bar and search bar:

* `AppBar`: The container for the header.
* `Toolbar`: The container for the header's content.
* `Typography`:  Displays the header title and search prompt.
* `InputBase`:  The text field for the search bar.
* `SearchIcon`:  The search icon.
* `Autocomplete`:  The autocomplete search bar powered by the Google Maps API.

The component also uses a custom `styles.js` file for styling.

```javascript
import React from 'react';
import { Autocomplete } from '@react-google-maps/api';
import { AppBar, Toolbar, Typography, InputBase, Box } from '@material-ui/core';
import SearchIcon from '@material-ui/icons/Search';

import useStyles from './styles.js';

const Header = ({ onPlaceChanged, onLoad }) => {
  const classes = useStyles();

  return (
    <AppBar position="static">
      <Toolbar className={classes.toolbar}>
        <Typography variant="h5" className={classes.title}>
          Travel Consultant
        </Typography>
        <Box display="flex">
          <Typography variant="h6" className={classes.title}>
            Explore new places
          </Typography>
          <Autocomplete onLoad={onLoad} onPlaceChanged={onPlaceChanged}>
            <div className={classes.search}>
              <div className={classes.searchIcon}>
                <SearchIcon />
              </div>
              <InputBase placeholder="Search…" classes={{ root: classes.inputRoot, input: classes.inputInput }} />
            </div>
          </Autocomplete>
        </Box>
      </Toolbar>
    </AppBar>
  );
};

export default Header;
```

### Usage Example 

The `Header` component can be used in the application's main layout:

```javascript
import Header from './Header';

function App() {
  // Handle place selection 
  const handlePlaceChanged = (place) => {
    console.log(place);
    // ... handle place selection logic 
  };

  // Handle autocomplete service loading
  const handleLoad = () => {
    console.log('Autocomplete service loaded.');
  };

  return (
    <div>
      <Header onPlaceChanged={handlePlaceChanged} onLoad={handleLoad} />
      {/* ... rest of the application content ... */}
    </div>
  );
}
```