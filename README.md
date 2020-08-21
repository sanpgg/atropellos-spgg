# Atropellos en San Pedro Garza García
## Descripción
Listado de hechos viales catalogados como atropellos a peatones con al menos un lesionado o fallecido en el municipio de San Pedro Garza García. Datos del 2015 al 2019.
## Leaflet Maps with Open Data API {- #leaflet-maps-with-api}
TODO:

- Note this new title and URL, which is more general than the older title and "leaflet-maps-with-socrata" URL
- Blend in other section below this one
- Update the example to pull map data from a continuously updated map, since the current example has not been updated since 2018
- Decide if there's anything useful to borrow from the other example repo, such as a non-Socrata endpoint?: https://github.com/HandsOnDataViz/leaflet-data-apis
- write intro to connect more directly to the [Open Data section](opendata.html) in ch 3, and describe open data APIs in general, with Socrata API serving as a convenient example.

<iframe src="https://handsondataviz.github.io/leaflet-socrata/index.html" style="width: 100%; height: 450px; border: 0 none;"></iframe>
Source: [Current Class 1 - Class 4 Food Establishments](https://data.hartford.gov/Public-Health/Current-Class-1-Class-4-Food-Establishments/xkvv-76v8), City of Hartford

#### Why pair Leaflet maps with Socrata data? {-}
Leaflet, a friendly and flexible open-source code library for creating interactive web maps, plays nicely with Socrata, an open data platform used by several government agencies and organizations. Benefits of pairing Leaflet and Socrata:

- Although the Socrata data platform includes built-in visualization tools for anyone to create charts and maps, Leaflet gives you more control over your map design. Furthermore, Leaflet allows you to create maps that bring together data from both Socrata and non-Socrata sources.
- Socrata datasets include an API (application program interface) endpoint, in the form of a web address. This endpoint enables other computers to easily access the most recent data online, instead of a static version that was manually downloaded.
- Newer Socrata datasets that include locations (such as latitude and longitude coordinates) also provide endpoints in GeoJSON format. Since Leaflet maps easily process GeoJSON data, only a few lines of code are required.

- However, Socrata GeoJSON endpoints do not currently support "real-time" data, such as up-to-the-minute locations of public transportation, etc. In these cases, you may need to access data through a provider other than Socrata, most likely in a different format, which may require more coding skills.

#### About Socrata API endpoints {-}

Go to any Socrata open data platform, find a dataset, and click the API tab. As an example, you can use City of Hartford's [Police Incidents dataset](https://data.hartford.gov/Public-Safety/Police-Incidents-01012005-to-Current/889t-nwfu).

![Police Incidents dataset on Hartford Open Data portal](images/11-leaflet/data-hartford-api.png)

Copy the API endpoint. The default version is JSON.

If you're new to APIs, test the endpoint by pasting it into your browser address line. Ideally you would see a formatted JSON view (use Chrome or Firefox for better results).

![Formatted JSON example in Firefox](images/11-leaflet/data-hartford-api-json.png)

If your browser does not support JSON view, you will see the raw JSON stream only, like the one shown below.

![Unformatted JSON example in Firefox](images/11-leaflet/data-hartford-api-json-not-formatted.png)

Test if this Socrata endpoint supports GeoJSON format by changing the extention in the API dropdown menu from `JSON` to `GeoJSON`. GeoJSON format works best with Leaflet because the coding is simpler.

If your endpoint supports GeoJSON format, your browser will display a data stream similar to the one below.

![Formatted GeoJSON example in Firefox](images/11-leaflet/data-hartford-api-geojson.png)

If your Socrata endpoint only supports JSON format, but includes data columns with latitude and longitude, see other Leaflet examples further below.

#### Register for Socrata App Token {-}
- Socrata requires developers to register for a free app token at https://opendata.socrata.com/signup

#### Demonstration Maps {-}

#### GeoJSON endpoint with circle markers and tooltips {-}
- map https://handsondataviz.github.io/leaflet-socrata/index.html
- code https://github.com/handsondataviz/leaflet-socrata/index.html
- data https://data.hartford.gov/Public-Health/Current-Class-1-Class-4-Food-Establishments/xkvv-76v8
- note: location data appears as latitude and longitude coordinates in the `geom` column

- steps to create your own   (MORE TODO HERE)

  - select API button, copy endpoint, and change suffix from .json to .geojson

  - copy this Leaflet map template, which includes this key section of code:

  - paste and explain the code

#### GeoJSON endpoint with simple data filter, default marker styling and pop-up info {-}
- map https://handsondataviz.github.io/leaflet-socrata/index-geojson-filter
- code https://github.com/handsondataviz/leaflet-socrata/
- data https://data.ct.gov/Environment-and-Natural-Resources/Agricultural-Commoditites-Grown-By-Farmer/y6p2-px98

#### Multiple Socrata datasets with Leaflet control layers legend {-}
- map https://handsondataviz.github.io/leaflet-socrata/index-control-layers.html
- code https://github.com/handsondataviz/leaflet-socrata/index-control-layers.html

#### Older JSON-only endpoint, with separate columns for latitude, longitude {-}
- map https://handsondataviz.github.io/leaflet-socrata/index-json.html
- code https://github.com/handsondataviz/leaflet-socrata/index-json.html
- data https://opendata.demo.socrata.com/Government/Kentucky-Farmers-Market-Map/3bfj-rqn7

Learn more:
- https://dev.socrata.com/
- https://github.com/chriswhong/simpleSodaLeaflet

#### Thanks to {-}
- Chris Metcalf https://github.com/chrismetcalf
- Tyler Klyeklamp https://data.ct.gov/


**TODO: blend this section into the one above**

Pull Open Data into Leaflet Map with APIs {- #leaflet-maps-open-apis}
TODO: Decide whether to keep or not. Up to this point in the book, we’ve built charts and maps using static data that you have downloaded from other sites. But some open data repositories have APIs, or application program interfaces, which means the software that allows computers to communicate with one another. Below is a Leaflet Map template that uses APIs to pull in the most current data from three different open repository platforms: Socrata, Esri ArcGIS Online, and USGS.

Try it:
Explore the map below or [view full-screen version in a new tab](https://handsondataviz.github.io/leaflet-data-apis)

<iframe src="https://handsondataviz.github.io/leaflet-data-apis/" width="90%" height=550></iframe>

#### How it works {-}

1) Go to the GitHub repo for the map above: https://github.com/handsondataviz/leaflet-data-apis

2) Explore the code to see how different APIs work. For example, see the first map overlay, which pulls Connecticut School Directory data from the CT Open Data repository on a Socrata open data platform: https://data.ct.gov/resource/v4tt-nt9n

3) Inside the open data repo, look for an API button and copy the endpoint.

