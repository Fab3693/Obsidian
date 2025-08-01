### 📄 **JSON-POJO**

**Простыми словами:** JSON-POJO — это обычный Java-объект, который можно **преобразовать в JSON-строку и обратно**. Это основа работы REST API: ты отправляешь и принимаешь данные как JSON, а внутри работаешь с Java-объектами.

---

#### 🔄 **1. Java → JSON (сериализация)**

```java
public class JacksonTest {  
  
    ObjectMapper objectMapper = new ObjectMapper();

    @Test  
    void pojoToJsonString() throws JsonProcessingException {  
        Employee employee = new Employee("Mark", "James", 20);  
  
        String json = objectMapper.writeValueAsString(employee);  
  
        System.out.println(json);  
    }  
}
```

📤 Результат:

```
{"firstName":"Mark","lastName":"James","age":20}
```

---

#### 🔁 **2. JSON → Java (десериализация)**

```java
public class JacksonTest {  
  
    ObjectMapper objectMapper = new ObjectMapper();

    @Test  
    void jsonStringToPojo() throws JsonProcessingException {  
        String employeeJson = "{\n" +  
                " \"firstName\" : \"Jalil\",\n" +  
                " \"lastName\" : \"Jarjanazy\",\n" +  
                " \"age\" : 30\n" +  
                "}";  
  
        Employee employee = objectMapper.readValue(employeeJson, Employee.class);  
  
        assertThat(employee.getFirstName()).isEqualTo("Jalil");  
    }  
}
```

---

#### 📦 **Что такое POJO?**

POJO (Plain Old Java Object) — это просто класс с полями, конструкторами, геттерами и сеттерами, **без логики и наследования от других фреймворков**.

```java
public class Employee {
    private String firstName;
    private String lastName;
    private int age;

    // конструктор, геттеры/сеттеры
}
```

---

#### 🧠 **Где используется:**

- В [[DTO]] и [[Entity]]
    
- В [[Spring MVC]] при получении `@RequestBody` и отправке `@ResponseBody`
    
- При работе с [[JSON]] в микросервисах и REST API
    

---

#### 🔗 **Связанные термины**

- [[DTO]]
    
- [[JSON]]
    
- [[Spring MVC]]
    
- [[Entity]]
    
- [[JPA]]
    

---

#java #json #pojo #jackson #restapi #spring