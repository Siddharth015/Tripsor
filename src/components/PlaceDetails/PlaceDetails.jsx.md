## PlaceDetails Component Documentation

### Table of Contents

| Section | Description |
|---|---|
| [Introduction](#introduction) | Overview of the PlaceDetails component |
| [Props](#props) | List of props accepted by the component |
| [Usage](#usage) | Example code demonstrating how to use the component |
| [Code Breakdown](#code-breakdown) | Detailed explanation of the code |

### Introduction

The `PlaceDetails` component displays detailed information about a specific place, including its name, rating, reviews, price level, ranking, awards, cuisine, address, phone number, and links to its Trip Advisor and website pages. It uses Material-UI components to create a visually appealing and user-friendly display.

### Props

| Prop | Type | Description | Required | Default |
|---|---|---|---|---|
| `place` | Object | An object containing information about the place. | ✅ | N/A |
| `selected` | Boolean | Indicates whether the place is currently selected. | ✅ | N/A |
| `refProp` | Object | A reference to a DOM element. | 🚫 | N/A |

### Usage

```jsx
import PlaceDetails from './PlaceDetails';

const myPlace = {
  name: 'Acme Restaurant',
  rating: 4.5,
  num_reviews: 200,
  price_level: '$',
  ranking: 10,
  awards: [
    // ...
  ],
  cuisine: [
    // ...
  ],
  address: '123 Main Street',
  phone: '555-123-4567',
  web_url: 'https://www.tripadvisor.com/acme-restaurant',
  website: 'https://www.acme-restaurant.com',
};

const myRef = useRef(null);

<PlaceDetails place={myPlace} selected={true} refProp={myRef} />
```

### Code Breakdown

```javascript
import React from 'react';
import { Box, Typography, Button, Card, CardMedia, CardContent, CardActions, Chip } from '@material-ui/core';
import LocationOnIcon from '@material-ui/icons/LocationOn';
import PhoneIcon from '@material-ui/icons/Phone';
import Rating from '@material-ui/lab/Rating';

import useStyles from './styles.js';

const PlaceDetails = ({ place, selected, refProp }) => {
  // If the place is selected, scroll to its position smoothly
  if (selected) refProp?.current?.scrollIntoView({ behavior: 'smooth', block: 'start' });
  const classes = useStyles();

  return (
    <Card elevation={6}>
      <CardMedia
        style={{ height: 350 }}
        // Use the place's photo if available, otherwise use a placeholder image
        image={place.photo ? place.photo.images.large.url : 'https://www.foodserviceandhospitality.com/wp-content/uploads/2016/09/Restaurant-Placeholder-001.jpg'}
        title={place.name}
      />
      <CardContent>
        <Typography gutterBottom variant="h5">{place.name}</Typography>
        <Box display="flex" justifyContent="space-between" my={2}>
          <Rating name="read-only" value={Number(place.rating)} readOnly />
          <Typography component="legend">{place.num_reviews} review{place.num_reviews > 1 && 's'}</Typography>
        </Box>
        <Box display="flex" justifyContent="space-between">
          <Typography component="legend">Price</Typography>
          <Typography gutterBottom variant="subtitle1">
            {place.price_level}
          </Typography>
        </Box>
        <Box display="flex" justifyContent="space-between">
          <Typography component="legend">Ranking</Typography>
          <Typography gutterBottom variant="subtitle1">
            {place.ranking}
          </Typography>
        </Box>
        {/* Display awards if available */}
        {place?.awards?.map((award) => (
          <Box display="flex" justifyContent="space-between" my={1} alignItems="center">
            <img src={award.images.small} />
            <Typography variant="subtitle2" color="textSecondary">{award.display_name}</Typography>
          </Box>
        ))}
        {/* Display cuisine types if available */}
        {place?.cuisine?.map(({ name }) => (
          <Chip key={name} size="small" label={name} className={classes.chip} />
        ))}
        {/* Display address if available */}
        {place.address && (
          <Typography gutterBottom variant="body2" color="textSecondary" className={classes.subtitle}>
            <LocationOnIcon />{place.address}
          </Typography>
        )}
        {/* Display phone number if available */}
        {place.phone && (
          <Typography variant="body2" color="textSecondary" className={classes.spacing}>
            <PhoneIcon /> {place.phone}
          </Typography>
        )}
      </CardContent>
      <CardActions>
        {/* Button to open the place's Trip Advisor page */}
        <Button size="small" color="primary" onClick={() => window.open(place.web_url, '_blank')}>
          Trip Advisor
        </Button>
        {/* Button to open the place's website */}
        <Button size="small" color="primary" onClick={() => window.open(place.website, '_blank')}>
          Website
        </Button>
      </CardActions>
    </Card>
  );
};

export default PlaceDetails;
```

**Explanation:**

* **Import necessary components:** The code starts by importing necessary components from Material-UI and other libraries.
* **Component definition:** The `PlaceDetails` component accepts three props: `place`, `selected`, and `refProp`.
* **Scroll into view:** If the `selected` prop is `true`, the component scrolls to its position smoothly using the `refProp`.
* **Card structure:** The component uses a `Card` element to contain all the place details.
* **Image display:** The `CardMedia` element displays the place's photo if available, otherwise it uses a placeholder image.
* **Place information:** The `CardContent` element displays the place's name, rating, reviews, price level, ranking, awards, cuisine, address, and phone number.
* **Awards and cuisine display:** The component uses `map` to iterate over the awards and cuisine arrays, displaying them using `Box` and `Chip` elements respectively.
* **Address and phone number display:** The component uses conditional rendering to display the address and phone number only if they are available.
* **Actions:** The `CardActions` element contains two buttons: one to open the place's Trip Advisor page and one to open its website.
* **Styling:** The component uses the `useStyles` hook to import styles from the `styles.js` file.

This documentation provides a comprehensive overview of the `PlaceDetails` component, explaining its purpose, props, usage, and code breakdown. 
