### 🧾 **@Query**

**Простыми словами:** `@Query` позволяет **вручную задать SQL или JPQL-запрос** в методе [[@Repository]], если Spring Data JPA не может сгенерировать его автоматически.

---

### ⚙️ **Когда использовать**

- Сложные условия, которые нельзя выразить методами (`findByNameAndAgeLessThan`)
    
- Использование `JOIN`, `GROUP BY`, агрегаций
    
- Когда нужен **нативный SQL** (`nativeQuery = true`)
    
- Возврат не [[Entity]], а [[DTO]]
    

---

### 📌 **JPQL-запрос (по имени [[Entity]])**

```java
@Query("SELECT u FROM User u WHERE u.age > :age")
List<User> findUsersOlderThan(@Param("age") int age);
```

📍 Здесь `User` — это [[Entity]]-класс, а не таблица в базе.

---

### 📌 **Нативный SQL (по таблице)**

```java
@Query(value = "SELECT * FROM users WHERE email = :email", nativeQuery = true)
User findByEmail(@Param("email") String email);
```

📍 Здесь `users` — это таблица из базы, а `email` — поле таблицы или [[@Column]].

---

### 🧠 **Особенности**

- Работает только в интерфейсах с [[@Repository]]
    
- Используется с `@Param` для привязки параметров
    
- Можно использовать в методах, обёрнутых в [[@Transactional]]
    
- Поддерживает возврат одного объекта, списка, [[Optional]] или [[DTO]]
    

---

### 🔗 **Связанные термины**

- [[@Repository]]
    
- [[Entity]]
    
- [[DTO]]
    
- [[@Column]]
    
- [[@Transactional]]
    

---

#spring #jpa #query #sql #repository