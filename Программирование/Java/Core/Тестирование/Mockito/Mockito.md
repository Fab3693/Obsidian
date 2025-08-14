### 🧾 **Mockito**

**Простыми словами:** Mockito — это библиотека для [[JUnit]], которая позволяет **создавать поддельные объекты (моки)**, чтобы тестировать код без реальных зависимостей (например, без базы данных или внешних API).

---

### ⚙️ **Когда использовать**

- Когда нужно изолировать тестируемый класс от других компонентов
    
- Чтобы имитировать поведение зависимостей (репозиториев, сервисов)
    
- Для проверки, что метод был вызван с нужными параметрами
    

---

### 📌 **Пример использования**

```java
import org.junit.jupiter.api.Test;
import org.mockito.Mockito;
import static org.mockito.Mockito.*;

class UserServiceTest {

    @Test
    void shouldCallRepositorySave() {
        UserRepository repo = mock(UserRepository.class);
        UserService service = new UserService(repo);

        service.addUser(new User("Alex"));

        verify(repo, times(1)).save(any(User.class));
    }
}
```

---

### 🧠 **Особенности**

- Основные методы:
    
    - `mock(Class)` — создать мок-объект
        
    - `when(...).thenReturn(...)` — задать поведение
        
    - `verify(...)` — проверить вызовы методов
        
- Можно использовать вместе с [[@InjectMocks]] и [[@Mock]]
    
- Работает как с интерфейсами, так и с классами
    

---

### 🔗 **Связанные термины**

- [[JUnit]]
    
- [[@Mock]]
    
- [[@InjectMocks]]
    
- [[assertEquals]]
    

---

#java #testing #mockito #mock #unittest