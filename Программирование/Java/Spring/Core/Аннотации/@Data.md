### 🧾 **@Data**

**Простыми словами:** `@Data` — это аннотация из библиотеки **Lombok**, которая автоматически **создаёт геттеры, сеттеры, `toString()`, `equals()`, `hashCode()` и конструктор для финальных полей**.

---

### ⚙️ **Когда использовать**

- Когда нужен простой класс с полями (например, [[DTO]] или [[Entity]])
    
- Чтобы не писать вручную геттеры/сеттеры и другие методы
    
- Для удобства и сокращения шаблонного кода
    

---

### 📌 **Пример использования**

```java
import lombok.Data;

@Data
public class User {
    private Long id;
    private String username;
    private String email;
}
```

После компиляции Lombok сгенерирует:

- `getId()`, `setId(...)`
    
- `getUsername()`, `setUsername(...)`
    
- `toString()`, `equals()`, `hashCode()`
    
- Конструктор для `final` полей
    

---

### 🧠 **Особенности**

- Объединяет в себе: [[@Getter]], [[@Setter]], [[@RequiredArgsConstructor]], [[@ToString]], [[@EqualsAndHashCode]]
    
- Работает на этапе компиляции — код реально создаётся в `.class`
    
- Удобно для [[DTO]], но осторожно для [[Entity]] в [[JPA]] (лучше использовать отдельно геттеры/сеттеры)
    

---

### 🔗 **Связанные термины**

- [[Lombok]]
    
- [[DTO]]
    
- [[Entity]]
    
- [[@Getter]]
    
- [[@Setter]]
    

---

#java #lombok #data #dto #entity