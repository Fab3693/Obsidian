### 🧾 **assertThrows**

**Простыми словами:** `assertThrows` — это метод из [[JUnit]], который **проверяет, что код выбрасывает ожидаемое исключение**. Если исключение не выброшено или его тип другой — тест упадёт.

---

### ⚙️ **Когда использовать**

- Для тестирования обработки ошибок
    
- Чтобы убедиться, что метод выбрасывает правильный тип исключения
    
- При проверке валидации входных данных
    

---

### 📌 **Пример (JUnit 5)**

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {

    @Test
    void divideByZeroShouldThrowException() {
        Calculator calc = new Calculator();
        assertThrows(ArithmeticException.class, () -> calc.divide(10, 0));
    }
}
```

---

### 🧠 **Особенности**

- Синтаксис:
    
    ```java
    assertThrows(ExceptionType.class, () -> { /* код */ });
    ```
    
- Возвращает объект исключения, чтобы можно было проверить сообщение:
    
    ```java
    Exception ex = assertThrows(IllegalArgumentException.class, () -> method());
    assertEquals("Ошибка", ex.getMessage());
    ```
    
- Работает только в JUnit 5 (в JUnit 4 использовался `@Test(expected = ...)`)
    

---

### 🔗 **Связанные термины**

- [[JUnit]]
    
- [[@Test]]
    
- [[assertEquals]]
    
- [[assertTrue]]
    

---

#java #testing #junit #assert #unittest