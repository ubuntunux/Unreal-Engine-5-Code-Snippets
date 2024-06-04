> [Unreal Engine 5 Code Snippets](../README.md) / [C++ Code Snippets For Unreal Engine](README.md) / Spawn NiagaraSystem.md
## Spawn NiagaraSystem
```
// .h
UPROPERTY(BlueprintReadWrite, EditDefaultsOnly, Category="Default")
TObjectPtr<UNiagaraSystem> FX;

// .cpp
#include "NiagaraFunctionLibrary.h"
#include "NiagaraComponent.h"

// load NiaragaEffect.uasset
FX = LoadObject<UNiagaraSystem>(nullptr, TEXT("/Game/Effect/NiaragaEffect.NiaragaEffect"));

// spawn niagara system
UNiagaraFunctionLibrary::SpawnSystemAtLocation(GetWorld(), FX, FVector(0, 0, 0));
```