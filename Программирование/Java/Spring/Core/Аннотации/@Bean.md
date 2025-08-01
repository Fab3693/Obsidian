### 📄 **@Bean**

**Простыми словами:** `@Bean` — это аннотация, которую применяют к методу внутри класса, помеченного `@Configuration`. Метод с `@Bean` создаёт и настраивает объект, который Spring регистрирует как бин в своём контексте.

---

#### ⚙️ **Для чего нужна:**

- 📦 Позволяет программно определять бины вместо XML.
    
- 🔗 Настраивать зависимости через параметры метода.
    
- ⚙️ Управлять жизненным циклом через `initMethod`/`destroyMethod`.
    

---

#### 🔤 **Пример:**

```java
@Configuration
public class AppConfig {

    @Bean
    public DataSource dataSource(
            @Value("${db.url}") String url,
            @Value("${db.user}") String user,
            @Value("${db.pass}") String pass) {
        return DataSourceBuilder.create()
            .url(url)
            .username(user)
            .password(pass)
            .build();
    }

    @Bean(initMethod = "initialize", destroyMethod = "cleanup")
    public CacheManager cacheManager() {
        return new CacheManager();
    }
}
```

- Spring вызывает `dataSource(...)`, получает `DataSource` и кладёт в контекст.
    
- При закрытии контекста вызовет `cleanup()` у `cacheManager`.
    

---

#### ✅ **Советы:**

- Предпочитай **конструкторную инъекцию**: параметры метода — это зависимости.
    
- Указывай `initMethod`/`destroyMethod`, если нужен кастомный lifecycle.
    
- Для простых компонентов без конфигурации лучше использовать `@Component`.
    

---

#### 🔗 **Связанные термины**

- [[Configuration]]
    
- [[Component]]
    
- [[Autowired]]
    
- [[Value]]
    
- [[Scope]]
    
- [[PostConstruct]] / [[PreDestroy]]
    

---

#spring #bean #configuration #di #lifecycle