```
bool result = someActor->IsA(AMyClass::StaticClass());

// if success then myClass is not null
AMyClass* myClass = Cast<AMyClass>(someActor);
```