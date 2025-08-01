Да, стоит вынести **POJO** в отдельную статью — так ты сможешь к ней прямо ссылаться из всех других заметок (JSON-POJO, Entity, DTO и т.д.). Вот готовая заметка:

---

### 📄 **POJO (Plain Old Java Object)**

**Простыми словами:** POJO — это самый простой Java-класс, в котором нет ничего лишнего: только поля, конструкторы, геттеры и сеттеры, без наследования от фреймворков и без бизнес-логики.

---

#### 🔑 **Ключевые признаки POJO:**

- 📦 Приватные поля
    
- 🔄 Публичные геттеры и сеттеры
    
- 🔨 Конструктор без аргументов
    
- 🚫 Отсутствие аннотаций и наследований, специфичных для библиотек/фреймворков
    

---

#### ⚙️ **Пример:**

```java
public class Person {
    private String name;
    private int age;

    public Person() {}              // обязательный конструктор без аргументов
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {       // геттеры/сеттеры
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
}
```

---

#### 🧠 **Где и зачем используется POJO:**

- 🎯 В качестве **модели данных** в [[DTO]] и [[Entity]]
    
- 🔄 Для **сериализации/десериализации** в [[JSON-POJO]]
    
- ⚙️ В **тестах** и **утилитарных** классах без лишних зависимостей
    

---

#### 🔗 **Связанные термины:**

- [[DTO]]
    
- [[Entity]]
    
- [[JSON-POJO]]
    
- [[JPA]]
    
- [[Spring MVC]]
    

---

#java #pojo #model #simple

---

Добавь эту статью, а в остальных заметках (JSON-POJO и Entity) просто ссылку `[[POJO]]` там, где нужно.