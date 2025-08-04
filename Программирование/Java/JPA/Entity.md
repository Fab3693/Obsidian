### 📄 **Entity**

**Простыми словами:** Entity — это обычный Java-класс, который отображает **таблицу в базе данных**. Каждый его экземпляр соответствует одной строке в этой таблице.

---

#### 🧩 **Что из себя представляет Entity:**

- 📦 Plain Old Java Object (POJO)
    
- 💠 Аннотирован [[@Entity]]
    
- 🔗 Связан с таблицей через [[@Table]] (необязательно)
    
- 🆔 Поле с [[@Id]] — первичный ключ
    
- 🔄 Поля маппятся на колонки через [[@Column]] (по умолчанию имя совпадает)
    

---

#### ⚙️ **Пример Entity-класса:**

```java
@Entity
@Table(name = "employees")
public class Employee {

    @Id
    @GeneratedValue
    private Long id;

    @Column(name = "first_name")
    private String firstName;

    private String lastName;

    // Обязательный конструктор без аргументов
    public Employee() {}

    // Геттеры и сеттеры
}
```

---

#### 🧠 **Зачем нужны Entity:**

- 🔄 Позволяют сохранять и загружать объекты из БД без [[SQL]]
    
- 🔗 Используются в [[JPA]] и [[Hibernate]] для реализации [[ORM]]
    
- 🏷️ В связке с [[DTO]] и [[Spring MVC]] строят полный цикл работы с данными
    

---

#### ✅ **Советы:**

- ❌ Не смешивай бизнес-логику в Entity
    
- ✅ Держи у Entity только поля и методы доступа
    
- 🧹 Используй [[@GeneratedValue]] для автоматического создания ключей
    
- 🔍 Если имя таблицы или колонки отличается, явно указывай `@Table(name…)` и `@Column(name…)`
    

---

#### 🔗 **Связанные термины**

- [[JPA]]
    
- [[Hibernate]]
    
- [[ORM]]
    
- [[DTO]]
    
- [[Spring MVC]]
    
- [[POJO]]
    

---

#java #entity #jpa #hibernate #orm #spring #database