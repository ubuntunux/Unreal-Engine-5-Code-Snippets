> [Unreal Engine 5 Code Snippets](../README.md) / [Python Code Snippets For Unreal Engine](README.md) / Make a Blueprint class with components from Python.md
## Make a Blueprint class with components from Python
[Make a Blueprint class with components from Python](https://dev.epicgames.com/community/snippets/8zx/unreal-engine-make-a-blueprint-class-with-components-from-python)

* [unreal.BlueprintFactory](https://docs.unrealengine.com/5.0/en-US/PythonAPI/class/BlueprintFactory.html)
* [unreal.SubobjectDataSubsystem](https://docs.unrealengine.com/5.0/en-US/PythonAPI/class/SubobjectDataSubsystem.html)
* [unreal.SubobjectDataBlueprintFunctionLibrary](https://docs.unrealengine.com/5.0/en-US/PythonAPI/class/SubobjectDataBlueprintFunctionLibrary.html)

```
import unreal
 
package_path = "/Game/Blueprints"
factory = unreal.BlueprintFactory()
factory.set_editor_property("parent_class", unreal.Actor)
 
# make the blueprint
asset_tools = unreal.AssetToolsHelpers.get_asset_tools()
blueprint = asset_tools.create_asset(asset_name, package_path, None, factory)
 
# get the root data handle
subsystem = unreal.get_engine_subsystem(unreal.SubobjectDataSubsystem)
blueprint_handle = subsystem.k2_gather_subobject_data_for_blueprint(blueprint)[0]
 
# get blueprint utility    
blueprint_library = unreal.SubobjectDataBlueprintFunctionLibrary()
 
component_type = 'StaticMesh'
asset_editor_property_name = ''
asset_path = ''
 
# choose component type
if 'Blueprint' == component_type:
    new_class = unreal.ChildActorComponent
    asset_editor_property_name = 'child_actor_class'
    asset_path = '/Game/Blueprints/BP_Character'
elif 'StaticMesh' == component_type:
    new_class = unreal.StaticMeshComponent
    asset_editor_property_name = 'static_mesh'              
    asset_path = '/Game/Environments/SM_House'
elif 'SkeletalMesh' == component_type:
    new_class = unreal.SkeletalMeshComponent
    asset_editor_property_name = 'skeletal_mesh'
    asset_path = '/Game/Characters/SK_Skeleton'
 
# add sub component
params = unreal.AddNewSubobjectParams(parent_handle=blueprint_handle, new_class=new_class, blueprint_context=blueprint)
sub_handle, fail_reason = subsystem.add_new_subobject(params)
if not fail_reason.is_empty():
    raise Exception("ERROR from sub_object_subsystem.add_new_subobject: {fail_reason}" )
 
# attach
subsystem.attach_subobject( blueprint_handle, sub_handle )
 
# get object and component
sub_data = blueprint_library.get_data(sub_handle)
sub_component = blueprint_library.get_object(sub_data)
 
# set static mesh asset
asset = unreal.EditorAssetLibrary.load_asset(asset_path)
if asset is not None:
    sub_component.set_editor_property(asset_editor_property_name, asset)
 
# set relative location
location, is_valid = unreal.StringLibrary.conv_string_to_vector('(X=-208.000000,Y=-1877.000000,Z=662.000000)')
sub_component.set_editor_property('RelativeLocation', location)
```