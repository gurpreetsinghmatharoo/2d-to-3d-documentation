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

• Go to **Tools > Texture Group**s and disable **Automatically Crop**

• When you delete the `o2Dto3D` object, the camera will still be 3D. To restore the camera back to the original one, go to the object's Clean Up event and set the camera in the last line, which is commented out.

## FAQ

• All your tiles & background layers will be flattened. If you are using tiles for world objects like rocks, walls, houses, etc. you will need to use objects so that they can stand up.

# Skybox



# Z Height

Converting a game into 3D creates a variable called `z` in every object, which is the height where it's positioned at. The default is `0`, on the ground. It goes up when it is increased, and goes down when decreased.

You can initialize the z variable yourself in an object with a custom value to override the converter's initialization.
