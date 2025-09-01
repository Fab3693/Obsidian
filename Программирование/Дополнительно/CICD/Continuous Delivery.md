# 📄 **Continuous Delivery**

### 📝 **Что это и зачем нужно**

**Continuous Delivery** — это практика в [[DevOps|DevOps]], при которой изменения, прошедшие [[Continuous Integration|Continuous Integration]], автоматически подготавливаются к выпуску в продакшн.  
Используется для ускорения доставки кода без ручных действий.  
Главная цель: сделать так, чтобы каждая новая версия приложения могла быть развернута в [[Production|продакшне]] в любой момент.

---

### ⚡ **Основные возможности**

- 📍 Автоматическая сборка и тестирование — после [[Commit|коммита]] и [[Merge|слияния]]
    
- 🔑 Подготовка артефактов — создание готовых пакетов для деплоя
    
- ➕ Автоматизация регрессионных и интеграционных тестов
    
- ➖ Требует надёжной инфраструктуры для сборок и окружений
    
- 🔄 Интеграция с [[Pipeline|pipeline]] и [[CI|Continuous Integration]]
    
- 🚫 Ошибки в конфигурации окружений блокируют выпуск
    

---

### 📌 **Пример кода (GitLab CI/CD)**

```yaml
# Pipeline для Continuous Delivery
stages:
  - build   # Сборка
  - test    # Тестирование
  - deploy  # Деплой

build:
  stage: build
  script:
    - mvn clean package # Собираем артефакт

test:
  stage: test
  script:
    - mvn test # Запускаем тесты

deploy:
  stage: deploy
  script:
    - echo "Разворачиваем на staging сервере" # Имитируем деплой
  only:
    - main # Только при изменениях в главной ветке
```

---

### 🧠 **Особенности и подводные камни**

- ❗ Автоматизация охватывает не только сборку, но и подготовку окружений
    
- 📦 Необходима система управления конфигурациями ([[Ansible|Ansible]], [[Terraform|Terraform]])
    
- 🔍 Ошибки в тестах блокируют выпуск в [[Production|продакшн]]
    
- 🏎 Чем стабильнее pipeline, тем быстрее и безопаснее релизы
    

---

### 📊 **Визуальное представление**

```
Commit → CI (сборка + тесты)
        ↓
   CD (подготовка артефактов)
        ↓
   Deploy на staging
        ↓
   Готовность к продакшн-деплою
```

---

### 💼 **Использование на практике**

1. **Автоматический деплой на staging**
    
    ```yaml
    deploy:
      stage: deploy
      script:
        - scp target/app.jar server:/apps # Копируем артефакт
    ```
    
    ✅ Упрощает тестирование новой версии.
    
2. **Регрессионные тесты перед релизом**
    
    ```yaml
    test:
      stage: test
      script:
        - mvn verify # Запускаем интеграционные тесты
    ```
    
    ✅ Проверяет совместимость новой версии.
    
3. **Хранение артефактов**
    
    ```yaml
    artifacts:
      paths:
        - target/*.jar # Сохраняем билд
    ```
    
    ✅ Позволяет быстро разворачивать одинаковую версию в разных окружениях.
    

---

### 🎯 **Типичные вопросы на собеседовании (с ответами)**

1. ❓ Что такое Continuous Delivery?  
    👉 Это практика, при которой каждая версия приложения после [[Continuous Integration|CI]] автоматически готова к развертыванию.
    
2. ❓ Чем отличается Continuous Delivery от Continuous Deployment?  
    👉 [[Continuous Delivery|CD]] готовит код к выпуску, но решение о деплое принимает человек. [[Continuous Deployment|Continuous Deployment]] — деплой без участия человека.
    
3. ❓ Какие инструменты используют для Continuous Delivery?  
    👉 [[Jenkins|Jenkins]], [[GitLab CI|GitLab CI]], [[GitHub Actions|GitHub Actions]], [[ArgoCD|ArgoCD]].
    
4. ❓ Как Continuous Delivery снижает риски?  
    👉 Благодаря автоматическим тестам и контролируемым развертываниям.
    
5. ❓ Почему Continuous Delivery требует хорошего тестирования?  
    👉 Потому что именно тесты подтверждают, что код можно безопасно доставить в [[Production|продакшн]].
    

---

### 🔗 **Связанные термины**

- [[Continuous Integration|Continuous Integration]]
    
- [[Continuous Deployment|Continuous Deployment]]
    
- [[Pipeline|Pipeline]]
    
- [[DevOps|DevOps]]
    

---

### 🏷 **Теги**

#devops #cd #automation #interview #delivery