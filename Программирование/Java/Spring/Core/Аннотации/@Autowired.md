### 📄 **@Autowired**

**Простыми словами:** `@Autowired` — это аннотация Spring, которая **внедряет зависимости** автоматически. Она ищет нужный бин по типу (и опционально по имени) в контексте и подставляет его в поле, сеттер или конструктор.

---

#### ⚙️ **Для чего нужна:**

- 🔗 Связывает один бин с другим без ручного `new`
    
- 🤖 Автоматизирует инъекцию зависимостей в поля, конструкторы и методы
    
- 🧩 Упрощает тестирование и модульность кода
    

---

#### 🔤 **Примеры использования:**

1. **В конструкторе:**
    
    ```java
    @Service
    public class UserService {
        private final UserRepository repo;
    
        @Autowired
        public UserService(UserRepository repo) {
            this.repo = repo;
        }
    }
    ```
    
2. **На поле:**
    
    ```java
    @Component
    public class NotificationService {
        @Autowired
        private EmailSender emailSender;
    }
    ```
    
3. **На сеттере:**
    
    ```java
    @Component
    public class ReportGenerator {
        private DataSource dataSource;
    
        @Autowired
        public void setDataSource(DataSource dataSource) {
            this.dataSource = dataSource;
        }
    }
    ```
    

---

#### ✅ **Советы:**

- Предпочитай **конструкторную инъекцию** для обязательных зависимостей.
    
- Для нескольких реализаций можно использовать `[[Qualifier]]` или `[[Primary]]`.
    
- Начиная с Spring 4.3, если у бина один конструктор — `@Autowired` можно опустить.
    

---

#### 🔗 **Связанные термины**

- [[@Component]]
    
- [[@Service]]
    
- [[@Repository]]
    
- [[@Qualifier]]
    
- [[@Primary]]
    
- [[@Scope]]
    

---

#spring #autowired #di #dependencyinjection #bean