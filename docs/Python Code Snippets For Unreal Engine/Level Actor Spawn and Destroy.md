> [Unreal Engine 5 Code Snippets](../README.md) / [Python Code Snippets For Unreal Engine](README.md) / Level Actor Spawn and Destroy.md
## Level Actor Spawn and Destroy
* [unreal.EditorActorSubsystem](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/EditorActorSubsystem.html)
* [unreal.EditorAssetLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/EditorAssetLibrary.html#unreal.EditorAssetLibrary)
* [unreal.StringLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/StringLibrary.html)

```
# spawn static mesh actor
asset_path = ''
asset = unreal.EditorAssetLibrary.load_asset(asset_path)
location, is_valid_location = unreal.StringLibrary.conv_string_to_vector('(X=-0,Y=0,Z=0)')
rotation, is_valid_rotation = unreal.StringLibrary.conv_string_to_rotator('(P=-0,Y=0,R=0)')
actor = unreal.EditorLevelLibrary.spawn_actor_from_object(asset, location, rotation, False)
 
# destroy actor
actor_subsystem = unreal.get_editor_subsystem(unreal.EditorActorSubsystem)
actor_subsystem.destroy_actor(actor)
```