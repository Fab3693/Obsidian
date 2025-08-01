### 📄 **@Repository**

**Простыми словами:** `@Repository` — это аннотация, которая помечает класс как **компонент уровня доступа к данным**. Такой класс содержит логику взаимодействия с базой (SQL, JPA, JDBC).

---

#### ⚙️ **Для чего нужна:**

- Помечает бин для автоматического сканирования Spring ([[@Component]]-специализация).
    
- Преобразует специфичные исключения доступа к данным в обёртки Spring (`DataAccessException`).
    
- Облегчает поддержку и тестирование слоя доступа к данным.
    

---

#### 🔤 **Пример:**

```java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    List<User> findByUsername(String username);
}
```

---

#### 🔗 **Связанные термины:**

- [[Service]]
    
- [[Entity]]
    
- [[JPA]]
    
- [[DTO]]
    

---

#spring #repository #jpa #dataaccess #dao