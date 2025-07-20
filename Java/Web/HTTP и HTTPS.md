# HTTP-запрос
- Стартовая строка: метод, путь, версия протокола (например,GET /index.html HTTP/1.1)
- Заголовки (header): метаинформация о запросе (Host, Content-Type и др.)
- Тело (body): данные запроса (чаще всего в JSON формате)
## Пример HTTP запроса
```
`POST /api/users HTTP/1.1`
`Host: example.com`
`Content-Type: application/json`
`Content-Length: 72`

`{`
    `"name": "John Doe",`
    `"email": "johndoe@example.com",`
    `"password": "secure123"`
`}`
```