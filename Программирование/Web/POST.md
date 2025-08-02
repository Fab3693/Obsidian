### 📤 **POST**

**Простыми словами:** `POST` — это [[HTTP - запрос]], с помощью которого **отправляют данные на сервер**, чтобы **создать** новый объект или выполнить какое-то действие.

---

#### 🧠 **Когда используется**

- Создание нового пользователя: `POST /api/users`
    
- Отправка формы регистрации
    
- Выполнение нестандартных операций (например, запуск обработки)
    

---

#### 📦 **В Spring MVC**

```java
@RestController
@RequestMapping("/api/users")
public class UserController {

    @PostMapping
    public UserDTO createUser(@RequestBody UserRequestDTO dto) {
        return userService.create(dto);
    }
}
```

- `@PostMapping` — аннотация для обработки `POST`-запросов.
    
- `@RequestBody` — связывает JSON-тело запроса с DTO.
    

---

#### 📮 **Пример запроса с curl**

```bash
curl -X POST http://localhost:8080/api/users \
  -H "Content-Type: application/json" \
  -d '{
        "username": "julia",
        "email": "julia@example.com"
      }'
```

---

#### 📥 **Что получит контроллер**

```json
{
  "username": "julia",
  "email": "julia@example.com"
}
```

Он преобразуется в объект [[DTO]] (например, `UserRequestDTO`), с которым уже работает сервис.

---

#### ⚠️ Особенности

- Может изменять состояние сервера
    
- Не идемпотентен (одинаковый запрос может создать **несколько** записей)
    
- Не должен кэшироваться
    
- Не должен использоваться для получения данных
    

---

#### 🔗 **Связанные термины**

- [[REST API]]
    
- [[Spring MVC]]
    
- [[DTO]]
    
- [[@PostMapping]]
    
- [[@RequestBody]]
    
- [[JSON]]
    

---

#http #post #restapi #spring #controller #request