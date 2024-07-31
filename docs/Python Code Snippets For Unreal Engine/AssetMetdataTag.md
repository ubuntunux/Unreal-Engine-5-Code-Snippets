## Asset Metdata Tag 활용하기

- https://dev.epicgames.com/documentation/en-us/unreal-engine/python-api/class/EditorAssetLibrary
- https://dev.epicgames.com/documentation/en-us/unreal-engine/asset-metadata-in-unreal-engine
- https://forums.unrealengine.com/t/how-to-store-text-data-with-python/688813/2

```
import unreal

#access asset metadata
eas = unreal.get_editor_subsystem(unreal.EditorAssetSubsystem)
asset = eas.load_asset("/game/NewBlueprint")
eas.set_metadata_tag(asset,"tag_name","tag_value")
eas.save_asset(asset)

#access a NewVar map variable on a custom blueprint
# get the generated class of the Blueprint (note the _C)
bp_gc = unreal.load_object(None, "/Game/NewBlueprint.NewBlueprint_C")
# get the Class Default Object (CDO) of the generated class
bp_cdo = unreal.get_default_object(bp_gc)
# set the default property values
bp_cdo.get_editor_property("NewVar")["map entry name"] = "map entry value"
#bp_cdo.set_editor_property("MyBoolProp", True)

```
