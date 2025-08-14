### 🧾 **@InjectMocks**

**Простыми словами:** `@InjectMocks` — это аннотация из [[Mockito]], которая **создаёт объект тестируемого класса и автоматически внедряет в него моки** (объекты с [[@Mock]]).

---

### ⚙️ **Когда использовать**

- Когда нужно протестировать класс, который зависит от других компонентов
    
- Чтобы автоматически подставить моки в поля или конструктор
    
- Для уменьшения ручного кода по созданию объекта и передачи зависимостей
    

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
    UserRepository repo; // поддельный объект

    @InjectMocks
    UserService service; // сюда автоматически внедрится repo

    @Test
    void shouldCallRepositorySave() {
        service.addUser(new User("Alex"));
        verify(repo, times(1)).save(any(User.class));
    }
}
```

---

### 🧠 **Особенности**

- Работает с внедрением через:
    
    - Конструктор
        
    - Сеттеры
        
    - Поля напрямую
        
- Требует включения `MockitoExtension` или `MockitoAnnotations.openMocks(this)`
    
- Все зависимости, помеченные [[@Mock]], будут внедрены в этот объект
    

---

### 🔗 **Связанные термины**

- [[Mockito]]
    
- [[@Mock]]
    
- [[JUnit]]
    
- [[assertEquals]]
    

---

#java #testing #mockito #injectmocks #unittest