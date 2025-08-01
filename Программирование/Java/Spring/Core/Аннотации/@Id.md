### 🏷 **@Id**

**Простыми словами:** `@Id` указывает, какое поле в классе является **первичным ключом** (primary key) — уникальным идентификатором записи в таблице базы данных.

---

#### 🧠 **Зачем нужен `@Id`?**

- Без него [[JPA]] и [[Hibernate]] не поймут, как отличать одну сущность от другой.
    
- Поле с `@Id` обязательно должно быть уникальным.
    

---

#### 🧱 **Пример:**

```java
import jakarta.persistence.Entity;
import jakarta.persistence.Id;

@Entity
public class Product {
    @Id
    private Long id;

    private String name;
}
```

> Без `@Id` JPA-реализация (например, [[Hibernate]]) выдаст ошибку: _"No identifier specified for entity..."_

---

#### ⚙️ **Дополнительно:**

Часто используется вместе с:

- [[@GeneratedValue]] — для автоматической генерации ID
    
- [[@Column]] — для настройки параметров столбца
    

---

#### 📚 **Связанные термины:**

- [[Entity]]
    
- [[@GeneratedValue]]
    
- [[JPA]]
    
- [[Hibernate]]
    
- [[ORM]]
    

---

#java #jpa #hibernate #id #entity #orm