### 🧾 **Thymeleaf**

**Простыми словами:** `Thymeleaf` — это **шаблонизатор (template engine)** для Java-приложений, который позволяет **встраивать переменные и логику прямо в HTML**. Используется вместе со [[Spring MVC]] для отображения данных пользователю.

---

### ⚙️ **Когда использовать**

- При создании HTML-страниц на стороне сервера
    
- Для динамической подстановки данных (из [[Model]])
    
- Когда нужен красивый и понятный HTML-код даже без запуска сервера (режим "читаемый как HTML")
    

---

### 📌 **Пример шаблона с переменной**

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<body>
    <p>Hello, <span th:text="${name}">User</span>!</p>
</body>
</html>
```

📍 `${name}` — это переменная, переданная из контроллера:

```java
[[@Controller]]
public class HelloController {

    [[ @GetMapping("/hello") ]]
    public String hello(Model model) {
        model.addAttribute("name", "Alice");
        return "hello"; // отобразит hello.html
    }
}
```

---

### 🧠 **Особенности**

- Работает как с HTML, так и с другими форматами (XML, текст и т.д.)
    
- Поддерживает условия (`th:if`, `th:unless`), циклы (`th:each`), ссылки (`th:href`), формы и т.д.
    
- Полностью интегрирован в [[Spring Boot]] и [[Spring MVC]]
    
- Шаблоны читаемы даже вне контекста Spring — можно открыть как обычный HTML-файл
    

---

### 🔗 **Связанные термины**

- [[Spring MVC]]
    
- [[Model]]
    
- [[View]]
    
- [[JSP]]
    
- [[Controller]]
    

---

#spring #thymeleaf #mvc #view #template #html