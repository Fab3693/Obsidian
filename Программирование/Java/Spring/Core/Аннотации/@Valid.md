### 🧾 **@Valid**

**Простыми словами:** `@Valid` — это аннотация из **Java Bean Validation**, которая **проверяет корректность объекта или его полей** перед использованием, например, в контроллере или сервисе.

---

### ⚙️ **Когда использовать**

- Проверка входящих данных в [[Spring MVC]] контроллерах
    
- Валидация полей [[DTO]] или [[Entity]]
    
- Совместно с аннотациями вроде `@NotNull`, `@Size`, `@Email` и т.д.
    

---

### 📌 **Пример использования**

```java
import jakarta.validation.Valid;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/users")
public class UserController {

    private final UserService service;

    public UserController(UserService service) {
        this.service = service;
    }

    @PostMapping
    public UserDTO createUser(@RequestBody @Valid UserDTO userDTO) {
        return service.saveUser(userDTO);
    }
}
```

```java
import jakarta.validation.constraints.*;

public class UserDTO {
    @NotBlank
    private String username;

    @Email
    private String email;
}
```

📍 Здесь Spring автоматически проверит, что `username` не пустой, а `email` — корректный.

---

### 🧠 **Особенности**

- Работает только с объектами, у которых указаны аннотации валидации
    
- В [[Spring MVC]] обычно применяется вместе с `@RequestBody` или `@ModelAttribute`
    
- При нарушении правил валидации выбрасывает исключение `MethodArgumentNotValidException`
    

---

### 🔗 **Связанные термины**

- [[DTO]]
    
- [[Spring MVC]]
    
- [[@NotNull]]
    
- [[@NotBlank]]
    
- [[@Email]]
    

---

#java #spring #validation #dto #mvc #valid