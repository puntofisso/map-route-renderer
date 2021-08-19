# map-route-renderer
This is to render an MP4 animation of geo routes. More context here: https://twitter.com/mwichary/status/1427007100845060096

## How to 
1. Open `index.html` and take a look at the dependencies: FFMpeg, FileSaver, and D3. According to what your system is, you might need to follow diffeerent steps.
2. You need to generate a file called `map.jpg`. This can be a blank file, a real map, or whatever you fancy as background.
3. Export your Strava activities and take the `.gpx` files out. Convert them to `geojson` either using CLI `togeojson`, the command `ogr2ogr`, or any online service. Verify that the geojson files represent routes by using a service like [geojson.io](http://geojson.io).
4. Save the geojson file in `data/` as `1.geojson`, `2.geojson`, and so on
5. In `index.html`, configure the following constants to values that make sense for your setting:
  - `const FRAMERATE = 20`, the higher the smoother (but it will take a while)
  - `const ROUTE_COUNT = 75`, the number of geojson files minus one
  - `const FIRST_FRAME_TO_RENDER = 0` and `const LAST_FRAME_TO_RENDER = 1500` are basically the first and last frame of the video; the good thing is that you can generate in multiple batches if you wish so
  -  variable for D3 to centre the map correctly, i.e. `const LONGITUDE = -0.119820`, `const LATITUDE = 51.559143`, `const SCALE = 500000`
6. Run a webserver in the location (or, simply `php -S localhost:4444` might work). The page will immediately start creating the .mp4 file. Opening developer tools might give you an idea of what's going on.

You can see a rendered video on my [Twitter account](https://twitter.com/puntofisso/status/1428376603436978181), and a static image below.

<img width="652" alt="Screenshot 2021-08-19 at 17 24 10" src="https://user-images.githubusercontent.com/612999/130099388-79800495-db28-4f63-a096-2b5db5072cd6.png">
