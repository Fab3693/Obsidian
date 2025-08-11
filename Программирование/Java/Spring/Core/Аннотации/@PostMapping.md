### 🧾 **@PostMapping**

**Простыми словами:** `@PostMapping` — это аннотация в [[Spring MVC]], которая **указывает, что метод контроллера обрабатывает HTTP POST-запросы** на указанный URL.

---

### ⚙️ **Когда использовать**

- При создании новых ресурсов (например, создание пользователя, заказa)
    
- Когда данные отправляются в теле запроса (например, форма, [[JSON]])
    
- Для REST API, где POST отвечает за создание
    

---

### 📌 **Пример использования**

```java
[[ @RestController ]]
public class UserController {
    
    [[ @PostMapping("/users") ]]
    public User createUser(@RequestBody User user) {
        return userService.save(user);
    }
}
```

📍 Метод принимает [[JSON]] с данными пользователя и сохраняет его.

---

### 🧠 **Особенности**

- Является сокращением для `@RequestMapping(method = RequestMethod.POST)`
    
- Может принимать параметры из тела запроса (`@RequestBody`), из формы (`@ModelAttribute`), или параметры URL
    
- Часто используется вместе с `@RequestBody` для обработки JSON
    

---

### 🔗 **Связанные термины**

- [[@GetMapping]]
    
- [[@RequestMapping]]
    
- [[@RequestBody]]
    
- [[REST API]]
    
- [[Spring MVC]]
    

---

#spring #mvc #post #rest #controller