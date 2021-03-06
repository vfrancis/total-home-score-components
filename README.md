# Total Home Score Components
React and vanilla javascript components for rendering Total Home Score livability scores, powered by the [Shine API](https://developers.solarialabs.com).

Total Home Score livability scores give you insights on what you can expect from day-to-day life in a home. From neighborhood noise to how easy it is to get to amenities like grocery stores and restaurants, you’ll know how this home compares to others in the same neighborhood.

For more information about the Shine API, check out https://developers.solarialabs.com

## Shine API Account
A Shine API account and an associated `apiKey` is required to leverage these components. For more information and details on how to sign up for an account, check out https://developers.solarialabs.com/apis

Once you have created an account, you will need to generate an `apiKey` to use within these components. This can be done by creating an `App` within the Shine API developer portal, and choosing the `Total Home Score` product. The `Consumer Key` can then be leveraged as an `apiKey` for these components.

## Example of Total Home Score Component
![Total Home Score](https://user-images.githubusercontent.com/10982483/41993421-66246af6-7a19-11e8-8624-3d0c29e0d40c.png)

## Usage
This repository contains both React and vanilla javascript components, as well as a basic stylesheet.

### Library Prereqs
In order to leverage the React or vanilla javascript components, the following prereqs must be met:
* React
* Bootstrap CSS or equivalent stylesheet
* [Optional] [Popper.js](https://getbootstrap.com/docs/4.0/components/popovers/) or equivalent for tooltips
* [Optional] [Font Awesome](https://fontawesome.com/) or equivalent for tooltips

**Note:** Some of these prereqs are defined as peer dependenices, but none are defined as explicit dependencies.

### React Component
To leverage the React component, install the following package from `npm`:

```bash
npm install @shine-api/total-home-score
```

Once installed, this component can be leveraged in your app by passing in the `apiKey` from your Shine API App and the `lat` and `lon` coordinates for the desired location to display information for.

If your app needs to process the score results directly, such as hiding the component entirely if no scores are present, you can pass in a `callback` function to the component. This function will get called with the scores or an empty array if no scores were returned from the API.

```javascript
import React from 'react';

import TotalHomeScore from '@shine-api/total-home-score';
import '@shine-api/total-home-score/dist/main.css';

const apiKey = 'API_KEY_FROM_SHINE_API';
const lat = 42;
const lon = -71;

const callback = scores => {
  // Process scores directly
};

const ExampleApp = () => (
  <div>
    <TotalHomeScore apiKey={apiKey} lat={lat} lon={lon} callback={callback} />
  </div>
);
```

### Plain Javascript Component
To leverage the plain javascript component, the following two script tags to your page, and a div container for the widget to get added to:

```html
<div id="widget-container"></div>
<script lang="text/javascript">
  TotalHomeScore = {
    apiKey: 'API_KEY_FROM_SHINE_API',
    lat: 42,
    lon: -71,
    id: "widget-container"
  }
</script>
<script src="<path_to_js_file>"></script>
```

The script tags will import the javascript component and place dom elements inside of the given `widget-container` element. 