![Screenshot: Sample API endpoint in Socrata open data repo](images/11-leaflet/ct-open-data-api-endpoint.png)

4) Paste the endpoint link into your browser, change the suffix from `.json` to `.geojson` and press return. In order to show the endpoint data as points on a map in this simple Leaflet template, the points must already be geocoded inside the open data repo, and the platform must support a GeoJSON endpoint. In your browser, one sign of success is a long stream of GeoJSON data like this:

![Screenshot: API endpoint with .geojson suffix in Chrome browser](images/11-leaflet/ct-open-data-geojson.png)

5) In this section of the Leaflet map template, the code includes a jQuery function `$.getJSON` to call the open data endpoint in GeoJSON format: `https://data.ct.gov/resource/v4tt-nt9n.geojson`. It also requires a Socrata app token, and you can get your own token for free at: https://dev.socrata.com/register. Each geocoded school in the Socrata data repository is displayed as a blue circle, with data properties (such as: name) in a clickable pop-up.

```javascript
// load open data from Socrata endpoint in GeoJSON format
// with simple marker styling: blue circles
// register your own Socrata app token at https://dev.socrata.com/register
// Connecticut School Directory, CT Open Data, https://data.ct.gov/resource/v4tt-nt9n
$.getJSON("https://data.ct.gov/resource/v4tt-nt9n.geojson?&$$app_token=QVVY3I72SVPbxBYlTM8fA7eet", function (data){
  var geoJsonLayer = L.geoJson(data, {
    pointToLayer: function( feature, latlng) {
      var circle = L.circleMarker(latlng, {
        radius: 6,
        fillColor: "blue",
        color: "blue",
        weight: 2,
        opacity: 1,
        fillOpacity: 0.7
      });
      circle.bindPopup(feature.properties.name + '<br>' + feature.properties.district_name); // replace last term with property data labels to display from GeoJSON file
      return circle;
    }
  }).addTo(map); // display by default
  controlLayers.addOverlay(geoJsonLayer, 'Public Schools (CT Open Data-Socrata)');
});
```

5) Fork a copy of this repo, play with the code, and try to insert GeoJSON endpoints from other open data repositories.
