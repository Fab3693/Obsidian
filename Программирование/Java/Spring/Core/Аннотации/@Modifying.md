````markdown
### 🔧 **@Modifying**

**Простыми словами:** `@Modifying` используется вместе с [[@Query]], когда ты **выполняешь запрос, изменяющий данные** — например, `UPDATE`, `DELETE`, `INSERT`.

Этот метод должен быть помечен как [[@Transactional]], иначе изменения не сохранятся.

---

#### 🛠 Пример с UPDATE

```java
@Modifying
@Query("UPDATE User u SET u.active = false WHERE u.lastLogin < :date")
int deactivateOldUsers(@Param("date") LocalDate date);
````

📌 Возвращает количество изменённых строк. Использует JPQL — работает с [[Entity]], а не с таблицами напрямую.

---

#### 🗃 Пример с native SQL

```java
@Modifying
@Query(value = "DELETE FROM users WHERE active = false", nativeQuery = true)
int deleteInactiveUsers();
```

---

#### 🔗 Смотри также:

- [[@Query]]
    
- [[@Transactional]]
    
- [[@Repository]]
    
- [[JPA]]