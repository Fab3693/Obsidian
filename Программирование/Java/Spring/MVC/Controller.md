### 🧾 **@Controller**

**Простыми словами:** `@Controller` — это аннотация в [[Spring MVC]], которая **обозначает класс как контроллер**, отвечающий за обработку HTTP-запросов и подготовку данных для отображения в веб-приложении.

---

### ⚙️ **Когда использовать**

- Для создания веб-страниц (HTML), которые возвращают представления (View)
    
- Когда нужно связать запросы с методами, обрабатывать данные и выбирать шаблоны
    
- Для классических MVC-приложений
    

---

### 📌 **Пример использования**

```java
[[ @Controller ]]
public class UserController {
    
    [[ @GetMapping("/hello") ]]
    public String hello(Model model) {
        model.addAttribute("name", "Alice");
        return "greeting"; // имя HTML-шаблона для рендеринга
    }
}
```

📍 Возвращается имя шаблона, а данные передаются через `Model`.

---

### 🧠 **Особенности**

- В отличие от [[@RestController]], возвращает имена представлений (страниц), а не данные напрямую
    
- Используется вместе с View Resolver (например, Thymeleaf, JSP)
    
- Можно комбинировать с [[@RequestMapping]], [[@GetMapping]], [[@PostMapping]] и другими для маршрутизации
    

---

### 🔗 **Связанные термины**

- [[@RestController]]
    
- [[Model]]
    
- [[View]]
    
- [[Spring MVC]]
    
- [[@RequestMapping]]
    

---

#spring #mvc #controller #web #mvccontroller