### 🧾 **@RequestMapping**

**Простыми словами:** `@RequestMapping` — универсальная аннотация в [[Spring MVC]], которая **указывает, какой HTTP-запрос (GET, POST, PUT, DELETE и др.) и на какой URL должен обрабатывать метод или класс контроллера**.

---

### ⚙️ **Когда использовать**

- Чтобы задать путь (URL) для обработки запросов
    
- Чтобы указать HTTP-метод (GET, POST, PUT, DELETE и др.) или разрешить несколько методов
    
- Для настройки заголовков, параметров запроса и форматов данных
    

---

### 📌 **Пример: базовое использование**

```java
[[ @Controller ]]
[[ @RequestMapping("/users") ]]
public class UserController {

    [[ @RequestMapping(method = RequestMethod.GET) ]]
    public String getUsers() {
        return "usersList";
    }

    [[ @RequestMapping(value = "/add", method = RequestMethod.POST) ]]
    public String addUser() {
        // логика добавления
        return "redirect:/users";
    }
}
```

---

### 📌 **Пример с указанием нескольких методов**

```java
[[ @RequestMapping(value = "/items", method = {RequestMethod.GET, RequestMethod.POST}) ]]
public String handleItems() {
    // обработка GET и POST запросов
    return "items";
}
```

---

### 🧠 **Особенности**

- Можно применять как на уровне класса, так и на уровне метода
    
- С появлением специальных аннотаций: [[@GetMapping]], [[@PostMapping]], [[@PutMapping]], [[@DeleteMapping]], часто используется только для общих настроек или на классе
    
- Поддерживает множество параметров: `params`, `headers`, `consumes`, `produces`
    

---

### 🔗 **Связанные термины**

- [[@GetMapping]]
    
- [[@PostMapping]]
    
- [[@PutMapping]]
    
- [[@DeleteMapping]]
    
- [[Spring MVC]]
    
- [[Controller]]
    

---

#spring #mvc #requestmapping #http #controller