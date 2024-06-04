> [Unreal Engine 5 Code Snippets](../../../README.md) / [Python Code Snippets For Unreal Engine](../../README.md) / [Level Create](../README.md) / [Load](README.md) / Save.md
## Save
* [unreal.EditorLevelLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/EditorLevelLibrary.html)
* [unreal.EditorLoadingAndSavingUtils](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/EditorLoadingAndSavingUtils.html)

```
import unreal
 
# create level
level_name = ‘/Game/Maps/test1’
level_library= unreal.EditorLevelLibrary()
success = level_library.new_level(level_name)
 
# load level
success = level_library.load_level(level_name)
 
# save level
success  = level_library.save_current_level()
 
# save selected level in contents browser
selected_assets = unreal.EditorUtilityLibrary.get_selected_assets()
for level in selected_assets:StringLibrary     asset_path = level.get_path_name().split('.')[0]
    unreal.EditorLoadingAndSavingUtils.save_map(level, asset_path)
```