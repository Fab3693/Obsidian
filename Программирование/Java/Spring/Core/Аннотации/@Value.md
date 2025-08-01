### 📄 **@Value**

**Простыми словами:** `@Value` — это аннотация Spring, которая **подставляет значение из конфигурации** (файлов `application.properties`/`.yml`, системных переменных или других источников) в поле или параметр метода.

---

#### ⚙️ **Для чего нужна:**

- 🎯 Внедрять наружу заданные настройки (URL, порты, параметры) прямо в бины.
    
- 🔄 Позволяет изменять поведение без перекомпиляции: меняешь свойства — меняется бин.
    
- 🔗 Работает вместе с `@PropertySource` и `@ConfigurationProperties`.
    

---

#### 🔤 **Пример использования:**

```properties
# application.properties
app.email.from=support@example.com
app.retry.count=5
```

```java
@Component
public class EmailService {

    @Value("${app.email.from}")
    private String fromAddress;

    private final int retryCount;

    // Можно и в конструкторе
    public EmailService(@Value("${app.retry.count}") int retryCount) {
        this.retryCount = retryCount;
    }

    public void send(String to, String message) {
        // используем fromAddress и retryCount
    }
}
```

---

#### ✅ **Советы:**

- Для сложных групп свойств лучше `[[ConfigurationProperties]]`.
    
- Проверяй наличие свойства: `@Value("${missing:default}")` задаёт значение по умолчанию.
    
- Не используйте `@Value` для больших структур данных — сериализуйте в объекты через `@ConfigurationProperties`.
    

---

#### 🔗 **Связанные термины**

- [[Component]]
    
- [[PropertySource]]
    
- [[ConfigurationProperties]]
    
- [[Value]]
    
- [[Autowired]]
    

---

#spring #configuration #properties #value #di