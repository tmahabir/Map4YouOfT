![Banner](/Images/coverPage.png)
# Map4YouOfT
Map 4 YouOfT, the map for all of your first-year problems. Map 4 YouOfT is a Geographic Information System that provides first-years with a simple yet elegant map to easily discover Toronto. By focusing our features on their needs and expectations, Map 4 YouOft aims to be like the friendly, welcoming and ever-present guide that everyone should have in their years at the University of Toronto.

Written using C++, retrieves data using the OpenStreetMap Database API, and draws graphics using GTK.

NOTE: This project was made for the course ECE297 at the University of Toronto, and therefore, the source code is not available to the public.

## Main Features
* Use arrow buttons to move around 
* Use '+' and '-' buttons to zoom in/out
* Use '[ ]' button to resize the map to be fully zoomed out
* Dropdown menu to select maps for different cities
* Display streets, street names, parks, rivers, lakes, buildings, etc...
* Find optimal path between two intersections (enter these intersections by either clicking on the map or using the search bar)
	* Know the time it takes to drive along this path
	* Display easy-to-follow driving instructions to go along this path
	* Click on a specific driving instruction in the directions window and the map will show you where on the map that instruction takes place by highlighting the street or intersection it takes place on.
* Click the Frosh button to enter Frosh Mode
	* All UofT Engineering buildings will be highlighted purple with their names displayed.
	* All restaurants, cafes, parks and libraries that have specifically been chosen for first years are highlighted as purple circles.
	* The path for Frosh Week's Scavenger Hunt will be highlighted purple.
* Search Bar at the top that works depending on which mode you are in.
	* Default Mode: allows you to find a specific street
	* Click the Find button to enter Find Mode and type two streets in the search bar (separated by a comma) to find all intersections between two streets
* Click either the Intersections, Points of Interest (P.O.I.), or Feature button to enter that specific mode
	* In a specific mode, only that specific aspect will appear on the map.
	 	* Intersection Mode: users can click anywhere on the screen and the closest intersection is highlighted a dark blue while adjacent intersections are highlighted a light blue.
		* P.0.I. Mode: users can click anywhere on the screen and then use the search bar to type in the name of the POI that they want to find.
		* Feature Mode: All the parks, beaches, lakes, rivers, islands or any significant buildings are highlighted in a more vibrant colour to add contrast.
	* Can combine the multiple modes listed above to be able to customize what is displayed on the map.
* Status Bar at the bottom to display any relevant information
* Night Mode
* Help Box

## Algorithms
### Setting up a Graph data structure
Our map represents the information retrieved from the OSM Database as a directed, weighted graph. The nodes of the graph represent city intersections, and the edges represent street segments that connect two intersections together. The weight of each edge represents the travel time to get from one intersection to another, which was calculated from the length of the street divided by the speed limit. 

### Pathfinding using A* Search Algorithm
Our map implements the A* Search algorithm to search for the shortest path between two intersections. Since we know the travel time to get from one intersection to another, our algorithm uses a greedy approach to always travel to the next intersection with the lowest time cost. Also, our algorithm takes into account a heuristic (which is the Euclidean distance between the start,end intersection, divided by the maximum speed limit in the city) to find the next intersection. This allows our algorithm to favor routes that get us closer to the destination, which allows us to find the shortest path much more quickly. 

### Traveling Salesman/Courier Problem - NP Hard Problem
Given a set of dropoff/pickup points, and a set of start/end intersections, our algorithm attempts to find the optimal path that reaches all the intersections. Since this type of problem is an example of a NP Hard problem, our algorithm finds a few "mediocre" solutions, then continues to make improvements until we end up with a relatively optimal path in a reasonable amount of time. 

For our initial "baseline" solution, we try starting at every possible depot(start point), and use a greedy algorithm to always travel to the next closest pickup or dropoff point from the current location. Then, using the best "baseline" solution, we try swapping the order of two random intersections continuously to look for a more optimal path until we run out of time which we set as a hard limit of 50 seconds.


## Screenshots
| Main Screen  | Zoom-Levels |
| ------------- | ------------- |
| ![Main Screen](/Images/mainScreen.png)  | ![Zoom-Levels](/Images/zoomLevels.gif) |

| Changing Maps  | Night Mode |
| ------------- | ------------- |
| ![Changing Maps](/Images/changingMaps.gif)  | ![Night Mode](/Images/nightMode.png) |

| Path-Finding  | Directions |
| ------------- | ------------- |
| ![Path Finding](/Images/pathFinding.gif)  | ![Directions](/Images/directions.gif) |

| Search Bar: Streets  | Search Bar: Intersections |
| ------------- | ------------- |
| ![Searching Streets](/Images/searchStreet.gif)  | ![Searching Intersections](/Images/searchIntersection.gif) |

| Search Bar: Points Of Interest  | Frosh Mode |
| ------------- | ------------- |
| ![Searching P.O.I.](/Images/poiFinding.gif)  | ![Frosh Mode](/Images/froshMode.gif) |

| Intersection Mode  | Feature Mode |
| ------------- | ------------- |
| ![Intersection Mode](/Images/intersectionMode.gif)  | ![Feature Mode](/Images/featureMode.gif) |
