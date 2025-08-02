### 🌐 **REST API**

**Простыми словами:** REST API — это способ, как клиент (например, браузер или мобильное приложение) может **общаться с сервером по интернету** через обычные HTTP-запросы: [[GET]], [[POST]], `PUT`, `DELETE` и т.д.

> REST — это архитектурный стиль.  
> API — интерфейс для взаимодействия с программой.

---

#### 🔍 **Как это выглядит**

📤 Клиент отправляет запрос:

```
GET /api/users/5
```

📥 Сервер отвечает JSON-объектом:

```json
{
  "id": 5,
  "username": "alex",
  "email": "alex@mail.com"
}
```

---

#### 🛠 **Основные методы:**

|HTTP|Назначение|Пример|
|---|---|---|
|`GET`|Получить данные|`/users` или `/users/1`|
|`POST`|Создать ресурс|`/users` + тело запроса|
|`PUT`|Обновить ресурс|`/users/1`|
|`DELETE`|Удалить ресурс|`/users/1`|

---

#### 🔄 **Работа в [[Spring MVC]]**

В Spring REST API создаётся через:

```java
@RestController
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}")
    public UserDTO getUser(@PathVariable Long id) {
        return userService.findById(id);
    }

    @PostMapping
    public void createUser(@RequestBody UserDTO userDto) {
        userService.create(userDto);
    }
}
```

- `@RestController` = `@Controller + @ResponseBody`
    
- `@RequestBody` автоматически превращает JSON → [[DTO]]
    
- `@ResponseBody` превращает объект Java → [[JSON]]
    

---

#### 🔗 **Связанные термины:**

- [[Spring MVC]]
    
- [[DTO]]
    
- [[JSON]]
    
- [[@RestController]]
    
- [[@RequestMapping]]
    
- [[@GetMapping]]
    
- [[@PostMapping]]
    

---

#rest #api #spring #web #json #controller