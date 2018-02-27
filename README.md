# 2D to 3D converter for GameMaker Studio 2
## Documentation

### This is a WIP asset, so you cannot get it yet. It will be published on the Marketplace.

# Usage

Place object `o2Dto3D` where you want the 3D effect. You can also create it with `instance_create_<>` and destroy it with `instance_destroy()` for switching between 2D and 3D.

You can customize everything in that object's Create event, under the **Customize** region.

You will need to add your background & tile layers to their respective arrays in the same event.

```
background_layers = ["BKLayer1", "BKLayer2"]
tile_layers = ["TileLayer1", "TileLayer2"];
```

## Important

• Enable **Clear Viewport Background** in room viewport settings

• When you delete the `o2Dto3D` object, the camera will still be 3D. To restore the camera back to the original one, go to the object's Clean Up event and set the camera in the last line, which is commented out.

• All your tiles & background layers will be flattened into one surface. If you are using tiles for world objects like rocks, walls, houses, etc. you will need to use objects so that they can stand up.

# Objects

## Cubes

`oCube` is a cube that you can place in the room for it to show up in 3D. Resizing in the room editor is supported too.

You can set its properties in the **Variable Definitions** window, so you can also set different properties for different instances (in the room editor). The properties are the height, color, sprite and alpha of the cube.

# Collisions

## place_meeting_3d()

This function checks whether the instance running the code is colliding with anything in the 3D world. It will return `false` if 3D is not on, or if the vertex buffer for an object isn't built yet (shouldn't happen or be a problem).

### Arguments:

**xAdd:** Amount to add to the instance's x position (x + xAdd will be the final position for collision checking)

**yAdd:** Amount to add to y

**zAdd:** Amount to add to z

**Obj:** Object/instance to check for collision with

### Example:

```
if (place_meeting_3d(xSpeed, 0, 0)){
  xSpeed = 0;
}
if (place_meeting_3d(0, ySpeed, 0)){
  ySpeed = 0;
}
if (place_meeting_3d(0, 0, zSpeed)){
  zSpeed = 0;
}
```

# 3D Variables

The converter creates some variables in all of your objects. They are:

* z
* xRot, yRot, zRot
* Faces
* Billboard

You can initialize these variables yourself in your objects with a custom value to override the converter's initialization.

## z

`z` is the height where an object is positioned at. The default is `0`, which is on the ground. Positive values go upwards, negative go downwards.

## Rotation

`xRot`, `yRot` and `zRot` are the rotations of an object.

![Example](http://www.3dmax-tutorials.com/graphics/ill_rotation_trackball.gif)

## Faces

By default, each object will be given one face, but you can change the `Faces` variable to give it more. Here's what the effect looks like:

### 2 Faces

![2 Faces](https://i.imgur.com/8HrLcZS.png)

### 4 Faces

![4 Faces](https://i.imgur.com/bzyME6p.png)

## Billboard

This is 0 by default. You can set it to 1 to have the object rotate on its Z axis to face the camera, but not look up or down. You can set it to 2 to have look up and down as well.

### Billboard = 1

![1](https://i.imgur.com/zaD8ITG.png)

### Billboard = 2

![2](https://i.imgur.com/GVebdJ7.png)
