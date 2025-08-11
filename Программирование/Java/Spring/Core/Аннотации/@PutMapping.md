### 🧾 **@PutMapping**

**Простыми словами:** `@PutMapping` — это аннотация в [[Spring MVC]], которая **обрабатывает HTTP PUT-запросы**. Обычно используется для **полного обновления** существующего ресурса на сервере.

---

### ⚙️ **Когда использовать**

- Когда нужно **заменить** весь объект новыми данными
    
- При реализации REST API метода **update**
    
- Когда клиент отправляет новые данные для уже существующего ресурса
    

---

### 📌 **Пример использования**

```java
[[ @RestController ]]
@RequestMapping("/users")
public class UserController {

    @PutMapping("/{id}")
    public UserDTO updateUser(@PathVariable Long id, @RequestBody UserDTO user) {
        // Логика обновления пользователя с указанным id
        return user;
    }
}
```

📍 Этот метод сработает, если отправить PUT-запрос на `/users/1` с JSON-данными пользователя.

---

### 🧠 **Особенности**

- Эквивалент `@RequestMapping(method = RequestMethod.PUT)`
    
- Работает только с **PUT**-запросами
    
- Отличие от [[@PatchMapping]]: PUT заменяет весь объект, PATCH — только часть
    
- Часто используется вместе с [[@PathVariable]] и [[@RequestBody]]
    

---

### 🔗 **Связанные термины**

- [[@RequestMapping]]
    
- [[@PathVariable]]
    
- [[@RequestBody]]
    
- [[HTTP - запрос]]
    
- [[Spring MVC]]
    
- [[DTO]]
    

---

#java #spring #mvc #controller #putmapping #restapi #http