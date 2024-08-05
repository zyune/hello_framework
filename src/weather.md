# Weather report

```js
const forecast = FileAttachment("./data/forecast.json").json();
```
```js
display(forecast);
```

```js
import * as L from "npm:leaflet";

// Create a div element for the map
const div = display(document.createElement("div"));
div.style = "height: 400px;";

// Initialize the map
const map = L.map(div)
  .setView([0, 0], 2);

// Add a tile layer to the map
L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
  attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>'
}).addTo(map);

// Add the GeoJSON data to the map
const geojsonLayer = L.geoJSON(forecast).addTo(map);

// Fit the map to the bounds of the GeoJSON layer
map.fitBounds(geojsonLayer.getBounds());

```

```js
// Step 1: Attach the HTML file
viewof htmlFile = FileAttachment("maine_counties_map.html").text()

// Step 2: Create an iframe to display the HTML content
htmlFileContent = (async () => {
  return await viewof htmlFile;
})()

```

html`
 <iframe src="${URL.createObjectURL(new Blob([await htmlFileContent], {type: 'text/html'}))}" width="100%" height="600px"></iframe>
`
```html
  <iframe src="${URL.createObjectURL(new Blob([await viewof htmlFile], {type: 'text/html'}))}" width="100%" height="600px"></iframe>
```