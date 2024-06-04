> [Unreal Engine 5 Code Snippets](../README.md) / [Python Code Snippets For Unreal Engine](README.md) / unreal.FXConverterUtilitiesLibrary.md
## unreal.FXConverterUtilitiesLibrary


```
import unreal
 
# particle asset 목록 얻어오기
class_name = 'ParticleSystem'
asset_registry = unreal.AssetRegistryHelpers.get_asset_registry()
particle_data_list = asset_registry.get_assets_by_class(unreal.TopLevelAssetPath('/Script/Engine', class_name))
particles = [asset_data.get_asset() for asset_data in particle_data_list]
 
# 첫번째 particle
particle = particles[0]
 
# emitter 목록 얻어오기
fx_library = unreal.FXConverterUtilitiesLibrary
emitters = fx_library .get_cascade_system_emitters(particle)
 
# 첫번쨰 emitter
 emitter =  emitters [0]
```