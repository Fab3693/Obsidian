### 🧾 **JUnit**

**Простыми словами:** JUnit — это популярный **фреймворк для модульного тестирования** в Java, который позволяет автоматически проверять работу кода.

---

### ⚙️ **Когда использовать**

- Для тестирования отдельных методов или классов
    
- Чтобы убедиться, что изменения в коде не ломают существующую логику
    
- Для автоматизации тестирования в CI/CD
    

---

### 📌 **Пример теста (JUnit 5)**

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {

    @Test
    void testSum() {
        Calculator calc = new Calculator();
        assertEquals(5, calc.sum(2, 3));
    }
}
```

---

### 🧠 **Особенности**

- Аннотация [[@Test]] помечает метод как тестовый
    
- Можно использовать `assertEquals`, `assertTrue`, `assertThrows` и др. для проверки результата
    
- Легко интегрируется с [[Spring Boot]] и другими фреймворками
    
- Актуальная версия — JUnit 5 (Jupiter API)
    

---

### 🔗 **Связанные термины**

- [[@Test]]
    
- [[Mockito]]
    
- [[Spring Boot Test]]
    
- [[CI/CD]]
    

---

#java #testing #junit #unittest #tdd