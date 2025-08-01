### 📄 **Spring MVC**

**Простыми словами:** Spring MVC — это часть Spring Framework, которая позволяет **строить веб-приложения** по принципу "контроллер → сервис → ответ". Она обрабатывает HTTP-запросы, вызывает нужный код и возвращает HTML или JSON.

---

#### 🧩 **Основные элементы:**

- 📥 `@Controller` — принимает запросы
    
- 📤 `@ResponseBody` или шаблоны — возвращают ответ
    
- 📦 [[DTO]] — для передачи данных
    
- 🔗 Сервисный слой и [[JPA]]-[[Entity]] — для логики и работы с БД
    

---

#### ⚙️ **Пример:**

```java
@RestController
@RequestMapping("/users")
public class UserController {

    private final UserService service;

    public UserController(UserService service) {
        this.service = service;
    }

    @GetMapping("/{id}")
    public UserDTO getUser(@PathVariable Long id) {
        return service.getUserDtoById(id);
    }
}
```

---

#### 🔄 **Как работает запрос:**

1. Клиент отправляет HTTP-запрос (например, GET /users/1)
    
2. Контроллер получает его и вызывает сервис
    
3. Сервис работает с [[Entity]] через [[JPA]]
    
4. Данные возвращаются в виде [[DTO]] (JSON или HTML)
    

---

#### 🧠 **Когда использовать:**

- Для REST API (JSON)
    
- Для HTML-приложений с [[JSP]] или Thymeleaf
    
- При разработке микросервисов или монолитов
    

---

#### 🔗 **Связанные термины**

- [[DTO]]
    
- [[JPA]]
    
- [[Entity]]
    
- [[JSP]]
    
- [[JSTL]]
    
- [[JSON-POJO]]
    

---

#java #spring #mvc #controller #restapi #web