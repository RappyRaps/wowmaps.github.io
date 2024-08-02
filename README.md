<!DOCTYPE html>
<html lang="en">
<head>
	<base target="_top">
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	
	<title>CRS.Simple example - Leaflet</title>
	
	<link rel="shortcut icon" type="image/x-icon" href="docs/images/favicon.ico" />

    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" crossorigin=""/>
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js" integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" crossorigin=""></script>

	<style>
		html, body {
			height: 100%;
			margin: 0;
		}
		.leaflet-container {
			height: 800px;
			width: 900px;
			max-width: 100%;
			max-height: 100%;
		}
	</style>

	
</head>
<body>

<div id='map'></div>

<script>

	const map = L.map('map', {
		crs: L.CRS.Simple,
		minZoom: 0,
		maxZoom: 3
	});
	
	

	const bounds = [[0, 0], [1000, 1000]];
	const image = L.imageOverlay('https://i.imgur.com/jCU6r0o.png', bounds).addTo(map);
	
	
	const poiIcon = L.Icon.extend({
		options: {
			iconSize:     [20, 20],
			iconAnchor:   [10, 10],
			shadowAnchor: [4, 62],
			popupAnchor:  [0, 0]
		}
	});
	


	//Non-Faction Based Icons
	const conflict = new poiIcon({iconUrl: 'https://i.imgur.com/Who6sQd.png'}); 			//Conflict
	const home = new poiIcon({iconUrl: 'https://i.imgur.com/0ulqRqa.png'});					//Homes
	const shrine = new poiIcon({iconUrl: 'https://i.imgur.com/3OQQUYI.png'});				//Shrines
	const poi = new poiIcon({iconUrl: 'https://i.imgur.com/aY5K7WB.png'});					//POI
	
	
	
	// MARKERS
	//const bobsteveconflict = L.marker([306, 278], {icon: conflict}).addTo(map)
	//	.bindPopup('<b>Conflict!</b><br />Currently, Bob and Steve are Fighting!').openPopup();

		
	//const marker = L.marker([430, 210], {icon: poi}).addTo(map)
	//		.bindPopup('<b>Hello world!</b><br />I am a Place of Interest at' ).openPopup();
	
	//const marker2 = L.marker([300, 200], {icon: poi}).addTo(map)
	//		.bindPopup('<b>Hello world!</b><br />I am another Place of Interest... INSIDE a Territory!' ).openPopup();
			
			

	// TERRITORIES
	// var territorysteve = L.polygon([[328, 198],	[329, 290], [305, 286],	[305, 286],	[277, 251],	[277, 204],	[299, 183]],{color: 'red', fillColor: '#f03', fillOpacity: 0.2,weight: 0.5,}).addTo(map)
	// .bindPopup("<b>Steves Territory!</b><br />I am Steves Territory!").openPopup();
	
	// var territorybob = L.polygon([[325,286],[295,260], [300,300]],{color: 'blue', fillColor: '#f03', fillOpacity: 0.1,weight: 0.5,}).addTo(map)
	// .bindPopup("<b>I am Bobs Territory!</b><br />I am Bobs Territory!").openPopup();
	
	
	/// Beacon City Stuff
	const BeaconCity= L.circle([700, 452], {
		color: 'red',
		fillColor: '#f03',
		fillOpacity: 0.1,
		weight: 0.5,
		radius: 45
	}).addTo(map).bindPopup('<h1>Beacon City</h1> <h2>The City of Light</h2> <p>The city build upon the ruins of another city. Nestled in the massive caldera of the now dormant (<i>possibly</i> extinct) Volcano.</p><p>All caro know that this city, and it\'s local residence have a higher tolerance for wandering caros and generally friendlier attitude due to their eclectic stances. Little has been fought over this little Haven.<br> <br><i>All Welcomed!</i><br>Territory Conflict: No. <br>Recruiting: Yes, Always Open<br>Visitors: Yes<br> Managed by: SlapDrink.<br> <br> This location is a \'Starting Zone\' for newcomers to introduce themselves to the map. For reasons, this zone cannot be in Conflict with any other territory.' );
	
	const BCtrack = L.marker([671, 442], {icon: poi}).addTo(map)
		.bindPopup('<h1>Beacon City Track</h1><p>An old and dilapilated megastructure, with a long massive cross-country racetrack.</p>').openPopup();

		const Beaconlight = L.marker([693, 457], {icon: poi}).addTo(map)
		.bindPopup('<h1>Beacon of Light</h1><p>An Omniscent Light that defines the entire territory of Beacon City. All know if the light of the Beacon is seen, they are in the confines of the Praxis, the four defining laws of the territory.</p>').openPopup();
	
		const manuelhome = L.marker([665, 453], {icon: home}).addTo(map)
		.bindPopup('<h1>Manuel\'s Home</h1><p>A familiar face lives here...</p>').openPopup();
	
		const TheStrays = L.marker([700, 450], {icon: poi}).addTo(map)
		.bindPopup('<h1>The Stray Market</h1><p>A hidden alcove where many items are traded and sold through the world.</p>').openPopup();
	

	
	var popup = L.popup();
	function onMapClick(e) {
    popup
        .setLatLng(e.latlng)
        .setContent("You clicked the map at " + e.latlng.toString())
        .openOn(map);
	}
	
	
	var CIcon = L.Icon.extend({
    options: {
        iconSize:     [38, 95],
        shadowSize:   [50, 64],
        iconAnchor:   [22, 94],
        shadowAnchor: [4, 62],
        popupAnchor:  [-3, -76]
    }
	

});

	map.on('click', onMapClick);

	map.setView([500, 500], 0.25);

</script>



</body>
</html>
