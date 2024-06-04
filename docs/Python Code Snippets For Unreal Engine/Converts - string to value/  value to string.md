> [Unreal Engine 5 Code Snippets](../../README.md) / [Python Code Snippets For Unreal Engine](../README.md) / [Converts - string to value](README.md) /   value to string.md
##   value to string
* [unreal.StringLibrary](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/StringLibrary.html)
```
import unreal
 
# String to Vector: 형식이 조금 틀리더라도 잘 변환됨
pos, is_valid  = unreal.StringLibrary.conv_string_to_vector('(X=-208.000000,Y=-1877.000000,Z=662.000000)')
pos, is_valid = unreal.StringLibrary.conv_string_to_vector('X=-208.000000,Y=-1877.000000,Z=662.000000')
pos, is_valid = unreal.StringLibrary.conv_string_to_vector('X=-208.000000 Y=-1877.000000 Z=662.000000')
 
# Vector to String
print(unreal.StringLibrary.conv_vector_to_string(pos))
# 'X=-208.000 Y=-1877.000 Z=662.000'
 
# String to Rotator: Pitch, Yaw, Roll의 앞글자만 사용함에 주의!
rotation, is_valid = unreal.StringLibrary.conv_string_to_rotator("(P=33.000000,Y=-89.999763,R=12.000000)")
 
# Rotator to String
print(unreal.StringLibrary.conv_rotator_to_string("(P=33.000000,Y=-89.999763,R=12.000000)"))
# 'P=0.000000 Y=0.000000 R=0.000000'
```