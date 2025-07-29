## @Bean 
- Определяет ручной бин, возвращаемый методом внутри `@Configuration`.
```java
@Bean
public Engine engine() {
    return new Engine("V6");
}
```