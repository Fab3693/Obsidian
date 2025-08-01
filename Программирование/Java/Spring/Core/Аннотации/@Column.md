### 📌 **@Column**

**Простыми словами:** `@Column` указывает, **с каким столбцом таблицы БД связано поле** в классе [[Entity]]. Без этой аннотации JPA тоже работает, но она нужна для точной настройки: имя столбца, ограничений, длины и т.д.

---

#### ⚙️ **Что можно указать в `@Column`:**

|Параметр|Что делает|
|---|---|
|`name`|Имя столбца в БД|
|`nullable`|Разрешено ли `NULL` (по умолчанию — `true`)|
|`unique`|Должно ли значение быть уникальным|
|`length`|Максимальная длина (только для строк)|
|`updatable`|Можно ли обновлять значение|
|`insertable`|Можно ли вставлять при `INSERT`|

---

#### 🧱 **Пример:**

```java
@Entity
public class User {

    @Id
    private Long id;

    @Column(name = "user_name", nullable = false, unique = true, length = 50)
    private String username;

    @Column(nullable = false)
    private String password;
}
```

📌 Здесь:

- `user_name` — имя столбца в БД
    
- `nullable = false` — поле обязательно
    
- `unique = true` — значение должно быть уникальным
    
- `length = 50` — строка максимум 50 символов
    

---

#### 💡 **Когда можно не писать `@Column`?**

Если:

- имя поля совпадает с именем столбца,
    
- не нужны доп. настройки (например, `nullable`, `unique`),  
    тогда `@Column` можно опустить — JPA всё сделает автоматически.
    

---

#### 🔗 **Связанные термины:**

- [[Entity]]
    
- [[@Id]]
    
- [[@GeneratedValue]]
    
- [[JPA]]
    
- [[Hibernate]]
    

---

#java #jpa #hibernate #column #entity #orm