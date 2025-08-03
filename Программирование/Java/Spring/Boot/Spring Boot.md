### 🧾 **Spring Boot**

**Простыми словами:** `Spring Boot` — это расширение Spring Framework, которое позволяет **быстро создавать готовые к запуску приложения с минимальной настройкой**.

Он убирает "лишнюю возню" с конфигурацией и дает "всё из коробки".

---

### ⚙️ **Что делает Spring Boot**

- 🚀 Автоматически настраивает [[Spring MVC]], [[JPA]], [[Thymeleaf]] и другие модули
    
- 📦 Включает встроенный веб-сервер (Tomcat, Jetty) — можно запускать как обычный `main`-класс
    
- 📁 Упрощает структуру проекта: один файл `application.properties` может заменить десятки XML-конфигураций
    
- 🔌 Легко подключает зависимости через `starter`-библиотеки (например, `spring-boot-starter-web`, `starter-data-jpa`)
    

---

### 📌 **Пример минимального приложения**

```java
[[ @SpringBootApplication ]]
public class App {
    public static void main(String[] args) {
        SpringApplication.run(App.class, args);
    }
}
```

📍 Этот код запускает всё приложение, включая веб-сервер.

---

### 🧠 **Особенности**

- Позволяет запускать приложение одной командой:
    
    ```
    mvn spring-boot:run
    ```
    
- Предоставляет встроенный мониторинг, конфигурацию, работу с БД и REST API
    
- Хорошо сочетается с микросервисной архитектурой
    

---

### 🔗 **Связанные термины**

- [[Spring MVC]]
    
- [[JPA]]
    
- [[Thymeleaf]]
    
- [[@SpringBootApplication]]
    
- [[application.properties]]
    
- [[REST API]]
    

---

#spring #boot #java #web #starter #autoconfiguration