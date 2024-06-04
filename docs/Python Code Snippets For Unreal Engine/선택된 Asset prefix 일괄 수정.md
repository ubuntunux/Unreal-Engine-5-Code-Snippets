> [Unreal Engine 5 Code Snippets](../README.md) / [Python Code Snippets For Unreal Engine](README.md) / 선택된 Asset prefix 일괄 수정.md
## 선택된 Asset prefix 일괄 수정
```
import unreal
 
prefix_mapping = {
    "Blueprint"      : "BP_",
    "Material"       : "M_",
    "MaterialInstanceConstant": "MI_",
    "Materiafuntion" : "MF_",
    "NiagaraSystem"  : "NS_",
    "NiagaraScript"  : "NSC_",
    "NiagaraEmitter" : "NE_",
    "Texture2D"      : "T_",
    "StaticMesh"     : "SM_",
    "SkeletalMesh"   : "SK_"
}
 
sys_lib = unreal.SystemLibrary()
edit_lib = unreal.EditorUtilityLibrary()
selected_assets = edit_lib.get_selected_assets()
for asset in selected_assets:
    asset_name = sys_lib.get_object_name(asset)
    asset_class = asset.get_class()
    class_name = sys_lib.get_class_display_name(asset_class)
    if prefix_mapping.get(class_name, None):
        if not asset_name.startswith(class_prefix):
            new_name = class_prefix + asset_name
            edit_lib.rename_asset(asset, new_name)
```