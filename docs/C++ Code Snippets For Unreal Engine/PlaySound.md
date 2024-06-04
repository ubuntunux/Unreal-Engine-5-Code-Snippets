> [Unreal Engine 5 Code Snippets](../README.md) / [C++ Code Snippets For Unreal Engine](README.md) / PlaySound.md
## PlaySound
```
// .h
UPROPERTY(BlueprintReadWrite, EditDefaultsOnly, Category="Default")
TObjectPtr<USoundWave> Sound;

// .cpp
#include "Kismet/GameplayStatics.h"

// load bgm.uasset
Sound = LoadObject<USoundWave>(nullptr, TEXT("/Game/Sounds/bgm.bgm"));

// play sound 2d
UGameplayStatics::PlaySound2D(GetWorld(), Sound);
```