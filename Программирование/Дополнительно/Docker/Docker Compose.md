### 📄 **Docker Compose**

**Простыми словами:** Docker Compose — это инструмент для **управления несколькими контейнерами Docker одновременно** с помощью одного файла конфигурации (`docker-compose.yml`). Позволяет запускать целые приложения с зависимостями одной командой.

---

### 🧩 **Что умеет Docker Compose**

- 📦 Определяет несколько контейнеров и их связи в одном файле
    
- 🔗 Настраивает сеть между контейнерами
    
- 💾 Подключает тома (volumes) для хранения данных
    
- ⚡ Позволяет запускать, останавливать и пересобирать все контейнеры командой
    

---

### 📌 **Пример docker-compose.yml**

```yaml
version: '3.9'
services:
  app:
    build: .
    ports:
      - "8080:8080"
    depends_on:
      - db

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydb
    volumes:
      - db-data:/var/lib/postgresql/data

volumes:
  db-data:
```

📍 Здесь запускаются два контейнера: `app` и `db`. Контейнер `app` зависит от `db`.

---

### ⚙️ **Основные команды Docker Compose**

- `docker-compose up` — поднять все сервисы
    
- `docker-compose down` — остановить и удалить контейнеры
    
- `docker-compose build` — собрать образы
    
- `docker-compose logs` — посмотреть логи всех сервисов
    

---

### 🧠 **Особенности**

- Позволяет легко управлять многоконтейнерными приложениями
    
- Настройки для каждого сервиса находятся в одном файле
    
- Интегрируется с [[Docker]] и [[Kubernetes]] для более сложных сценариев
    
- Удобно использовать для локальной разработки, тестирования и CI/CD
    

---

### 🔗 **Связанные термины**

- [[Docker]]
    
- [[Kubernetes]]
    
- [[Spring Boot]]
    
- [[Microservices]]
    
- [[CI/CD]]
    

---

#docker-compose #docker #containers #microservices #devops #spring #java