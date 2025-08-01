### 📄 **@Configuration**

**Простыми словами:** `@Configuration` — это аннотация Spring, которая помечает класс как **источник определения бинов**. Внутри такого класса ты описываешь методы с [[@Bean]], и Spring регистрирует возвращаемые ими объекты в контексте.

---

#### ⚙️ **Для чего нужна:**

- 📦 Объявлять бины программно вместо XML-конфигураций
    
- 🔄 Группировать связанные определения бинов в одном классе
    
- ⚙️ Позволяет использовать Java-код для условного создания бинов и настройки
    

---

#### 🔤 **Пример использования:**

```java
@Configuration
public class AppConfig {

    @Bean
    public DataSource dataSource() {
        return DataSourceBuilder.create()
            .url("jdbc:h2:mem:testdb")
            .username("sa")
            .password("")
            .build();
    }

    @Bean
    public JdbcTemplate jdbcTemplate(DataSource ds) {
        return new JdbcTemplate(ds);
    }
}
```

- При старте Spring создаст бин `dataSource` и передаст его в метод `jdbcTemplate(...)`.
    

---

#### ✅ **Советы:**

- Используй `@Configuration` вместо множества `@Component` + `@Bean`, когда нужно настроить внешние ресурсы.
    
- Класс с `@Configuration` по умолчанию — **proxyBeanMethods=true**, что гарантирует синглтон для вызова методов между собой.
    
- Для лёгких настроек можно предпочесть `[[@Component]]` + `@Bean` в отдельных классах — когда нет межзависимости методов.
    

---

#### 🔗 **Связанные термины**

- [[@Component]]
    
- [[@Bean]]
    
- [[@Value]]
    
- [[@PropertySource]]
    
- [[@ConfigurationProperties]]
    
- [[@Autowired]]
    

---

#spring #configuration #bean #context #di