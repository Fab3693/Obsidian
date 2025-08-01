### 📄 **@Service**

**Простыми словами:** `@Service` — это аннотация, которая помечает класс как **компонент бизнес-логики**. Такой класс отвечает за координацию операций, проверку правил и работу с данными через репозитории.

---

#### ⚙️ **Для чего нужна:**

- Помечает бин для автоматического сканирования Spring ([[@Component]]-специализация).
    
- Помогает структурировать проект: отделяет слой сервисов от контроллеров и репозиториев.
    
- Может участвовать в транзакционном управлении ([[@Transactional]] на методах).
    

---

#### 🔤 **Пример:**

```java
@Service
public class UserService {

    private final UserRepository repo;

    public UserService(UserRepository repo) {
        this.repo = repo;
    }

    @Transactional
    public UserDTO getUserById(Long id) {
        User user = repo.findById(id)
                        .orElseThrow(() -> new NotFoundException("User not found"));
        return new UserDTO(user);
    }
}
```

---

#### 🔗 **Связанные термины:**

- [[@Repository]]
    
- [[@Controller]]
    
- [[DTO]]
    
- [[Entity]]
    

---

#spring #service #business #transaction