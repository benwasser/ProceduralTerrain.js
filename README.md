ProceduralTerrain.js
====================

A module for generating 2D procedurally-generated terrain and height maps using Simplex noise

See live demo here: http://benwasser.github.io/ProceduralTerrain.js/

Usage:
--------------------
```
// Include module in HTML:
<script type='application/javascript' src="proceduralterrain.js"></script>
```

Initial setup
--------------------
This generates Simplex seeds, so evolutions and changes in granularity on each ProceduralTerrain object will use the same seed
```
var map = new ProceduralTerrain({
        height:50, // Size of map
        width:50, // Size of map
        details:20, // Range of values each tile can be
        continent_factor:2, // Acts as a multiplier on the Simplex results
});
```

Generate the height, temp, and precipitation maps
--------------------
```
map.generateMaps(granularity); // Granularity is a number representing how "zoomed" in the map is

// Get the height, temp, and precipitation maps as arrays or ascii + HTML
map.getHeightMap(); // Returns 2D array of values
map.getTemperatureMap(); // Returns 2D array of values
map.getPrecipitationMap('text'); // If you add the 'text' argument, it will generate a text preview with <br /> tags
```


Getting the compiled terrain is a little different because you need to pass it a water level and it has a callback
--------------------
water_level should be whatever you set for the details option, multiplied by a float (best between 0 and 1): water_level = (details * 0.33)
```
map.compileTerrain(water_level, function(err, terrain_map){
        // The terrain_map return object is a 2D array of characters representing different materials/biomes
}
```

If all that's confusing, check out the demo HTML code