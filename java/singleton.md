#Singleton Pattern

An Enum with only one element is the best way to make sure that only one instance exists at all times:

```java
// Enum singleton - the preferred approach
public enum Elvis {
    INSTANCE;
    
    public void leaveTheBuilding() { ... }
}
```  
(Avoid Singletons if possible)
