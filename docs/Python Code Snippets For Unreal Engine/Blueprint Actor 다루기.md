> [Unreal Engine 5 Code Snippets](../README.md) / [Python Code Snippets For Unreal Engine](README.md) / Blueprint Actor 다루기.md
## Blueprint Actor 다루기
```
import unreal
import re
 
# level의 actor 목록 얻어오기
level_actors = unreal.EditorLevelLibrary.get_all_level_actors()
 
# blueprint로 부터 파생된 actor들만 모으기
bp_actors = [actor for actor in level_actors if actor.get_class().__class__ is unreal.BlueprintGeneratedClass]
bp_actor = bp_actors[0]
 
# blueprint actor의 blueprint asset 경로 알아내기
class_info = str(bp_actor.get_class())
 
# 정규식 준비
re_split_class_name = re.compile(".+?\'(.+?)\'.+?Class \'(.+?)\'")
 
# blueprint인 경우 class_path가 asset의 경로가 된다.
class_path, class_of_class = re_split_class_name.match(class_path).groups()
```