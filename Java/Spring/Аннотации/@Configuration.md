## @Configuration 
- Помечает класс как Java-конфигурацию (аналог XML-файла).
- Содержит методы с `@Bean`.
```java
@Configuration
public class AppConfig {
    @Bean
    public Car car() {
        return new Car();
    }
}
```