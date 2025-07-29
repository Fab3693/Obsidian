## @Qualifier 
- Уточняет, какой именно бин использовать, если несколько подходят по типу.
```java
@Autowired
@Qualifier("mysqlRepository")
private Repository repository;
```
![[Pasted image 20250721144444.png]]
![[Pasted image 20250721144627.png]]