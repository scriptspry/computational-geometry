computational-geometry.js
=========================

Node.js implementations of some computational geometry algorithms:

* [Minimum square covering](https://en.wikipedia.org/wiki/Polygon_covering#Covering_a_rectilinear_polygon_with_squares);
* [Maximum disjoint set](https://en.wikipedia.org/wiki/Maximum_disjoint_set);
* [Fair cake-cutting](https://en.wikipedia.org/wiki/Fair_cake-cutting) with square pieces.

The algorithms are implemented as extensions to the [JSTS](https://github.com/bjornharrtell/jsts) library.


Installation
------------
Installation requires browserify, and it is only required if you want to run the client code.

    git clone https://github.com/erelsgl/computational-geometry.git
    cd computational-geometry
    npm install

Then, point your favorite browser to the file client/index.html to see some examples. To see it online, go to [http://tora.us.fm/geometry](http://tora.us.fm/geometry).


Examples
--------

	var jsts = require("../computational-geometry"); // contains all JSTS functionality in addition to new algorithms
	var factory = new jsts.geom.GeometryFactory();

	var srp = new jsts.geom.SimpleRectilinearPolygon([0,0, 10,10, 20,20]);
	console.log("An L-shaped simple rectilinear polygon:")
	console.dir(srp.getCoordinates());

	var covering = jsts.algorithm.minSquareCovering(srp);
	console.log("A minimum square-covering:")
	console.dir(covering);

	var squares = factory.createSquaresTouchingPoints([{x:1,y:1}, {x:2,y:1}, {x:1,y:2}]);
	console.log("A collection of "+squares.length+" squares spanned by points:")
	console.dir(squares);

	var disjointset = jsts.algorithm.maximumDisjointSet(squares);
	console.log("A maximum disjoint set of "+disjointset.length+" squares:");
	console.dir(disjointset);


Status
------
The algorithms work in many cases but they are NOT fully tested. See the test/ folder
for the cases that do work.
