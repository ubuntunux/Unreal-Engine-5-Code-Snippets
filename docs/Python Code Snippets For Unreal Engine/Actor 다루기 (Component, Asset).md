> [Unreal Engine 5 Code Snippets](../README.md) / [Python Code Snippets For Unreal Engine](README.md) / Actor 다루기 (Component, Asset).md
## Actor 다루기 (Component, Asset)
```
import unreal
 
# level의 actor 목록 얻어오기
level_actors = unreal.EditorLevelLibrary.get_all_level_actors()
static_mesh_actors = unreal.EditorFilterLibrary.by_class(level_actors, unreal.StaticMeshActor)
actor = static_mesh_actors[0]
 
# 위치 얻어오기
actor_location = unreal.StringLibrary.conv_vector_to_string(actor.get_actor_location())
 
# static mesh component 얻어오기
static_mesh_components = actor.get_components_by_class(unreal.StaticMeshComponent)
component = static_mesh_components[0]
 
# static mesh asset의 경로 얻어오기
asset_path = component.static_mesh.get_full_name()
```