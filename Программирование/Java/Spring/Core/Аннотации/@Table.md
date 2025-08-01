### 🗂 **@Table**

**Простыми словами:** `@Table` используется в [[Entity]]-классе, чтобы указать, **к какой таблице БД он привязан**. Без этой аннотации JPA автоматически возьмёт имя класса как имя таблицы.

---

#### ⚙️ **Зачем использовать `@Table`**

- Указать **точное имя таблицы** (особенно если оно не совпадает с названием класса)
    
- Настроить **индексы** и **уникальные ограничения**
    

---

#### 🔧 **Простой пример:**

```java
@Entity
@Table(name = "users")
public class User {

    @Id
    private Long id;

    @Column(nullable = false)
    private String username;
}
```

📌 Здесь таблица в БД называется `users`, хотя класс называется `User`.

---

#### 🔒 **С индексами и ограничениями:**

```java
@Entity
@Table(
    name = "users",
    uniqueConstraints = @UniqueConstraint(columnNames = "username"),
    indexes = {
        @Index(name = "idx_email", columnList = "email")
    }
)
public class User {
    @Id
    private Long id;

    @Column(nullable = false)
    private String username;

    @Column
    private String email;
}
```

---

#### 🧠 **Когда `@Table` не нужен?**

Если:

- имя таблицы совпадает с именем класса (например, `User` → `user`),
    
- и не нужны индексы или ограничения,
    

тогда `@Table` можно не писать.

---

#### 🔗 **Связанные термины:**

- [[Entity]]
    
- [[@Id]]
    
- [[@Column]]
    
- [[JPA]]
    
- [[Hibernate]]
    

---

#java #jpa #hibernate #table #orm #entity