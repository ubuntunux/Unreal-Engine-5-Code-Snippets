> [Unreal Engine 5 Code Snippets](../../../../README.md) / [Python Code Snippets For Unreal Engine](../../../README.md) / [Asset - Create](../../README.md) / [Delete](../README.md) / [Load](README.md) / Save.md
#### Create/Delete Asset
* [unreal.AssetTools](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/AssetTools.html#unreal.AssetTools)
* [unreal.EditorAssetLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/EditorAssetLibrary.html#unreal.EditorAssetLibrary)

```
import os
import unreal
 
asset_tools = unreal.AssetToolsHelpers.get_asset_tools()
 
# create MaterialInstance asset
asset_folder = '/Game/MaterialInstances'
asset_name = 'MI_Test'
asset_class = unreal.MaterialInstanceConstant
factory = unreal.MaterialInstanceConstantFactoryNew()
uasset = asset_tools.create_asset(asset_name, asset_folder, asset_class, factory)
 
# delete asset
asset_path = unreal.Paths.combine([asset_folder,  asset_name])
unreal.EditorAssetLibrary.delete_asset(asset_path)
```

#### Load/Save Asset
* [unreal.EditorAssetLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/EditorAssetLibrary.html#unreal.EditorAssetLibrary)

```
import unreal
 
# load asset: BP_House Asset 불러오기
package_name = '/Game/Blueprint/BP_House.BP_House'
uasset = unreal.EditorAssetLibrary.load_asset(package_name)

# modify dirty mark for edit (option)
uasset.modify()
 
# save asset
unreal.EditorAssetLibrary.save_loaded_asset(uasset)
```
