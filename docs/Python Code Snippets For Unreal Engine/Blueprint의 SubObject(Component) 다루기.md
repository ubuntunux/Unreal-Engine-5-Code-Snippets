> [Unreal Engine 5 Code Snippets](../README.md) / [Python Code Snippets For Unreal Engine](README.md) / Blueprint의 SubObject(Component) 다루기.md
## Blueprint의 SubObject(Component) 다루기
* [unreal.EditorUtilityLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/EditorUtilityLibrary.html#unreal.EditorUtilityLibrary)
* [unreal.SubobjectDataSubsystem](https://docs.unrealengine.com/5.0/en-US/PythonAPI/class/SubobjectDataSubsystem.html)
* [unreal.SubobjectDataBlueprintFunctionLibrary](https://docs.unrealengine.com/5.0/en-US/PythonAPI/class/SubobjectDataBlueprintFunctionLibrary.html)
* [unreal.StringLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/StringLibrary.html)

```
import unreal
 
blueprint_library = unreal.SubobjectDataBlueprintFunctionLibrary()
subsystem = unreal.get_engine_subsystem(unreal.SubobjectDataSubsystem)
# get blueprint
bp_data = unreal.EditorUtilityLibrary.get_selected_asset_data()[0]
bp = bp_data.get_asset()
sub_handles = subsystem.k2_gather_subobject_data_for_blueprint(bp)
sub_handle = sub_handles[1]
sub_data = blueprint_library.get_data(sub_handle)
 
# get object
sub_object_component = blueprint_library.get_object(sub_data)
 
# get name
component_name = blueprint_library.get_variable_name(sub_data)
 
# set name
subsystem.rename_subobject(sub_handle, "StaticMesh_House_00")
 
# set relative location
location, is_valid = unreal.StringLibrary.conv_string_to_vector('(X=-208.000000,Y=-1877.000000,Z=662.000000)')
sub_object_component.set_editor_property('RelativeLocation', location)
```