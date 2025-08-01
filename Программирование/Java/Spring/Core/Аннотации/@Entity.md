### 🏷 **@Entity**

**Простыми словами:** `@Entity` помечает Java-класс как **сущность**, которая будет **отображаться на таблицу** в базе данных. Это основа ORM в [[JPA]] и [[Hibernate]].

---

#### 🧠 **Зачем нужен `@Entity`?**

- Указывает, что класс — это объект, связанный с таблицей БД
    
- Позволяет использовать [[JPA]] для сохранения, поиска, обновления, удаления данных
    

---

#### 🧱 **Пример:**

```java
import jakarta.persistence.Entity;
import jakarta.persistence.Id;

@Entity
public class User {
    @Id
    private Long id;

    private String username;
    private String email;
}
```

👉 Теперь `User` будет автоматически связан с таблицей `user`.  
Имя таблицы можно задать через аннотацию `@Table`.

---

#### 🧩 **Часто используется вместе с:**

- [[@Id]] — первичный ключ
    
- [[@GeneratedValue]] — автоинкремент ID
    
- [[@Column]] — описание столбцов
    
- [[@Table]] — имя таблицы
    

---

#### 📚 **Связанные термины:**

- [[Entity]]
    
- [[JPA]]
    
- [[Hibernate]]
    
- [[ORM]]
    
- [[DTO]]
    

---

#java #jpa #hibernate #entity #orm