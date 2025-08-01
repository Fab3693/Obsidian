### 📄 **@Component**

**Простыми словами:** [[@Component]] — это базовая аннотация Spring, которая **помечает класс как управляемый Spring-контейнером бин**. Любой класс с [[@Component]] автоматически обнаруживается при сканировании и становится доступным для инъекций.

---

#### ⚙️ **Для чего нужна:**

- 📦 Регистрирует класс как Spring-бин
    
- 🔍 Позволяет применять к нему [[@Autowired]] и другие аннотации
    
- 🔄 Обеспечивает жизненный цикл бина (scope, init/destroy)
    

---

#### 🔤 **Пример:**

```java
@Component
public class EmailSender {
    
    public void send(String to, String message) {
        // логика отправки письма
    }
}
```

```java
@Service
public class NotificationService {
    
    private final EmailSender emailSender;

    @Autowired
    public NotificationService(EmailSender emailSender) {
        this.emailSender = emailSender;
    }

    public void notifyUser(String userEmail) {
        emailSender.send(userEmail, "Welcome!");
    }
}
```

---

#### 🧠 **Где применяется:**

- Для **универсальных утилитарных** классов (напр., парсеры, сервисы отправки почты)
    
- Вместо специализированных аннотаций [[@Service]], [[@Repository]], [[@Controller]], если нет чёткого слоя
    
- В кастомных **фабриках**, **валидаторах**, **хелперах**
    

---

#### ✅ **Советы:**

- Используй `@Component` для **сервисов общего назначения**, не подходящих под [[@Service]]/[[@Repository]].
    
- Для **конфигурационных** классов лучше [[@Configuration]].
    
- Не забывай про `[[Scope]]`, если нужен не singleton.
    

---

#### 🔗 **Связанные термины**

- [[@Service]]
    
- [[@Repository]]
    
- [[@Controller]]
    
- [[@Configuration]]
    
- [[@Bean]]
    
- [[@Scope]]
    
- [[@Autowired]]
    

---