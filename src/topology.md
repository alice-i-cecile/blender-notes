# Mastering Topology

"Good topology" is something that blender gurus love to talk about.
But what does it mean, and why do we care?

Topology (in the 3D modelling sense) is the underlying structural elements of the mesh: the vertexs, edges and faces.

## What is bad topology?

There's a number of serious problems to look out for:

- loose edges or vertices
  - messy, rendered badly
- nearly coincident parts (hi light leaks)
  - snap properly!
- severely non-planar faces (non-manifold geometry)
  - when converting to triangles to rendering, the normals will be fucked
- internal geometry
  - wasteful, buggy, won't be rendered properly
- n-gons (faces with more than 4 sides)
  - this is only actually a problem when they're non-planar!
- inconsistent detail
  - vertex density should be roughly equal everywhere unless you need that density for something like close-ups or animation

But there's also another category: topology that doesn't play nice with what I'm calling the **edge loop workflow**.

## Subdivs, LODs and Topology

Different applications, both in games and outside of it, work better with more or less geometrical detail.

In order to smoothly increase and decrease the detail in an automated way, most studios rely on two operations:

- subdivision surfaces: increase the number of polygons by dividing the existing ones in half
- decimate: selectively collapse vertices to reduce the number of polygons

Because these operations are fully algorithmic, they work much better with orderly, predictable geometry.
They really really love grids: uniformly sized, trivially divisible

## Light, shadow and curved surfaces

Curved surfaces need more detail than flat surfaces in order to maintain the same perceptual "smoothness".
The tighter the curve, the more detail it needs!
The detail is needed along the radius of the curve: adding extra edge loops around every radius works great.

As a secondary result, polygons should be longer along the axes that they're flattest. An upper arm can be made up of long strips joined into a tube, while a male chest ends up with more regular polygons.

Problems with inadequate topology around curves is easiest to see under a harsh light: the shadows will lie wrong and highlight undesired sharp edges.

## Creases, bones and animation

Adding topological detail to curved surfaces gets much more complicated when animating things!
You need more detail where things *will* curve, ideally in the preferred directions of those curves.

## The Edge Loop standard

To solve these problems, 3D modellers have developed a set of topology best practices that I'm going to call the **Edge Loop standard**.
Here are its rules, as I have determined them:

1. Strongly prefer four-sided polygons (quads). Use triangles and pentagons sparingly to divide and join tricky regions or change edge loop density.
2. Quads should be joined side-to-side and end-to-end where possible to create "edge loops" around surfaces.
3. Polygons shall be longer in the flattest direction, flowing in the direction of movement.
4. Quads should be as flat as possible.
5. Curved geometry should be reinforced with edge loops along the curve.
6. Animated joints need to be reinforced for all possible curved geometry.
7. Polygon density should be roughly equal everywhere, but scale up with complex, non-flat geometry.

This workflow is enabled by three core tools:

- Loop Cut and Slide
  - Generate density perpendicular to any axis of your choice
- Select Edge Loop
  - Quickly selects all edges (or vertices) along one of your edge loops to transform or modify.
- Subdivide
  - If you did everything right, locally or globally create well-behaved polygon density to play with
  - This same math can be applied globally via a modifier!
