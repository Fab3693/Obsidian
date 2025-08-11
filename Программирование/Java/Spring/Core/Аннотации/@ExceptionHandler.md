### 🧾 **@ExceptionHandler**

**Простыми словами:** `@ExceptionHandler` — это аннотация в [[Spring MVC]], которая позволяет **обрабатывать ошибки и исключения**, возникшие в контроллерах, и возвращать удобный ответ клиенту.

---

### ⚙️ **Когда использовать**

- Для перехвата ошибок, например, `NullPointerException`, `IllegalArgumentException` и своих кастомных исключений
    
- Чтобы вернуть понятное сообщение об ошибке или страницу ошибки
    
- Для централизованной обработки исключений в контроллере
    

---

### 📌 **Пример использования**

```java
[[ @RestController ]]
public class UserController {

    @GetMapping("/user/{id}")
    public User getUser(@PathVariable Long id) {
        if (id <= 0) {
            throw new IllegalArgumentException("Id должен быть положительным");
        }
        return userService.findById(id);
    }

    [[ @ExceptionHandler(IllegalArgumentException.class) ]]
    public ResponseEntity<String> handleIllegalArgument(IllegalArgumentException ex) {
        return ResponseEntity.badRequest().body("Ошибка: " + ex.getMessage());
    }
}
```

---

### 🧠 **Особенности**

- Можно указать несколько типов исключений
    
- Можно использовать в контроллерах или в отдельном классе с `@ControllerAdvice` для глобальной обработки
    
- Позволяет возвращать разные типы ответов: JSON, HTML, статус HTTP и т.д.
    

---

### 🔗 **Связанные термины**

- [[@ControllerAdvice]]
    
- [[ResponseEntity]]
    
- [[Spring MVC]]
    
- [[Exception]]
    

---

#java #spring #mvc #exceptionhandling #error #controller