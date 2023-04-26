# Layer Manager

This library will help you to manage the addition and removal of layers. It also provides methods to set opacity, visibility and zIndex.

We currently only supports Mapbox spec. Leaflet or Google Maps Plugin is in our minds.

## :bomb: Install

Using npm:

`npm install layer-manager`

Using yarn:

`yarn add layer-manager`


## :heavy_exclamation_mark: Requirements

`layer-manager` requires `react@16.3.2` or higher to work.

You should also install these packages versions to have everything working
- `viewport-mercator-project@6.1.1`
- `axios`


## :clipboard: Docs

### LayerManager

#### `map - (required)`

An instance of the map.

#### `plugin - (required)`

A plugin to handle all the layer functionalities depending on the map tech. Layer Manager provides you with the Mapbox one, if you want to use Leaflet, GoogleMaps or any other map tech you should provide it with the correct specification.

How could you create your own plugin? => Cooming soon

#### `providers - (optional)`
An object with the provider type as a key. Each key should be a function.

Each function will receive the following props:
- `layerModel - (object)`
  - Current layer model. It contains `source` and `render` already parsed.
- `layer - (object)`
  - Current layer spec ready to be consumed.
- `resolve - (function)`
  - resolve function from the Promise. You must resolve it always with the `layer` transformed
- `reject - (function)`
  - reject function from the Promise.



If you need to fetch something inside this function you will need to use `fetch` function exported by layer-manager. It's a little wrapper around axios and adds a `CancelToken` from axios that will cancel requests to prevent duplicate layers and bugs.

You need to send the following params
- `type - (required) - (string)`
  - get or post
- `url - (required) - (string)`
  - url where you want to get the data
- `options - (required) - (object)`
  - axios options
- `layerModel - (required) - (object)`
  - It will be used for saving the request and apply cancelation