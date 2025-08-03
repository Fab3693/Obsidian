### 🧾 **@GetMapping**

**Простыми словами:** `@GetMapping` — это аннотация из [[Spring MVC]], которая **обрабатывает HTTP GET-запросы**. Она указывает, какой метод вызывать, когда приходит GET-запрос по заданному пути.

---

### ⚙️ **Когда использовать**

- Когда нужно **вернуть данные клиенту**, например: HTML-страницу, JSON, текст и т.д.
    
- При реализации **REST API методов для чтения (Read)**
    
- Для обработки запросов типа `GET /users`, `GET /products/1`
    

---

### 📌 **Простой пример**

```java
[[ @RestController ]]
public class UserController {

    [[ @GetMapping("/hello") ]]
    public String sayHello() {
        return "Hello!";
    }
}
```

📍 Запрос по `/hello` вернёт строку `Hello!`

---

### 📌 **С параметрами запроса**

```java
[[ @GetMapping("/greet") ]]
public String greetUser([[ @RequestParam ]] String name) {
    return "Hi, " + name;
}
```

📍 Запрос `/greet?name=Anna` вернёт `Hi, Anna`

---

### 📌 **С переменной пути**

```java
[[ @GetMapping("/users/{id}") ]]
public User getUserById([[ @PathVariable ]] Long id) {
    return userService.findById(id);
}
```

📍 Обрабатывает запрос вроде `/users/5`

---

### 🧠 **Особенности**

- Альтернатива: `@RequestMapping(method = RequestMethod.GET)`
    
- Поддерживает параметры (`params`, `headers`, `produces`, `consumes`)
    
- Возвращает HTML (через шаблон) или данные (обычно JSON)
    
- Используется только для **GET-запросов**, не обрабатывает `POST`, `PUT`, `DELETE`
    

---

### 🔗 **Связанные термины**

- [[@RequestMapping]]
    
- [[@PostMapping]]
    
- [[@RestController]]
    
- [[@PathVariable]]
    
- [[@RequestParam]]
    
- [[Spring MVC]]
    

---

#spring #mvc #get #rest #controller