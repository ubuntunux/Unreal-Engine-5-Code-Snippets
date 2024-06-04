> [Unreal Engine 5 Code Snippets](../README.md) / [Python Code Snippets For Unreal Engine](README.md) / Asset 목록을 얻어오는 여러가지 방법.md
## Asset 목록을 얻어오는 여러가지 방법
* [unreal.AssetRegistryHelpers](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/AssetRegistryHelpers.html#unreal.AssetRegistryHelpers)
* [unreal.EditorAssetLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/EditorAssetLibrary.html#unreal.EditorAssetLibrary)
* [unreal.EditorUtilityLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/EditorUtilityLibrary.html#unreal.EditorUtilityLibrary)
* [ unreal.EditorLevelLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/EditorLevelLibrary.html#unreal.EditorLevelLibrary)
* [unreal.EditorFilterLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/EditorFilterLibrary.html#unreal.EditorFilterLibrary)

```
import unreal

# level의 actor 목록 얻어오기
level_actors = unreal.EditorLevelLibrary.get_all_level_actors()
static_mesh_actors = unreal.EditorFilterLibrary.by_class(level_actors,unreal.StaticMeshActor)
skeletal_mesh_actors = unreal.EditorFilterLibrary.by_class(level_actors,unreal.SkeletalMeshActor)
 
# ContentBrowser에서 선택된 Asset 목록 얻어 오기
selected_assets = unreal.EditorUtilityLibrary.get_selected_assets()
 
# 예) Content/AssetRef 폴더의 Asset목록 얻어 오기
folder_assets = unreal.EditorAssetLibrary.list_assets('/Game/AssetRef',True)
 
# 예) UE5에서  전체 StaticMesh Asset 목록 얻어오기
class_name = 'StaticMesh'
asset_registry = unreal.AssetRegistryHelpers.get_asset_registry()
static_mesh_assets = asset_registry.get_assets_by_class(unreal.TopLevelAssetPath('/Script/Engine', class_name))
 
# 예) UE4에서  전체 StaticMesh Asset 목록 얻어오기
class_name = 'StaticMesh'
asset_registry = unreal.AssetRegistryHelpers.get_asset_registry()
static_mesh_assets = asset_registry.get_assets_by_class(unreal.StringLibrary.conv_string_to_name( class_name ), False)
```