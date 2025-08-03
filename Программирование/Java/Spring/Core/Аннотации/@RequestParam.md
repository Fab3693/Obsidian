### 🧾 **@RequestParam**

**Простыми словами:** `@RequestParam` используется, чтобы **получить параметры из строки запроса (query string)**, например: `?name=John&age=25`.

---

### ⚙️ **Когда использовать**

- Когда параметр передаётся **в URL после знака `?`**
    
- Для обработки простых запросов: фильтрация, сортировка, пагинация и т.п.
    
- Если нужно получать параметры как строки, числа, списки и т.д.
    

---

### 📌 **Пример с одним параметром**

```java
[[ @GetMapping("/hello") ]]
public String sayHello([[ @RequestParam ]] String name) {
    return "Hello, " + name;
}
```

📍 Запрос `/hello?name=Alice` вернёт `Hello, Alice`.

---

### 📌 **С параметром по умолчанию**

```java
[[ @GetMapping("/page") ]]
public String getPage([[ @RequestParam(defaultValue = "1") ]] int page) {
    return "Page: " + page;
}
```

📍 Если параметр `page` не передан, будет использовано значение `1`.

---

### 📌 **Сделать параметр необязательным**

```java
[[ @RequestParam(required = false) ]] String filter
```

---

### 🧠 **Особенности**

- Можно указывать `required`, `defaultValue`, `name`
    
- Работает только с параметрами **query string**, а не с телом запроса
    
- Для тел запросов (`POST`, `PUT`) с JSON — см. [[@RequestBody]]
    

---

### 🔗 **Связанные термины**

- [[@RequestBody]]
    
- [[@PathVariable]]
    
- [[@Controller]]
    
- [[Spring MVC]]
    
- [[@RestController]]
    

---

#spring #mvc #request #queryparam #rest