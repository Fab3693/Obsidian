### 🧾 **assertTrue**

**Простыми словами:** `assertTrue` — это метод из [[JUnit]], который **проверяет, что условие истинно** (`true`). Если условие ложно (`false`) — тест завершится с ошибкой.

---

### ⚙️ **Когда использовать**

- Чтобы проверить логические выражения
    
- Для тестирования результатов булевых методов
    
- Для проверки сложных условий в коде
    

---

### 📌 **Пример (JUnit 5)**

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class NumberTest {

    @Test
    void numberShouldBePositive() {
        int number = 10;
        assertTrue(number > 0);
    }
}
```

---

### 🧠 **Особенности**

- Синтаксис:
    
    ```java
    assertTrue(condition);
    assertTrue(condition, "Сообщение об ошибке");
    ```
    
- Если `condition == false` — тест упадёт
    
- Есть обратный метод [[assertFalse]] для проверки ложных условий
    

---

### 🔗 **Связанные термины**

- [[JUnit]]
    
- [[@Test]]
    
- [[assertEquals]]
    
- [[assertFalse]]
    

---

#java #testing #junit #assert #unittest