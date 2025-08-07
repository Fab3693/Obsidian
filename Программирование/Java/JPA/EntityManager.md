### 🧾 **EntityManager**

**Простыми словами:** `EntityManager` — это **основной интерфейс JPA** для **взаимодействия с базой данных**. Через него ты можешь **вручную управлять [[Entity]]-объектами**: сохранять, удалять, искать и обновлять.

---

### ⚙️ **Когда использовать**

- Когда нужно **точно контролировать работу с БД**
    
- Если не используешь [[JPA]] и [[@Repository]]
    
- Для сложных операций, кастомных запросов или явного управления транзакциями
    
- Внутри сервисов, обёрнутых в [[@Transactional]]
    

---

### 📌 **Пример использования**

```java
@PersistenceContext
private EntityManager em;

public User findUser(Long id) {
    return em.find(User.class, id);
}

public void saveUser(User user) {
    em.persist(user);
}
```

---

### 🧠 **Основные методы**

|Метод|Что делает|
|---|---|
|`find()`|Получить объект по ID|
|`persist()`|Сохранить новый объект|
|`merge()`|Обновить существующий объект|
|`remove()`|Удалить объект|
|`createQuery()`|Выполнить JPQL-запрос|
|`createNativeQuery()`|Выполнить SQL-запрос|

---

### 🧠 **Особенности**

- Используется **вместо** или **в дополнение к** [[@Repository]]
    
- Требует аннотацию `@PersistenceContext` для внедрения
    
- Управляется [[JPA]]-провайдером, например [[Hibernate]]
    
- Работает внутри транзакций ([[@Transactional]])
    

---

### 🔗 **Связанные термины**

- [[JPA]]
    
- [[Entity]]
    
- [[@Transactional]]
    
- [[@Repository]]
    
- [[JPQL]]
    
- [[Hibernate]]
    

---

#java #jpa #entitymanager #persistence #database #hibernate #spring