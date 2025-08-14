### 🧾 **@Mock**

**Простыми словами:** `@Mock` — это аннотация из [[Mockito]], которая **создаёт поддельный объект (мок)** для тестирования, чтобы заменить реальную зависимость.

---

### ⚙️ **Когда использовать**

- Чтобы изолировать тестируемый класс от внешних зависимостей
    
- Для задания фиктивного поведения методов
    
- Для проверки вызовов методов без реальной логики
    

---

### 📌 **Пример использования**

```java
import org.junit.jupiter.api.Test;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoExtension;

import static org.mockito.Mockito.*;

@ExtendWith(MockitoExtension.class)
class UserServiceTest {

    @Mock
    UserRepository repo; // мок-объект

    @InjectMocks
    UserService service; // сюда внедрится мок

    @Test
    void shouldCallRepositorySave() {
        service.addUser(new User("Alex"));
        verify(repo, times(1)).save(any(User.class));
    }
}
```

---

### 🧠 **Особенности**

- Работает только вместе с `@ExtendWith(MockitoExtension.class)` или `MockitoAnnotations.openMocks(this)`
    
- По умолчанию возвращает `null` или пустые значения, пока не настроено `when(...).thenReturn(...)`
    
- Используется вместе с [[@InjectMocks]] для автоматической подстановки моков в тестируемый объект
    

---

### 🔗 **Связанные термины**

- [[Mockito]]
    
- [[@InjectMocks]]
    
- [[JUnit]]
    
- [[assertEquals]]
    

---

#java #testing #mockito #mock #unittest