### 🧾 **@Query**

**Простыми словами:** аннотация `@Query` позволяет **вручную задать SQL или JPQL-запрос** в методе репозитория, если Spring Data JPA не может сгенерировать его автоматически.

---

### ⚙️ **Когда использовать?**

- Когда метод слишком сложен для автогенерации (`findByNameAndAgeLessThan`)
    
- Когда нужен `JOIN`, `GROUP BY`, подзапрос или агрегация
    
- Когда нужно написать **нативный SQL** (через `nativeQuery = true`)
    

---

### 📌 **Пример с JPQL**

```java
public interface UserRepository extends JpaRepository<User, Long> {

    @Query("SELECT u FROM User u WHERE u.age > :age")
    List<User> findUsersOlderThan(@Param("age") int age);
}
```

📍 Здесь используется **JPQL** (Java Persistence Query Language), где `User` — имя Entity, а не таблицы.

---

### 🧾 **Пример с нативным SQL**

```java
@Query(value = "SELECT * FROM users WHERE email = :email", nativeQuery = true)
User findByEmail(@Param("email") String email);
```

📍 Здесь уже обращение к **реальной таблице** (`users`) и обычный SQL.

---

### 🧠 **Особенности**

- `@Query` можно применять к методам в интерфейсах с `@Repository`
    
- Используй `@Param("...")` для привязки аргументов метода
    
- Можно возвращать DTO, Entity, коллекции, `Optional`
    

---

### 🔗 **Связанные термины**

- [[@Repository]]
    
- [[@Param]]
    
- [[JPA]]
    
- [[Entity]]
    
- [[DTO]]
    
- [[@Transactional]]
    

---

#jpa #springdata #query #sql #repository