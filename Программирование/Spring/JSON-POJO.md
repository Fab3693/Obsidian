Начнем с преобразования POJO в строку JSON:

```
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

В качестве вывода увидим следующее:

```
{"firstName":"Mark","lastName":"James","age":20}
```

Теперь посмотрим, как преобразовать строку JSON в объект `Employee` с помощью `ObjectMapper`.

```
public class JacksonTest {  
  ...
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