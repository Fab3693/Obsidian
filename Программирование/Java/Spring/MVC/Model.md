### 🧾 **Model**

**Простыми словами:** `Model` — это объект в [[Spring MVC]], который **хранит данные, которые нужно передать из контроллера во View (шаблон HTML)** для отображения пользователю.

---

### ⚙️ **Когда использовать**

- Чтобы передать переменные (данные) из контроллера в шаблон (например, Thymeleaf, JSP)
    
- Для организации данных, которые будут показаны на веб-странице
    
- При построении динамического HTML
    

---

### 📌 **Пример использования**

```java
[[ @Controller ]]
public class UserController {
    
    [[ @GetMapping("/hello") ]]
    public String hello(Model model) {
        model.addAttribute("name", "Alice");
        return "greeting";  // имя шаблона (greeting.html или greeting.jsp)
    }
}
```

📍 В шаблоне можно использовать переменную `name` для отображения.

---

### 🧠 **Особенности**

- `Model` — интерфейс, часто используют вместе с `ModelMap` или `ModelAndView`
    
- Позволяет передавать любое количество данных
    
- Используется только при возвращении представлений (HTML), а не при REST API (где используют [[@ResponseBody]])
    

---

### 🔗 **Связанные термины**

- [[View]]
    
- [[ModelAndView]]
    
- [[@Controller]]
    
- [[Spring MVC]]
    
- [[Thymeleaf]], [[JSP]]
    

---

#spring #mvc #model #view #controller