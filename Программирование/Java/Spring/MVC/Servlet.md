Вот статья для Obsidian по термину **Servlet**:

---

### 🧾 **Servlet**

**Простыми словами:** `Servlet` — это Java-класс, который **обрабатывает [[HTTP - запрос]] и формирует ответ**. Это **базовый строительный блок веб-приложений в Java**, до появления [[Spring MVC]].

---

### ⚙️ **Когда используется**

- В классических Java EE веб-приложениях
    
- Под капотом [[Spring MVC]] через [[DispatcherServlet]]
    
- Внутри [[Tomcat]] и других сервлет-контейнеров
    

---

### 📦 **Что делает Servlet**

1. Получает [[HTTP - запрос]] (`GET`, `POST` и т.д.)
    
2. Обрабатывает его с помощью Java-кода
    
3. Отправляет обратно [[HTML]], [[JSON]] или другой ответ клиенту
    

---

### 📌 **Пример простого сервлета**

```java
@WebServlet("/hello")
public class HelloServlet extends HttpServlet {
    
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp)
            throws IOException {
        resp.getWriter().write("Hello, world!");
    }
}
```

📍 Такой сервлет отвечает на запросы `GET /hello`.

---

### 🧠 **Особенности**

- Наследуется от `HttpServlet`
    
- Переопределяет методы `doGet()`, `doPost()` и другие
    
- Живёт внутри сервлет-контейнера (например, [[Tomcat]])
    
- Может настраиваться в `web.xml` или через `@WebServlet`
    
- В [[Spring]] работа сервлетов инкапсулируется в [[DispatcherServlet]]
    

---

### 🔗 **Связанные термины**

- [[HTTP - запрос]]
    
- [[Tomcat]]
    
- [[DispatcherServlet]]
    
- [[Spring MVC]]
    
- [[Spring Boot]]
    

---

#java #servlet #http #web #tomcat #spring #webapp