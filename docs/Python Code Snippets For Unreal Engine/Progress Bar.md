* [unreal.ScopedSlowTask](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/ScopedSlowTask.html)


```
import unreal
 
jobs = list(range(10))
 
num_frames = len( jobs )
with unreal.ScopedSlowTask(num_frames, "adding StaticMeshes...") as slow_task:
    slow_task.make_dialog(True)
    for num in  jobs:
        # do some slow job
        print(num)
        slow_task.enter_progress_frame(1)
```