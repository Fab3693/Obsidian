### 🛡 **Spring Security**

**Простыми словами:** Spring Security — это модуль [[Spring Framework]] для **защиты веб-приложений**, который отвечает за **аутентификацию** (проверку, кто пользователь) и **авторизацию** (проверку, что ему можно).

---

### 🧩 **Что делает Spring Security**

- 🔐 Проверяет логин и пароль, токены, JWT и т.п.
    
- 🛂 Ограничивает доступ к страницам, методам и API
    
- 🔄 Автоматически перенаправляет на страницу входа
    
- 🧱 Защищает от CSRF, XSS и других атак
    

---

### ⚙️ **Пример настройки**

```java
[[ @Configuration ]]
[[ @EnableWebSecurity ]]
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .antMatchers("/admin/**").hasRole("ADMIN")
                .antMatchers("/", "/home").permitAll()
                .anyRequest().authenticated()
            .and()
            .formLogin()
                .loginPage("/login")
                .permitAll()
            .and()
            .logout()
                .permitAll();
    }
}
```

---

### 🔄 **Как работает**

1. Пользователь открывает защищённый ресурс
    
2. Spring Security проверяет, авторизован ли он
    
3. Если нет — отправляет на страницу логина
    
4. После входа проверяет его права и открывает доступ
    

---

### 🧠 **Особенности**

- Можно использовать разные механизмы входа: форма, Basic Auth, JWT
    
- Легко интегрируется с базой пользователей через [[JPA]]
    
- Гибко настраивается с помощью фильтров и конфигов
    

---

### 🔗 **Связанные термины**

- [[REST API]]
    
- [[Spring MVC]]
    
- [[HTTP - запрос]]
    
- [[JWT]]
    

---

#java #spring #security #authentication #authorization #jwt #csrf