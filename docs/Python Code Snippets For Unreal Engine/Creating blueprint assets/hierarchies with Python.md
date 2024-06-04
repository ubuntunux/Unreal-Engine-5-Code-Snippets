> [Unreal Engine 5 Code Snippets](../../README.md) / [Python Code Snippets For Unreal Engine](../README.md) / [Creating blueprint assets](README.md) / hierarchies with Python.md
## hierarchies with Python
URL: [Creating blueprint assets/hierarchies with Python](https://forums.unrealengine.com/t/creating-blueprint-assets-hierarchies-with-python/115929)

```
import unreal
 
asset_name = "MyAwesomeBPActorClass"
package_path = "/Game/MyContentFolder"
 
factory = unreal.BlueprintFactory()
factory.set_editor_property("ParentClass", unreal.Actor)
 
asset_tools = unreal.AssetToolsHelpers.get_asset_tools()
my_new_asset = asset_tools.create_asset(asset_name, package_path, None, factory)
 
unreal.EditorAssetLibrary.save_loaded_asset(my_new_asset)
```