### 🛡️ **SQL Injection**

**Простыми словами:** SQL Injection — это **опасная уязвимость**, когда злоумышленник может вставить вредоносный SQL-код в запрос к базе данных через ввод пользователя.

---

### 🧩 **Что происходит при SQL Injection:**

- Злоумышленник вводит специальный текст в поля формы или URL
    
- Этот текст становится частью SQL-запроса
    
- В результате можно получить доступ к данным, изменить их или удалить
    

---

### ⚙️ **Пример уязвимого кода:**

```java
String sql = "SELECT * FROM users WHERE username = '" + userInput + "'";
Statement stmt = connection.createStatement();
ResultSet rs = stmt.executeQuery(sql);
```

Если `userInput` — это

```sql
' OR '1'='1
```

то запрос станет

```sql
SELECT * FROM users WHERE username = '' OR '1'='1'
```

и вернёт все записи.

---

### 🧠 **Как защититься:**

- Использовать [[PreparedStatement]] с параметрами
    
- Валидировать и фильтровать пользовательский ввод
    
- Использовать ORM (например, [[JPA]]) и фреймворки с безопасными API
    

---

### 🔗 **Связанные термины**

- [[PreparedStatement]]
    
- [[SQL]]
    
- [[JDBC]]
    
- [[ORM]]
    

---

#security #sql #injection #java #jdbc #database