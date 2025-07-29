## @PreDestroy 
- Метод, вызываемый перед удалением бина (например, при завершении контекста).
```java
@PreDestroy
public void cleanup() {
    System.out.println("Bean destroyed");
}
```
![[Pasted image 20250721150625.png]]