### 🧾 **Tomcat**

**Простыми словами:** **Tomcat** — это **веб-сервер и сервлет-контейнер**, который **запускает Java веб-приложения**. Он умеет обрабатывать [[HTTP - запрос]]ы, запускать [[Servlet]] и возвращать ответы клиенту.

---

### ⚙️ **Когда используется**

- При запуске приложений на [[Spring MVC]] и [[Spring Boot]]
    
- Для обработки REST API, HTML-страниц и динамического контента
    
- При деплое `.war`-файлов в продакшн или запуске `.jar`-приложений
    

---

### 🧱 **Что делает Tomcat**

- 🔄 Получает HTTP-запросы и передаёт их в [[DispatcherServlet]]
    
- 🛠️ Управляет жизненным циклом [[Servlet]]-ов и фильтров
    
- 📦 Запускает веб-приложение из `.war` или встроен в `.jar`
    

---

### 📌 **Spring Boot и Tomcat**

В Spring Boot Tomcat **встроен** по умолчанию:

```plaintext
java -jar myapp.jar
```

📍 При запуске `Spring Boot` сам поднимает встроенный Tomcat на порту 8080 (или другом).

---

### 🧠 **Особенности**

- Работает с сервлетами (JSR 340), включая [[DispatcherServlet]]
    
- Поддерживает HTTP, HTTPS, фильтры, сессии
    
- Настраивается через `server.port`, `server.servlet.*` в `application.properties`
    
- Можно заменить Tomcat на Jetty или Undertow (в Spring Boot)
    

---

### 🔗 **Связанные термины**

- [[Servlet]]
    
- [[DispatcherServlet]]
    
- [[Spring Boot]]
    
- [[HTTP - запрос]]
    
- [[Spring MVC]]
    
- [[application.properties]]
    

---

#java #tomcat #spring #webserver #servlet #springboot #mvc