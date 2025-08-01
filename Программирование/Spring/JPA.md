### 📄 **JPA (Java Persistence API)**

**Простыми словами:** JPA — это стандарт Java для **работы с базами данных через объекты**, а не SQL-запросы. Вместо таблиц ты используешь классы, а вместо строк — объекты.

---

#### 🧩 **Что делает JPA:**

- 🔄 Автоматически сохраняет, обновляет и удаляет объекты в БД
    
- 🗂️ Связывает Java-классы с таблицами (см. [[Entity]])
    
- 🧵 Упрощает транзакции и работу с отношениями (один-ко-многим и т.д.)
    

---

#### ⚙️ **Пример использования:**

```java
@Entity
public class User {
    @Id
    @GeneratedValue
    private Long id;

    private String username;
    private String email;
}
```

```java
public interface UserRepository extends JpaRepository<User, Long> {
    List<User> findByUsername(String username);
}
```

---

#### 🧠 **Что ты получаешь с JPA:**

- 🧹 Меньше SQL — больше читаемого Java-кода
    
- 🔁 Поддержку [[ORM]] (автоматическое сопоставление объектов и таблиц)
    
- 🔌 Возможность использовать разные реализации, например [[Hibernate]]
    

---

#### 🔗 **Связанные термины**

- [[Entity]]
    
- [[ORM]]
    
- [[Hibernate]]
    
- [[DTO]]
    
- [[Spring MVC]]
    

---

#java #jpa #orm #database #hibernate #spring