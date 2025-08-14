### 🧾 **@Test**

**Простыми словами:** `@Test` — это аннотация из [[JUnit]], которая **помечает метод как тестовый**, чтобы фреймворк знал, что его нужно запустить при тестировании.

---

### ⚙️ **Когда использовать**

- Чтобы явно указать, что метод — это тест
    
- Для проверки работы кода в автоматическом режиме
    
- Вместе с [[assertEquals]], [[assertTrue]], [[assertThrows]] и другими методами утверждений
    

---

### 📌 **Пример (JUnit 5)**

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {

    @Test
    void sumShouldReturnCorrectValue() {
        Calculator calc = new Calculator();
        assertEquals(5, calc.sum(2, 3));
    }
}
```

---

### 🧠 **Особенности**

- В JUnit 5 импортируется из `org.junit.jupiter.api.Test`
    
- В JUnit 4 импортировалась из `org.junit.Test`
    
- Может использовать дополнительные параметры, например, для таймаута или указания исключения (в JUnit 4)
    
- В JUnit 5 тесты можно дополнять аннотациями вроде [[@BeforeEach]] и [[@AfterEach]]
    

---

### 🔗 **Связанные термины**

- [[JUnit]]
    
- [[@BeforeEach]]
    
- [[@AfterEach]]
    
- [[assertEquals]]
    

---

#java #testing #junit #unittest #tdd