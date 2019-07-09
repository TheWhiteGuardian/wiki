<!--TITLE: Rings-->
<!--Subtitle: Enchanting Italians for 300 years-->

Each Body may have a node called Rings, containing one or more Ring nodes, each of which defines a planetary ring. These may be flat discs as with Saturn, loops of ribbon as with the Ringworld, or voluminous cylinders.

Distance units for rings are milliradii, thousandths of the radius of the parent body. So 1000 is 1 radius, 2000 is 2 radii, etc.

```
Rings
{
    Ring
    {
        // Distance from center of parent to inner edge of ring in milliradii
        innerRadius = 2000
        // Distance from center of parent to outer edge of ring in milliradii
        outerRadius = 4000
        // Distance between top and bottom faces of ring in milliradii
        thickness = 100
        // Number of quad strips to create to represent the ring
        steps = 120

        // Path to file containing the texture, relative to GameData
        texture = MyMod/MyTexture
        // Number of times to tile the texture around the ring
        // Texture coordinates depend on this!
        // If 0, then a thin strip from (0,0) to (1,1) is applied to the whole ring.
        // Otherwise the following rectangles are tiled top-to-bottom:
        //   |      |            |            |
        //   | side |   inner    |   outer    |
        //   |      |            |            |
        //   (0.0,0)-(0.2,1): Top/bottom edges
        //   (0.2,0)-(0.6,1): Inner edge
        //   (0.6,0)-(1.0,1): Outer edge
        tiles = 10
        // R,G,B,A tint for ring, 0=black and 1=white
        color = 1,1,1,1
        // If true,  use the Unlit/Transparent   shader.
        // If false, use the Transparent/Diffuse shader.
        unlit = false
        // If true, use the Kopernicus/Rings shader, which allows parent body to cast shadow on ring.
        // Overrides `unlit`.
        useNewShader = false
        // An input to the NewShader.
        // Makes planet shadow softer (values larger than one) or less soft (smaller than one).
        // Softness still depends on distance from sun, distance from planet and radius of sun and planet.
        penumbraMultiplier = 200

        // Inclination in degrees
        angle = 30
        // If false, ring's LAN rotates with parent body (unnatural if `angle` not 0)
        // If true, LAN is locked in place
        lockRotation = true
        // LAN in degrees (only effective if `lockRotation` is true)
        longitudeOfAscendingNode = 30
        // Number of seconds the ring takes to rotate once (only noticeable if `tiles` not 0)
        rotationPeriod = 600

        // Added in 1.4.2-1, allows deformation of rings
        InnerRadiusMultiplier
        {
	    // key = <angle (degrees)> <multiplier> <in-tangent (optional)> <out-tangent (optional)>
   	    // add as many key values as you need
            key = 0 1 0 0
        }﻿
        OuterRadiusMultiplier
        {
            // same applies as InnerRadiusMultiplier
	    key = 0 1 0 0
        }﻿
    }
}
```