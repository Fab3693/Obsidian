### 🌱 **Spring Framework**

**Простыми словами:** Spring Framework — это **большой набор инструментов для Java-разработки**, который помогает писать гибкие, модульные и легко поддерживаемые приложения.

---

### 🧩 **Что делает Spring Framework**

- 🔄 Управляет зависимостями через [[IoC]] и [[DI]]
    
- 🖥 Упрощает работу с вебом через [[Spring MVC]]
    
- 🗄 Облегчает доступ к БД через [[Spring Data]] и [[JPA]]
    
- 🛡 Обеспечивает безопасность через [[Spring Security]]
    
- ⚙️ Поддерживает тестирование и интеграцию
    

---

### ⚙️ **Пример кода с Spring**

```java
[[ @Service ]]
public class UserService {

    private final UserRepository repo;

    public UserService(UserRepository repo) {
        this.repo = repo;
    }

    public List<User> getAllUsers() {
        return repo.findAll();
    }
}
```

---

### 🧠 **Ключевые модули Spring**

- **Core** — [[IoC]] контейнер, [[DI]]
    
- **Spring MVC** — веб-приложения
    
- **Spring Data** — работа с БД
    
- **Spring Security** — безопасность
    
- **Spring Boot** — упрощённый запуск приложений
    

---

### 🔗 **Связанные термины**

- [[Spring Boot]]
    
- [[Spring MVC]]
    
- [[Spring Security]]
    
- [[IoC]]
    
- [[DI]]
    
- [[JPA]]
    

---

#java #spring #framework #ioc #di #mvc #security #data