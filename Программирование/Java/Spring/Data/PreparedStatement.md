### 📄 **PreparedStatement**

**Простыми словами:** `PreparedStatement` — это **специальный объект в JDBC**, который позволяет безопасно выполнять SQL-запросы с параметрами, защищая от [[SQL Injection]].

---

### 🧩 **Что делает PreparedStatement:**

- 🛡️ Подставляет значения в запрос без риска SQL-инъекций
    
- 📦 Позволяет многократно выполнять один и тот же запрос с разными данными
    
- 🚀 Может работать быстрее, так как запрос компилируется один раз
    

---

### ⚙️ **Пример использования:**

```java
String sql = "SELECT * FROM users WHERE username = ?";
PreparedStatement stmt = connection.prepareStatement(sql);
stmt.setString(1, "admin");
ResultSet rs = stmt.executeQuery();
```

---

### 🧠 **Плюсы:**

- 🔒 Безопаснее, чем [[Statement]]
    
- 🔄 Удобная работа с параметрами (`setString`, `setInt`, и т.д.)
    
- ⚡ Оптимизация выполнения повторяющихся запросов
    

---

### 🔗 **Связанные термины**

- [[SQL]]
    
- [[Statement]]
    
- [[SQL Injection]]
    
- [[ResultSet]]
    

---

#java #jdbc #database #sql #preparedstatement