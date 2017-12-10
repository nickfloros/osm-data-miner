# osm-data-miner
Mine open street map data using overpass-turbo api to extract
- motorway junctions 
- motorway and trunk links
- motorway and trunk roads

Extracted data is then pushed to a mongo catalogue



// retrieve road e.g. M3
[out:json][timeout:25];
(
 way["ref"="M3"]({{bbox}});
);
// print results
out body;
>>;
//(._<;>);
out skel qt;


// retrieve junction motorway and trunk links
[out:json][timeout:25];
// gather results
(
way["highway"="motorway_link"]({{bbox}});
way["highway"="trunk_link"]({{bbox}});
node["highway"="motorway_junction"]({{bbox}});
);
// print results
out body;
>>;
//(._<;>);
out skel qt;


// geojson that defines a box arround UK
{
	type: "FeatureCollection",
	features: [
		{
			type: "Feature",
			properties: { },
			geometry: {
				type: "Polygon",
				coordinates: [
					[
						[ // SW CORNER
							-10.8544921875, 
							49.82380908513249
						],
						[ // NW CORNER
							-10.8544921875,
							59.478568831926395
						],
						[ // NE CORNER
							2.021484375,
							59.478568831926395
						],
						[ // SE CORNER
							2.021484375,
							49.82380908513249
						],
						[ // SW CORNER
							-10.8544921875,
							49.82380908513249
						]
					]
				]
			}
		}
]
}
