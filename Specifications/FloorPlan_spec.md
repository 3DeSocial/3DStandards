
# FloorPlan Specification  [Draft]


## Overview

This document outlines an approach for storing a floor plan for a virtual location.

The purpose of a floor plan is to store the positions at which 3D Objects or NFTs can be displayed.

This is useful for automatically filling a room with items, for example when creating a 3D gallery space.

The use case for this specification is to enable the minting of virtual locations consisting of a 3D environment model plus metadata explaining how to use the model. 

Floor plans are part of the metadata for a location.

### FloorPlan Sections

The floorPlan is divided into sections based on geometrical shapes which can be calculated by a layout plotter.

The grouping types so far are:

#### Circle

Properties:

type:'circle' - Indicates items will be plotted evenly in a circle.

radius: <number of meters> - distance from the center to the circle in meters.

maxItems: <number of items> The number of items that will be plotted evenly around the circle.

center: {x:0,y: 0,z: 0} (Optional) - The center of the circle in 3D space. Defaults to 0,0,0

#### Row

type:'row' - Indicates items will be plotted evenly between two points.

start: {x:0,y: 0,z: 0}

end: {x:0,y: 0,z: 0}

maxItems: <maximum number of items in this row>

#### CenterPiece

type:'circle' - Indicates item will be plotted in the highest priority / central place 

center: {x:0,y: 0,z: 0} (Optional) - The position to be plotted in 3D space. Defaults to 0,0,0

### JSON Example


```

floorPlan: [{type:'centerPiece',
                maxItems: 1},
                {type:'circle',
                center:{x:0,y: 0,z: 0},
                radius: 9,
                maxItems: 5},
                {type:'circle',
                 center:{x:0,y: 0,z: 0},
                 radius: 19.5,
                maxItems: 10},
                {type:'circle',
                 center:{x:0,y: 0,z: 0},
                 radius: 31,
                maxItems: 10,
                size: 4}]
```
