## @Scope 
- Определяет область видимости бина:
- `singleton` (по умолчанию)
- `prototype`
- `request`, `session`, `application` (для web)
```java
@Component
@Scope("prototype")
public class MyPrototypeBean { }
```
![[Pasted image 20250721145045.png]]