### 📄 **@Qualifier**

**Простыми словами:** `@Qualifier` используется вместе с [[@Autowired]], чтобы указать, **какой конкретно бин внедрить**, если есть несколько одинакового типа.

---

#### ⚙️ **Для чего нужна:**

- 📌 Уточнить, какой именно бин использовать, если есть 2+ одинаковых.
    
- ⚠️ Без `@Qualifier` Spring выбросит `NoUniqueBeanDefinitionException`.
    

---

#### 🔤 **Пример:**

```java
@Component("fileStorage")
public class FileStorageService implements StorageService {}

@Component("dbStorage")
public class DatabaseStorageService implements StorageService {}

@Service
public class UploadService {
    
    private final StorageService storageService;

    @Autowired
    public UploadService(@Qualifier("fileStorage") StorageService storageService) {
        this.storageService = storageService;
    }
}
```

📍 Без `@Qualifier("fileStorage")` Spring не поймёт, какой `StorageService` внедрять.

---

#### ✅ **Советы:**

- Используй `@Qualifier` в **конструкторе**, **сеттере** или **поле**.
    
- Название в `@Qualifier("...")` должно совпадать с именем бина.
    
- Вместо строк можно использовать **кастомные аннотации** (продвинутый уровень).
    

---

#### 🔗 **Связанные термины**

- [[@Autowired]]
    
- [[@Component]]
    
- [[@Service]]
    
- [[@Primary]]
    

---

#spring #qualifier #di #bean #autowiring