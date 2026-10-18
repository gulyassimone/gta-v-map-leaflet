# GTA V MAP LEAFLET 
GTA V MAP LEAFLET is a MAP  based on LEAFLET.

**[Documentation](https://docs.ricearaul.com/gta-v-map/)**

## Features

* Easy to use
* Custom Icons
* 3 Map Style(Atlas,Satellite,Grid)

## Dependencies
Map Styles
```
  https://mega.nz/file/UKo0wI4A#hDZV1RE-KU0rF2BePRjaKQfwWVBvWbsBVAFmM7yWvo8
```
Leaflet
```
 https://leafletjs.com/
```
## Install
```
  Extract map styles in source folder
```
## How to use
Create blip
The coordinates are inverted X will be Y and Y will be X.
```
var X  = 0;
var Y = 0;
L.marker([Y,X], {icon: customIcon(1)}).addTo(Icons["Example"]).bindPopup("I am here.");
```
How use CustomIcon
The parameter in the customIcon function is the name of the .png picture in the blips folder
```
For /blips/1.png we will use customIcon(1)
```
## Screenshots
| Atlas         |   Grid        |    Satellite    | 
| ------------- | ------------- | ----------------| 
| !["Atlas Screenshot"](https://docs.ricearaul.com/gta-v-map/sattelite.png)  | !["Grid Screebshot"](https://docs.ricearaul.com//gta-v-map/atlas.png)  |    !["Satellite Screenshot"](https://docs.ricearaul.com//gta-v-map/grid.png)             | 

## Install via npm

[![npm](https://img.shields.io/npm/v/gta-v-map)](https://www.npmjs.com/package/gta-v-map)

```
npm install gta-v-map
```

## Support

If you find this project useful, consider supporting its development:

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/ricearaul)

## License

GTA V MAP LEAFLET is licensed under MIT License.

## Local single-image integration

The supplied raster is stored at `assets/satellite.jpg`. The trucking preview
build copies this image and `dist/gta-v-map.es.js` into its own NUI distribution;
this library does not need a FiveM manifest or a separate `ensure` command.

```html
<gta-v-map image-url="map/satellite.jpg" blips-url="map/blips"
  blip-extension="svg" min-zoom="0" max-zoom="6"
  disable-clustering hide-zoom-control></gta-v-map>
```

Leaflet CSS is bundled locally. `leaflet-css-url` remains an optional override.
With `image-url`, the component uses one image overlay and makes no tile requests.
Without it, the existing satellite/atlas/grid tile mode remains available.
Markers, shapes, heatmaps, groups and click/place events remain available in both
modes. Alternative base styles still require their own tile assets.

`image-bounds` is `[[southY, westX], [northY, eastX]]`, in GTA game units.
The supplied default is derived from the existing GTA CRS over the complete
256×256 base map: x = (pixelX - 117.3) / 0.02072,
y = (172.8 - pixelY) / 0.0205. This preserves the original calibration; verify
known in-game landmarks before using a different crop. The 8192×8192 raster
scales into those bounds without changing the coordinate API.

`resetView()` fits the whole image; `changeZoom(delta)` supports host controls.
A ResizeObserver updates the viewport on layout changes. Disconnection removes
Leaflet listeners/layers and the observer; reconnection recreates the map.
Declarative markers now use the same registry as imperative markers, so updates
and removals do not leave orphan layers.
