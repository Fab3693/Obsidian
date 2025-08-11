### 🧾 **@PathVariable**

**Простыми словами:** `@PathVariable` — это аннотация в [[Spring MVC]], которая извлекает **значения переменных прямо из пути URL**.

---

### ⚙️ **Когда использовать**

- Когда часть URL содержит идентификатор или имя, которое нужно передать в метод
    
- Для REST API, где путь описывает ресурс: `/users/5`, `/orders/123`
    
- Для более читаемых и "чистых" адресов без query string
    

---

### 📌 **Пример использования**

```java
[[ @RestController ]]
@RequestMapping("/users")
public class UserController {

    @GetMapping("/{id}")
    public String getUser(@PathVariable Long id) {
        return "Пользователь с id = " + id;
    }
}
```

Запрос:

```
GET /users/5
```

Ответ:

```
Пользователь с id = 5
```

---

### 🧠 **Особенности**

- Имена переменной в `@PathVariable` и в URL должны совпадать:
    
    ```java
    @GetMapping("/items/{itemId}")
    public String getItem(@PathVariable("itemId") Long id) { ... }
    ```
    
- Можно указывать другой параметр в аннотации, если имя переменной в методе отличается
    
- Автоматически конвертирует строку из URL в нужный тип (Long, Integer и т.д.)
    

---

### 🔗 **Связанные термины**

- [[@RequestParam]]
    
- [[HTTP - запрос]]
    
- [[Spring MVC]]
    
- [[REST API]]
    

---

#java #spring #mvc #controller #pathvariable #restapi #http