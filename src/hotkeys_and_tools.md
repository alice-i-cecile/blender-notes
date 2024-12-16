# Hotkeys and Tools

This isn't a full list: see Edit > Preferences > Keymap for a full listing.

The standard hot key is listed, but I also include notes about the how / what / why for each tool here.

## Universal

- Undo: Ctrl + Z
- Redo: Ctrl + Shift + Z
- Save: Ctrl + S
- Change modes: Tab

## Camera Movement

- Middle click + drag: orbit
- Mouse wheel: zoom
- Shift + middle click + drag: pan
- Orthographic views:
  - use the view widget in the top right
  - Numpad 1/3/7/9 for orthographic views
  - Numpad 5 to toggle orthographic views

## Selection

- Select all: A
- Delete selected: Delete
- Deselect: click on empty space?

## Object Mode

- Add object: Shift + A
  - Mesh is by far the most important class for standard 3D game dev

## General Editing

- Translate: G
  - Position object on top of ground plane
    - Go to an orthographic view (Numpad 1)
    - Translate (G) along Z axis (Z) until it's close to the ground plane
    - Toggle snapping (Shift + S / Shift + Tab) and snap to grid
- Rotate: R
- Scale: S
- Lock axes: X / Y / Z during a transform operation
  - Only transformations along that axis will be allowed
  - Red is X, Blue is Y, Green is Z
- Snapping: Shift + S for wheel menu, Shift + Tab for snap during transform
  - Use magnet icon on the top to control behavior
  - Snap to grid for easy global alignment
  - Snap to faces / vertices edges to connect to other objects
  - Zoom in more to get another 10x grid divisions

## View and Overlays

- X-ray mode (Alt+Z)
  - see into / through meshes
- Viewport Shading
  - Wireframe / Solid / Material Preview / Rendered Display
    - rendered isn't super useful for game dev
  - Change material color to black + flat lighting to check silhouette

## Edit Mode

### Modes

- Mirror mesh geometry (Butterfly in the top right)
  - Extremely useful and safer than mirror modifier

## Selection

- Vertex / Edge / Face select mode (1/2/3)
  - Top left of edit mode
- Select edge loop (Alt + Left Click)

## Building Base Geometry

- Extrude (E)
  - Very useful for creating geometry quickly
- Loop Cut and Slide (Ctrl + R)
  - Creating edge loops is ideal for adding detail
  - Right click to divide at even points
  - Drag to adjust divisions
  - Can increase number of cuts and smoothness!
- Bridge Edge Loops
  - Connect weird gaps smoothly
- Knife Tool (K)
  - Cut apart geometry
- Boolean operations (Ctrl + Shift + B)
  - Create two mesh objects
  - Make them overlap
  - Select them both
  - Open the Bool Tools menu
    - Make sure the extension is installed!
  - Select an operation: Union, Intersection, Difference, Slice
    - Difference subtracts the first selected object from the second

## Polishing Geometry

- Bevel (Ctrl + B)
  - Can bevel both vertices and edges
- Face inset
  - Great for making chimneys

## More Detail

- Subdivide (S)
  - Increase detail!
- Poke Faces (Ctrl + F -> P)
  - Turns face into a fan
- Triangulate Faces (Ctrl + T)

## Less Detail

- Merge Vertices (M)
  - Collapse geometry
- Dissolve Vertices / Edges / Faces

## Tweaking Geometry

- Slide Vertices (Ctrl + V)
  - Safe constrained adjustments

## Normals

- Shade Flat vs Shade Smooth
  - Flat will have sharp creases: good for hard surface modelling
  - Shade smooth will have soft edges: good for organics
- Detailed control can be obtained for each edge through the Edge view's right click menu

## Working with Parts

- Separate
  - Split into multiple objects by selection, material or loose parts
- Join (Object mode)
  - Simply groups objects
- Boolean Union
  - Actually unifies overlapping geometry