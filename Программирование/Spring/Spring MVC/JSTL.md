### 🌐 **JSTL (JSP Standard Tag Library)**  
**Что это?**  
Библиотека **стандартных тегов** для JSP, которая упрощает разработку веб-страниц. Заменяет Java-код в JSP на XML-подобные теги.

---
### 🧩 **Основные компоненты JSTL**
| Группа тегов       | Префикс | Для чего используется                  |
|--------------------|---------|----------------------------------------|
| **Core**           | `c:`    | Управление потоком, переменными        |
| **Formatting**     | `fmt:`  | Форматирование дат, чисел, локализация |
| **SQL**            | `sql:`  | Работа с БД (не рекомендуется)         |
| **XML Processing** | `x:`    | Парсинг XML                            |
| **Functions**      | `fn:`   | Строковые операции                     |

> ⚠️ **Важно!** Теги SQL (`sql:`) считаются устаревшими и опасными. Всегда используйте DAO/Repository вместо прямых SQL-запросов в JSP.

---

### 💡 **Топ-10 полезных тегов**
1. **`<c:if>`**  
   Проверка условия:
   ```jsp
   <c:if test="${user.role == 'ADMIN'}">
     <button>Delete</button>
   </c:if>
   ```

2. **`<c:forEach>`**  
   Итерация по коллекциям:
   ```jsp
   <c:forEach items="${users}" var="user">
     <tr>${user.name}</tr>
   </c:forEach>
   ```

3. **`<c:set>`**  
   Создание переменных:
   ```jsp
   <c:set var="discount" value="${price * 0.15}" />
   ```

4. **`<fmt:formatDate>`**  
   Форматирование дат:
   ```jsp
   <fmt:formatDate value="${order.date}" pattern="dd.MM.yyyy HH:mm"/>
   ```

5. **`<c:url>` + `<c:param>`**  
   Генерация URL с параметрами:
   ```jsp
   <a href="<c:url value="/products">
        <c:param name="category" value="books"/>
    </c:url>">Books</a>
   ```

---

### 🔧 **Как подключить JSTL**
1. Добавьте зависимость в `pom.xml`:
   ```xml
   <dependency>
     <groupId>jakarta.servlet.jsp.jstl</groupId>
     <artifactId>jakarta.servlet.jsp.jstl-api</artifactId>
     <version>3.0.0</version>
   </dependency>
   ```

2. В начале JSP-страницы:
   ```jsp
   <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
   <%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
   ```

---

### 🆚 **JSTL vs Чистый Java-код в JSP**
**Плохой подход (scriptlets):**
```jsp
<% for(User user : (List<User>)request.getAttribute("users")) { %>
   <%= user.getName() %> 
<% } %>
```

**Хороший подход (JSTL):**
```jsp
<c:forEach items="${users}" var="user">
   ${user.name}
</c:forEach>
```

**Преимущества JSTL:**
1. Читаемость кода
2. Безопасность (нет прямого доступа к Java-объектам)
3. Проще поддерживать
4. Поддержка i18n (интернационализация)

---

### 💎 **Лучшие практики**
1. **Избегайте scriptlets**  
   Полностью замените `<% ... %>` на JSTL/EL.

2. **Используйте Expression Language (EL)**  
   Вместо `<%= request.getAttribute("user") %>` пишите `${user}`.

3. **Комбинируйте с EL-функциями**  
   ```jsp
   ${fn:toUpperCase(user.name)}
   ```

4. **Для сложной логики создавайте custom tags**  
   Если тегов JSTL недостаточно.

> 📊 **Статистика использования**:  
> 87% Java-разработчиков используют JSTL в JSP-проектах (источник: JetBrains, 2023)

```mermaid
pie
    title Распространённость тегов JSTL
    “Core (c:)” : 65
    “Formatting (fmt:)” : 20
    “Functions (fn:)” : 10
    “Другие” : 5
```