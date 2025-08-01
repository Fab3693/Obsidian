### 📄 **@Controller**

**Простыми словами:** `@Controller` — это аннотация, которая помечает класс как **веб-контроллер**. Такой класс обрабатывает [[HTTP - запрос]] и возвращает представление ([[HTML]]) или данные ([[JSON]], XML).

---

#### ⚙️ **Для чего нужна:**

- Помечает бин для автоматического сканирования Spring ([[@Component]]-специализация).
    
- Связывает URL-пути с методами контроллера через аннотации `@RequestMapping`, `@GetMapping`, `@PostMapping` и т.д.
    
- Взаимодействует с [[@Service]] для бизнес-логики и отдаёт [[DTO]] или шаблоны представления.
    

---

#### 🔤 **Пример:**

```java
@Controller
@RequestMapping("/users")
public class UserController {

    private final UserService service;

    public UserController(UserService service) {
        this.service = service;
    }

    @GetMapping("/{id}")
    public String getUserPage(@PathVariable Long id, Model model) {
        UserDTO user = service.getUserById(id);
        model.addAttribute("user", user);
        return "user/view"; // имя JSP/Thymeleaf шаблона
    }

    @ResponseBody
    @PostMapping("/api")
    public UserDTO createUser(@RequestBody @Valid UserCreateDTO dto) {
        return service.createUser(dto);
    }
}
```

---

#### 🔗 **Связанные термины:**

- [[@Service]]
    
- [[@Repository]]
    
- [[Spring MVC]]
    
- [[DTO]]
    
- [[JSP]] / [[Thymeleaf]]
    

---

#spring #controller #mvc #web