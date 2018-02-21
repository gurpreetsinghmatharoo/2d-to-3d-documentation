# 2D to 3D converter for GameMaker Studio 2
## Documentation

### This is a WIP asset, so you cannot get it yet. It will be published on the Marketplace.

# Usage

Place object `o2Dto3D` where you want the 3D effect. You can also create it with `instance_create_<>` and destroy it with `instance_destroy()` for switching between 2D and 3D.

You can customize everything in that object's Create event.
You will need to add your background & tile layers to their respective arrays in the same event.

```
background_layers = ["BKLayer1", "BKLayer2"]
tile_layers = ["TileLayer1", "TileLayer2"];
```

## Important

• Enable **Clear Viewport Background** in room viewport settings

• When you delete the `o2Dto3D` object, the camera will still be 3D. To restore the camera back to the original one, go to the object's Clean Up event and set the camera in the last line, which is commented out.

• All your tiles & background layers will be flattened into one surface. If you are using tiles for world objects like rocks, walls, houses, etc. you will need to use objects so that they can stand up.

# 3D Variables

The converter creates some variables in all of your objects. They are:

* z
* xRot, yRot, zRot
* Faces

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
