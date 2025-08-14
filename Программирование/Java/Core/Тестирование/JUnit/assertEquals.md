### 🧾 **assertEquals**

**Простыми словами:** `assertEquals` — это метод из [[JUnit]], который **проверяет, что ожидаемое значение совпадает с фактическим**. Если они разные — тест упадёт с ошибкой.

---

### ⚙️ **Когда использовать**

- Чтобы проверить, что метод возвращает правильный результат
    
- Для сравнения примитивов, объектов, строк и коллекций
    
- Для автоматической проверки логики вместо ручного вывода в консоль
    

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

- Синтаксис:
    
    ```java
    assertEquals(expected, actual);
    assertEquals(expected, actual, "Сообщение об ошибке");
    ```
    
- В случае несовпадения выводит подробное сообщение
    
- Для сравнения чисел с плавающей точкой можно указать допустимую погрешность:
    
    ```java
    assertEquals(3.14, result, 0.01);
    ```
    

---

### 🔗 **Связанные термины**

- [[JUnit]]
    
- [[@Test]]
    
- [[assertTrue]]
    
- [[assertThrows]]
    

---

#java #testing #junit #assert #unittest