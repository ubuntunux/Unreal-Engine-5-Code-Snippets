> [Unreal Engine 5 Code Snippets](../README.md) / [C++ Code Snippets For Unreal Engine](README.md) / Type Check.md
## Type Check
```
bool result = someActor->IsA(AMyClass::StaticClass());

// if success then myClass is not null
AMyClass* myClass = Cast<AMyClass>(someActor);
```