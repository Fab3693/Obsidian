### ⚙️ **CRUD: Create, Read, Update, Delete**

**CRUD** — это четыре базовые операции над данными, каждая из которых соответствует определённому HTTP-методу:

|Операция|HTTP|Назначение|Пример URL|Аннотация Spring|
|---|---|---|---|---|
|**C**reate|`POST`|Создать ресурс|`/api/users`|`@PostMapping`|
|**R**ead|`GET`|Получить ресурс|`/api/users/{id}`|`@GetMapping`|
|**U**pdate|`PUT`|Обновить ресурс|`/api/users/{id}`|`@PutMapping`|
|**D**elete|`DELETE`|Удалить ресурс|`/api/users/{id}`|`@DeleteMapping`|

---

### 📚 **Примеры в Spring**

```java
@RestController
@RequestMapping("/api/users")
public class UserController {

    @PostMapping
    public UserDTO create(@RequestBody UserRequestDTO dto) {
        return userService.create(dto);
    }

    @GetMapping("/{id}")
    public UserDTO read(@PathVariable Long id) {
        return userService.get(id);
    }

    @PutMapping("/{id}")
    public UserDTO update(@PathVariable Long id, @RequestBody UserRequestDTO dto) {
        return userService.update(id, dto);
    }

    @DeleteMapping("/{id}")
    public void delete(@PathVariable Long id) {
        userService.delete(id);
    }
}
```

---

### 🧠 **Особенности**

- `@PostMapping` — создание (без `id`)
    
- `@GetMapping` — получение по `id` (или списка)
    
- `@PutMapping` — полное обновление ресурса
    
- `@DeleteMapping` — удаление по `id`
    

---

### 🔗 **Связанные термины**

- [[REST API]]
    
- [[Spring MVC]]
    
- [[@PostMapping]]
    
- [[@GetMapping]]
    
- [[@PutMapping]]
    
- [[@DeleteMapping]]
    
- [[DTO]]
    
- [[JSON]]
    

---

#crud #restapi #spring #controller #http