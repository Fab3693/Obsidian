### 🧾 **application.properties**

**Простыми словами:** `application.properties` — это **основной файл конфигурации в [[Spring Boot]]**, в котором задаются настройки приложения: порты, доступ к базе данных, логирование и многое другое.

---

### ⚙️ **Когда использовать**

- Чтобы задать настройки подключения к БД
    
- Чтобы указать порт сервера, пути, параметры логики приложения
    
- Для настройки поведения модулей: [[JPA]], [[Thymeleaf]], безопасности, REST и т.д.
    

---

### 📌 **Примеры настроек**

```properties
# Настройка порта сервера
server.port=8081

# Подключение к базе данных
spring.datasource.url=jdbc:postgresql://localhost:5432/mydb
spring.datasource.username=postgres
spring.datasource.password=secret

# Настройка JPA
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# Путь к шаблонам (если используешь Thymeleaf)
spring.thymeleaf.prefix=classpath:/templates/
```

---

### 🧠 **Особенности**

- Альтернатива: `application.yml` — YAML-версия того же самого
    
- Можно использовать несколько профилей (например, `application-dev.properties`, `application-prod.properties`)
    
- Позволяет легко изменять поведение приложения без перекомпиляции кода
    
- Spring автоматически загружает этот файл при запуске
    

---

### 🔗 **Связанные термины**

- [[Spring Boot]]
    
- [[JPA]]
    
- [[Thymeleaf]]
    
- [[Spring MVC]]
    
- [[REST API]]
    
- [[application.yml]]
    

---

#spring #boot #properties #configuration #settings