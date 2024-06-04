> [Unreal Engine 5 Code Snippets](../README.md) / [C++ Code Snippets For Unreal Engine](README.md) / Spawn Blueprint Actor from C++.md
## Spawn Blueprint Actor from C++
Solution 1: cpp example
```
// .cpp
UObject* cls = StaticLoadObject(UObject::StaticClass(), nullptr, TEXT("/Game/Blueprint/BP_Actor.BP_Actor"));
UBlueprint* bp = Cast<UBlueprint>(cls);
TSubclassOf<class UObject> blockBP = (UClass*)bp->GeneratedClass;
GetWorld()->SpawnActor<AActor>(blockBP, FVector::ZeroVector, FRotator::ZeroRotator);
```

Solution 2: cpp example
```
// .h
UPROPERTY(BlueprintReadWrite, EditDefaultsOnly, Category="Default")
TObjectPtr<UBlueprint> BP_Actor;

// .cpp
BP_Actor = LoadObject<UBlueprint>(nullptr, TEXT("/Game/Blueprint/BP_Actor.BP_Actor"));
TSubclassOf<class UObject> blockBP = (UClass*)BP_Actor->GeneratedClass;
GetWorld()->SpawnActor<AActor>(blockBP, out_spawnPosition, FRotator::ZeroRotator);
```

Solution 3: cpp + blueprint
```
// .h
UPROPERTY(BlueprintReadWrite, EditDefaultsOnly, Category="Default")
TSubclassOf<AActor> SpawnToActor;

// .cpp
GetWorld()->SpawnActor<AActor>(SpawnToActor, FVector::ZeroVector, FRotator::ZeroRotator);

// Create Blueprint from .cpp then bind SpawnToActor
```