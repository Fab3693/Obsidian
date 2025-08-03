### 🧾 **DispatcherServlet**

**Простыми словами:** `DispatcherServlet` — это **центральный контроллер в [[Spring MVC]]**, который принимает все HTTP-запросы, обрабатывает их и отправляет к нужному обработчику (контроллеру).

Он как "диспетчер", который направляет трафик внутри Spring-приложения.

---

### 🧩 **Что делает DispatcherServlet:**

- 🛬 Получает входящий HTTP-запрос
    
- 🔄 Передаёт его подходящему контроллеру (например, с [[@Controller]] или [[@RestController]])
    
- 🧠 Обрабатывает данные, вызывает бизнес-логику, формирует ответ
    
- 📤 Возвращает HTTP-ответ клиенту (чаще всего — JSON, HTML, текст и т.п.)
    

---

### ⚙️ **Как работает (упрощённо):**

```text
Браузер → DispatcherServlet → Контроллер → Сервис → Репозиторий → База данных
                                     ↓
                          Возврат ответа (View или JSON)
```

---

### 📌 **Пример маршрутизации**

```java
[[ @RestController ]]
public class UserController {
    
    [[ @GetMapping("/users") ]]
    public List<User> getAllUsers() {
        return userService.findAll();
    }
}
```

📍 Здесь `DispatcherServlet` обрабатывает запрос `/users` и вызывает `getAllUsers()`.

---

### 🧠 **Особенности**

- Автоматически настраивается при использовании [[Spring Boot]]
    
- Конфигурация по умолчанию направляет все запросы на `/` через `DispatcherServlet`
    
- Можно переопределять поведение через `WebMvcConfigurer`
    

---

### 🔗 **Связанные термины**

- [[Spring MVC]]
    
- [[@Controller]]
    
- [[@RestController]]
    
- [[@RequestMapping]]
    
- [[ModelAndView]]
    
- [[ViewResolver]]
    

---

#spring #mvc #dispatcher #controller #web