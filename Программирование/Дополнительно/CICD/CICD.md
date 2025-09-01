# 📄 **CICD**

### 📝 **Что это и зачем нужно**

**CICD** — это практика в [[DevOps|DevOps]], объединяющая [[Continuous Integration|непрерывную интеграцию]] и [[Continuous Delivery|непрерывную доставку]] (или [[Continuous Deployment|непрерывное развертывание]]).  
Используется для автоматизации сборки, тестирования и доставки кода.  
Главная цель: ускорение выпуска ПО и повышение стабильности через автоматизацию.

---

### ⚡ **Основные возможности**

- 📍 Автоматическая сборка — после каждого коммита код собирается и тестируется
    
- 🔑 Непрерывная интеграция — проверка совместимости новых изменений с основной веткой
    
- ➕ Непрерывная доставка — автоматическая подготовка кода к релизу
    
- ➖ Непрерывное развертывание — деплой в продакшен без ручного вмешательства
    
- 🔄 Обратная связь — быстрые уведомления об ошибках
    
- 🚫 Минимизация ручных действий — снижение риска человеческих ошибок
    

---

### 📌 **Пример кода (Jenkinsfile)**

```groovy
// Определяем конвейер
pipeline {
    agent any // Запускаем на любом доступном агенте
    stages {
        stage('Build') { // Этап сборки
            steps {
                sh 'mvn clean install' // Сборка проекта с помощью Maven
            }
        }
        stage('Test') { // Этап тестирования
            steps {
                sh 'mvn test' // Запуск юнит-тестов
            }
        }
        stage('Deploy') { // Этап деплоя
            steps {
                sh 'scp target/app.jar server:/apps/' // Копирование артефакта на сервер
            }
        }
    }
}
```

---

### 🧠 **Особенности и подводные камни**

- ❗ Нужна культура [[DevOps|DevOps]], иначе автоматизация не принесёт пользы
    
- 📦 Требует настройки [[Pipeline|pipeline]] и инфраструктуры
    
- 🔍 Ошибки в тестах могут блокировать доставку кода
    
- 🏎 Чем чаще релизы — тем быстрее обратная связь и выше качество
    

---

### 📊 **Визуальное представление**

```
Разработчик → Git Push
        ↓
 Continuous Integration (сборка + тесты)
        ↓
 Continuous Delivery (подготовка к релизу)
        ↓
 Continuous Deployment (автодеплой)
        ↓
  Продукт в продакшене
```

---

### 💼 **Использование на практике**

1. **Автоматическая проверка кода при коммите**
    
    ```yaml
    name: CI
    on: [push] # Запускаем при каждом push
    jobs:
      build:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2 # Получаем код
          - run: mvn test # Запускаем тесты
    ```
    
    ✅ Код проверяется сразу после загрузки в репозиторий.
    
2. **Непрерывная доставка артефактов**
    
    ```yaml
    deploy:
      needs: build
      runs-on: ubuntu-latest
      steps:
        - run: scp target/app.jar server:/apps/ # Загружаем приложение на сервер
    ```
    
    ✅ Автоматически подготавливает приложение к запуску.
    
3. **Непрерывное развертывание в Kubernetes**
    
    ```yaml
    - name: Deploy to Kubernetes
      run: kubectl apply -f deployment.yaml # Применяем манифест в кластере
    ```
    
    ✅ Приложение сразу выкатывается в кластер без ручного вмешательства.
    

---

### 🎯 **Типичные вопросы на собеседовании (с ответами)**

1. ❓ Что такое CICD?  
    👉 Это практика, объединяющая [[Continuous Integration|непрерывную интеграцию]] и [[Continuous Delivery|непрерывную доставку]]/[[Continuous Deployment|непрерывное развертывание]].
    
2. ❓ В чём разница между Continuous Delivery и Continuous Deployment?  
    👉 [[Continuous Delivery|Delivery]] готовит код к релизу, но деплой запускается вручную; [[Continuous Deployment|Deployment]] — деплой выполняется автоматически.
    
3. ❓ Какие инструменты используют для CICD?  
    👉 [[Jenkins|Jenkins]], [[GitLab CI|GitLab CI]], [[GitHub Actions|GitHub Actions]], [[TeamCity|TeamCity]], [[ArgoCD|ArgoCD]].
    
4. ❓ Какие преимущества CICD?  
    👉 Быстрая обратная связь, меньше багов в продакшене, автоматизация рутины.
    
5. ❓ Какие подводные камни CICD?  
    👉 Нужна инфраструктура, качественные [[Unit tests|юнит-тесты]], культура работы с [[Git|Git]].
    

---

### 🔗 **Связанные термины**

- [[DevOps|DevOps]]
    
- [[Continuous Integration|Continuous Integration]]
    
- [[Continuous Delivery|Continuous Delivery]]
    
- [[Continuous Deployment|Continuous Deployment]]
    
- [[Pipeline|Pipeline]]
    

---

### 🏷 **Теги**

#devops #cicd #automation #interview #infrastructure