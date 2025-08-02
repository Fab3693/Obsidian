### 🧾 **@Modifying**

**Простыми словами:** `@Modifying` используется вместе с `@Query` для **обозначения методов, которые изменяют данные** (например, выполняют `INSERT`, `UPDATE`, `DELETE`) в базе, а не просто читают их.

---

### ⚙️ **Когда использовать**

- При написании кастомных запросов, которые **обновляют или удаляют записи**
    
- Если метод должен влиять на данные, а не возвращать их
    
- В комбинации с `@Query` для явного указания, что запрос изменяющий
    

---

### 📌 **Пример: обновление записи**

```java
@Modifying
@Query("UPDATE User u SET u.status = :status WHERE u.id = :id")
int updateUserStatus(@Param("id") Long id, @Param("status") String status);
```

📍 Возвращает количество изменённых строк.

---

### 📌 **Пример: удаление записи**

```java
@Modifying
@Query("DELETE FROM User u WHERE u.expired = true")
int deleteExpiredUsers();
```

---

### 🧠 **Особенности**

- Работает только в интерфейсах с [[@Repository]]
    
- Метод должен быть вызван в контексте транзакции ([[Transactional]])
    
- Обязательно сочетать с [[@Transactional]] при изменении данных
    
- Возвращаемый тип обычно `int` — число изменённых строк
    
- Без `@Modifying` `@Query` по умолчанию ожидает запрос на чтение
    

---

### 🔗 **Связанные термины**

- [[@Query]]
    
- [[@Transactional]]
    
- [[@Repository]]
    
- [[Entity]]
    

---

#spring #jpa #modifying #update #delete