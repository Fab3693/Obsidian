### `@Repository`  
**Назначение**: Специализированная аннотация Spring для **классов-репозиториев**, работающих с данными (DAO-слой). Помечает компоненты, отвечающие за доступ к БД, преобразование исключений и интеграцию с [[ORM]] ([[JPA]], [[Hibernate]]).  

---

#### Ключевые функции:  
1. **Преобразование исключений**:  
   Автоматически транслирует **технические исключения** (например, JDBC `SQLException`, JPA `PersistenceException`) в Spring `DataAccessException`. Это позволяет:  
   - Избежать привязки к специфике СУБД.  
   - Обрабатывать ошибки единообразно через unchecked-исключения.  

2. **Интеграция с JPA/Hibernate**:  
   Работает в связке с `@PersistenceContext` (для инъекции `EntityManager`) или Spring Data JPA (через интерфейсы `JpaRepository`).  

3. **Поддержка транзакций**:  
   Методы репозиториев обычно выполняются в **транзакционном контексте** (через `@Transactional`).  

---

#### Пример ([[Spring]] + [[JPA]]):  
```java
@Repository // Объявляет класс как репозиторий
public class UserRepository {
    @PersistenceContext
    private EntityManager em;

    @Transactional
    public void saveUser(User user) {
        em.persist(user); // Автоматическая трансляция исключений
    }
}
```

---

#### Отличия от других аннотаций:  
| Аннотация     | Роль                                  | Особенности                          |     |
| ------------- | ------------------------------------- | ------------------------------------ | --- |
| `@Repository` | **Доступ к данным** (DAO/репозиторий) | + Обработка исключений               |     |
| `@Service`    | **Бизнес-логика**                     | - Нет спец. обработки исключений     |     |
| `@Component`  | Универсальный компонент               | Базовый уровень для всех стереотипов |     |

---

#### Best Practices:  
1. **Комбинируйте с Spring Data JPA**:  
   Используйте наследование от `JpaRepository` для автоматической генерации запросов:  
   ```java
   @Repository
   public interface UserRepository extends JpaRepository<User, Long> {}
   ```  
2. **Явно настраивайте сканирование**:  
   Убедитесь, что пакет с репозиториями указан в `@SpringBootApplication(scanBasePackages = "...")`.  
3. **Избегайте логики в репозиториях**:  
   Репозиторий должен **только получать/сохранять данные**, бизнес-логика — в `@Service`.  

---

**Связанные термины**:  
[[@PersistenceContext]], [[Spring Data JPA]], [[EntityManager]], [[@Transactional]], [[DAO vs Repository Pattern]].