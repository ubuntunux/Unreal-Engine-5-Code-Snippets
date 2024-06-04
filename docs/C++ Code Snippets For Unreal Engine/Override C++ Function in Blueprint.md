// .h
// Class Specifiers: BlueprintType, Blueprintable
UCLASS(BlueprintType, Blueprintable) 
class MYGAME_API AMyGameMode : public AGameModeBase
{
    // decalre function
    UFUNCTION(BlueprintNativeEvent)
    void foo();
}

// .cpp
void AMyGameMode::foo_Implementation()
{
}

// now you can override in blueprint

![](img/OverrideFunction.png)