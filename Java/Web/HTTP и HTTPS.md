# HTTP-запрос
- Стартовая строка: метод, путь, версия протокола (например,GET /index.html HTTP/1.1)
- Заголовки (header): метаинформация о запросе (Host, Content-Type и др.)
- Тело (body): данные запроса (чаще всего в JSON формате)
## Пример HTTP запроса
Запрос:
```http
POST /api/users HTTP/1.1
Host: example.com
Content-Type: application/json
Content-Length: 72

{
    "name": "John Doe",
    "email": "johndoe@example.com",
    "password": "secure123"
}
```
Ответ:
```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 85

{
    "id": 1,
    "status": "created"
}
```

![[Pasted image 20250720151345.png]]