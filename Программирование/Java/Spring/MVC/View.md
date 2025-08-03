### 🧾 **View**

**Простыми словами:** `View` — это **представление или шаблон**, который отвечает за отображение данных пользователю в [[Spring MVC]]. Обычно это HTML-страница, созданная с помощью шаблонизатора (например, Thymeleaf, JSP).

---

### ⚙️ **Что делает View**

- Получает данные из [[Model]] (переданные контроллером)
    
- Формирует конечный HTML (или другой формат) для отправки клиенту
    
- Отвечает за визуальное представление информации
    

---

### 📌 **Пример**

Контроллер:

```java
[[ @Controller ]]
public class UserController {
    
    [[ @GetMapping("/hello") ]]
    public String hello(Model model) {
        model.addAttribute("name", "Alice");
        return "greeting"; // имя шаблона
    }
}
```

Шаблон `greeting.html` (Thymeleaf):

```html
<!DOCTYPE html>
<html>
<body>
    <p>Hello, <span th:text="${name}">User</span>!</p>
</body>
</html>
```

---

### 🧠 **Особенности**

- Может быть реализован с помощью разных шаблонизаторов: [[Thymeleaf]], [[JSP]], [[FreeMarker]], и др.
    
- [[ViewResolver]] в Spring отвечает за выбор конкретного шаблона по имени
    
- Используется только в традиционных MVC-приложениях, а не в REST API
    

---

### 🔗 **Связанные термины**

- [[Model]]
    
- [[@Controller]]
    
- [[ViewResolver]]
    
- [[Spring MVC]]
    
- [[Thymeleaf]], [[JSP]]
    

---

#spring #mvc #view #template #html