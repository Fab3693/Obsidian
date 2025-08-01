### 📦 **DTO (Data Transfer Object) для Java-разработчика**

**Простыми словами:** DTO — это "контейнер для данных", который используется для **безопасной передачи информации** между слоями приложения, например от контроллера к клиенту в [[Spring MVC]].

---

#### 🧠 **Зачем нужен DTO?**

- 🛡️ Изолировать внутренние данные (например, [[JPA]]-[[Entity]]) от внешнего мира.
    
- ⚡ Вернуть только нужные поля, убрать лишнее (`password`, `createdAt` и т.д.).
    
- 🧪 Упростить валидацию данных при входе (`@Valid`, `@NotBlank`, и др.).
    
- 🔄 Управлять структурой [[JSON-POJO|JSON]] независимо от модели БД.
    

---

#### ⚙️ **Как выглядит DTO?**

```java
// Entity (отражает таблицу в БД)
@Entity
public class User {
    private Long id;
    private String username;
    private String password;
    private LocalDateTime createdAt;
}

// DTO (что уйдёт клиенту)
public class UserDTO {
    private Long id;
    private String username;
    private String joinDate;

    public UserDTO(User user) {
        this.id = user.getId();
        this.username = user.getUsername();
        this.joinDate = user.getCreatedAt().format(DateTimeFormatter.ISO_DATE);
    }
}
```

> DTO обычно сериализуется в JSON (см. [[JSON-POJO]]) и возвращается через [[Spring MVC]]-контроллер.

---

#### 🛠 **Как создать и использовать DTO?**

1. 🧰 С помощью [[MapStruct]]:
    

```java
@Mapper
public interface UserMapper {
    UserDTO toDto(User user);
}
```

2. ⚡ С помощью Lombok:
    

```java
@Data
@AllArgsConstructor
@NoArgsConstructor
public class ProductDTO {
    private String name;
    private BigDecimal price;
}
```

3. 📦 Через `record` (Java 14+):
    

```java
public record UserDTO(Long id, String username) {}
```

---

#### ✅ **Советы**

- ❌ Не возвращай `Entity` напрямую — только `DTO`.
    
- ✅ Используй `@Valid` с `RequestDTO` в контроллерах.
    
- 🧩 Разделяй DTO по задачам:
    
    - `UserCreateDTO`
        
    - `UserResponseDTO`
        
    - `AdminUserDTO`
        

---

#### 🔗 **Связанные термины**

- [[Spring MVC]]
    
- [[JPA]]
    
- [[ORM]]
    
- [[JSON-POJO]]
    
- [[JSP]]
    
- [[JSTL]]
    
- [[Hibernate]]
    

---

#java #spring #dto #mvc #restapi #lombok #mapstruct