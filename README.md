# Frenet

[![Clojars Project](https://img.shields.io/clojars/v/frenet.svg)](https://clojars.org/frenet)

The right coordinate system often makes things easier. In the case of
a winding road, it is much easier to deal with distance along the road
and distance to the right of center, rather than dealing with (x,y)
coordinates.

The frenet library allows you to define such a coordinate system based
on a list of (x,y) points along a path. The s coordinate measures
distance along that path. The d coordinate measures distance to the
right of the path.

The frenet library includes converters between (x,y) and (s,d). There
are also options to convert velocity between (vx,vy) and (vs,vd).

## Installation

Add the following dependency to your `project.clj` file:

    [frenet "0.1.0"]

## Usage

This code snippet demonstrates how each function is used:

```clojure
(ns hello-world.core
  (:require [frenet.core :as frenet]))

(def coordinates
  (frenet/track [[0 0] [1 2] [2 3.5] [3 4.5] [4 4.5]
                 [5 4] [6 3] [7 2.7] [8 3.3] [9 4.6]]))

(frenet/xy->sd coordinates 1.0   2.0) ; [2.236 0.0]
(frenet/sd->xy coordinates 2.236 0.0) ; [1.0   2.0]

(frenet/xyv->sdv coordinates 1.0   2.0 1.5   0.5)   ; [2.236 0.0 1.216 1.036]
(frenet/sdv->xyv coordinates 2.236 0.0 1.216 1.036) ; [1.0   2.0 1.5   0.5  ]
```

See tests for more details.

## License

Copyright © 2018 Eric Lavigne

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
