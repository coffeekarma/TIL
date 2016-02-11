# Type inference

Useful to initialize hashmaps:

```java
public static <K, V> HashMap<K, V> newInstance() {
    return new HashMap<K, V>();
}
```

