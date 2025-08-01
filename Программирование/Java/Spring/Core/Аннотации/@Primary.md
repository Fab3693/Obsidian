### 📄 **@Primary**

**Простыми словами:** `@Primary` указывает Spring, что **этот бин следует внедрять по умолчанию**, если есть несколько кандидатов одного типа и не указан [[@Qualifier]].

---

#### ⚙️ **Для чего нужна:**

- 🔄 Разрешение конфликта, когда есть несколько одинаковых бинов.
    
- 🧭 Используется как "основной путь", если другой явно не указан.
    

---

#### 🔤 **Пример:**

```java
@Component
@Primary
public class FileStorageService implements StorageService {}

@Component
public class DatabaseStorageService implements StorageService {}

@Service
public class UploadService {

    private final StorageService storageService;

    @Autowired
    public UploadService(StorageService storageService) {
        this.storageService = storageService;
    }
}
```

📍 В этом примере внедрится `FileStorageService`, потому что он помечен `@Primary`.

---

#### ✅ **Советы:**

- Удобно использовать для стандартного поведения.
    
- Можно комбинировать с `@Qualifier`, чтобы выбирать нестандартный бин вручную.
    
- Есть аналог в XML-конфигурации: `<bean primary="true" />`.
    

---

#### 🔗 **Связанные термины**

- [[@Autowired]]
    
- [[@Qualifier]]
    
- [[@Component]]
    
- [[@Service]]
    

---

#spring #primary #di #bean #autowiring