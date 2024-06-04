> [Unreal Engine 5 Code Snippets](../README.md) / [Python Code Snippets For Unreal Engine](README.md) / unreal.SystemLibrary.md
## unreal.SystemLibrary
```
# unreal engine 버전
version = unreal.SystemLibrary.get_engine_version ()
print(version)
'4.27.2-1285477+++tl+ue4.27.2_tl'
 
# 디버깅용 박스 렌더링
unreal.SystemLibrary.draw_debug_line(world_context_object, line_start, line_end, line_color, duration=0.000000, thickness=0.000000)
```