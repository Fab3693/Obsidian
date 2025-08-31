# 📄 **@FeignClient**

### 📝 **Что это и зачем нужно**

`@FeignClient` — это [[Spring Cloud|фреймворк]] аннотация, используемая для создания HTTP-клиентов в стиле [[Declarative REST Client|декларативного REST-клиента]] в приложениях на [[Java|Java]] с использованием Spring.  
Используется для упрощения взаимодействия между микросервисами через [[REST API|REST API]] без необходимости вручную писать код для [[HTTP Request|HTTP-запросов]].  
Главная цель: упростить и стандартизировать вызовы внешних сервисов, обеспечивая интеграцию через интерфейсы и аннотации.

---

### ⚡ **Основные возможности**

- 📍 Декларативные клиенты — интерфейсы с методами, помеченные аннотациями [[RequestMapping|@GetMapping, @PostMapping]], автоматически реализуются Feign.
    
- 🔑 Интеграция с [[Ribbon|клиентским балансировщиком]] — распределение нагрузки между инстансами сервиса.
    
- ➕ Поддержка [[Hystrix|фолбэков]] — можно задать альтернативное поведение при недоступности сервиса.
    
- ➖ Поддержка кастомных [[Decoder|декодеров]] и [[Encoder|кодировщиков]] для сериализации/десериализации объектов.
    
- 🔄 Поддержка настроек таймаутов и retry-механизмов через конфигурацию клиента.
    
- 🚫 Автоматическая генерация REST-запросов — не нужно вручную создавать [[RestTemplate|HTTP-клиент]].
    

---

### 📌 **Пример кода**

```java
import org.springframework.cloud.openfeign.FeignClient; // Подключаем аннотацию FeignClient
import org.springframework.web.bind.annotation.GetMapping; // Для маршрутизации GET-запросов
import org.springframework.web.bind.annotation.PathVariable;

@FeignClient(name = "user-service", url = "http://localhost:8080") // Обозначаем внешний сервис
public interface UserClient { 
    @GetMapping("/users/{id}") // Маршрут GET-запроса
    UserDto getUserById(@PathVariable("id") Long id); // Метод, который будет вызван через Feign
}
```

---

### 🧠 **Особенности и подводные камни**

- ❗ При использовании `@FeignClient` необходимо включить `@EnableFeignClients` в конфигурации Spring Boot.
    
- 📦 Для сложных проектов можно задавать кастомные настройки таймаутов, логирования, кодеров/декодеров через `configuration` атрибут.
    
- 🔍 Если микросервисы находятся за балансировщиком, стоит использовать `name` вместо `url` и интегрировать с [[Eureka|сервис-дискавери]].
    
- 🏎 Не рекомендуется использовать Feign для высокочастотных синхронных вызовов без кэширования и ограничения таймаутов — возможны проблемы с производительностью.
    

---

### 📊 **Визуальное представление**

```
[Your Service] --> [FeignClient Interface] --> [HTTP Request] --> [Remote Service]
```

---

### 💼 **Использование на практике**

1. **Простой вызов внешнего сервиса**
    
    ```java
    @RestController
    public class UserController {
        private final UserClient userClient;
    
        public UserController(UserClient userClient) {
            this.userClient = userClient;
        }
    
        @GetMapping("/get-user/{id}")
        public UserDto getUser(@PathVariable Long id) {
            return userClient.getUserById(id); // вызываем внешний сервис через Feign
        }
    }
    ```
    
    ✅ Позволяет обращаться к другому сервису через декларативный клиент без ручного создания HTTP-запросов.
    
2. **Использование фолбэка**
    
    ```java
    @FeignClient(name = "user-service", fallback = UserClientFallback.class)
    public interface UserClient { 
        @GetMapping("/users/{id}")
        UserDto getUserById(@PathVariable("id") Long id);
    }
    
    @Component
    public class UserClientFallback implements UserClient {
        @Override
        public UserDto getUserById(Long id) {
            return new UserDto(); // возвращаем пустой объект при недоступности сервиса
        }
    }
    ```
    
    ✅ Позволяет задавать альтернативное поведение при сбоях внешнего сервиса.
    
3. **Кастомная конфигурация таймаутов**
    
    ```java
    @Configuration
    public class FeignConfig {
        @Bean
        public Request.Options options() {
            return new Request.Options(5000, 30000); // connect timeout 5s, read timeout 30s
        }
    }
    ```
    
    ✅ Позволяет контролировать таймауты и повторные попытки.
    

---

### 🎯 **Типичные вопросы на собеседовании (с ответами)**

1. ❓ Что такое `@FeignClient`?  
    👉 [[Spring Cloud|Фреймворк]] для создания [[Declarative REST Client|декларативных HTTP-клиентов]] через интерфейсы в [[Java|Java]].
    
2. ❓ Как включить Feign в проекте Spring Boot?  
    👉 Через `@EnableFeignClients` в конфигурации приложения.
    
3. ❓ Чем Feign отличается от [[RestTemplate|RestTemplate]]?  
    👉 Feign — декларативный, автоматически генерирует HTTP-запросы из интерфейсов, RestTemplate требует ручного построения запросов.
    
4. ❓ Можно ли задать кастомный фолбэк?  
    👉 Да, через атрибут `fallback` или `fallbackFactory`.
    
5. ❓ Как настроить таймауты и retry?  
    👉 Через кастомную конфигурацию `configuration` и бин `Request.Options`.
    
6. ❓ Можно ли использовать Feign с сервис-дискавери?  
    👉 Да, указывая `name` сервиса и интегрируя с [[Eureka|Eureka]] или другим discovery.
    
7. ❓ Какие HTTP-методы поддерживаются?  
    👉 Все стандартные: GET, POST, PUT, DELETE и др., через аннотации Spring MVC (`@GetMapping`, `@PostMapping` и т.д.).
    
8. ❓ Как обрабатывать ошибки сервиса?  
    👉 Через `fallback` или `ErrorDecoder` в конфигурации Feign.
    
9. ❓ Можно ли использовать Feign для синхронных и асинхронных вызовов?  
    👉 По умолчанию — синхронные. Для асинхронных можно использовать обёртки, например, с `CompletableFuture`.
    
10. ❓ Что происходит при недоступности сервиса без фолбэка?  
    👉 Feign выбросит исключение `FeignException`, которое нужно обработать.
    

---

### 🔗 **Связанные термины**

- [[Spring Cloud|Spring Cloud]]
    
- [[Declarative REST Client|Декларативный REST-клиент]]
    
- [[Ribbon|Ribbon]]
    
- [[Hystrix|Hystrix]]
    
- [[Eureka|Eureka]]
    

---

### 🏷 **Теги**

#java #frameworks #interview #spring-cloud