## @PostConstruct 
- Метод, вызываемый сразу после создания бина и внедрения зависимостей.
```java
@PostConstruct
public void init() {
    System.out.println("Bean initialized");
}
```
![[Pasted image 20250721150615.png]]