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
