# 📄 **API Server**

### 📝 **Что это и зачем нужно**

**API Server** — это центральный компонент [[Kubernetes|Kubernetes]]-кластера, который принимает все запросы на изменение или получение состояния.  
Он реализует REST [[API|API]], через которое работают [[kubectl|kubectl]], веб-интерфейсы и внутренние компоненты.

Проще говоря, **API Server — это «дверь» в кластер**, через которую проходят все команды.

---

### ⚡ **Основные задачи**

- 📩 Принимает и обрабатывает запросы (например, `kubectl apply`)
    
- 🗄 Сохраняет и получает данные из [[etcd|etcd]]
    
- ✅ Проверяет правильность конфигурации (валидация [[YAML|YAML]]-манифестов)
    
- 🔑 Управляет доступом ([[RBAC|RBAC]], [[Authentication|аутентификация]] и [[Authorization|авторизация]])
    
- 📡 Обеспечивает взаимодействие компонентов ([[Scheduler|Scheduler]], [[Controller Manager|Controller Manager]], [[kubelet|kubelet]])
    

---

### 📌 **Пример работы**

1. Администратор выполняет команду:
    

```bash
kubectl create deployment my-app --image=my-app:1.0
```

2. [[kubectl|kubectl]] отправляет запрос в [[API Server|API Server]]
    
3. API Server:
    
    - проверяет синтаксис и права доступа
        
    - записывает описание Deployment в [[etcd|etcd]]
        
    - уведомляет [[Controller Manager|Controller Manager]] и [[Scheduler|Scheduler]]
        

---

### 🧠 **Особенности и подводные камни**

- ❗ Отказ API Server делает управление кластером невозможным
    
- 🔐 Требует настройки [[TLS|TLS]] для защищённых соединений
    
- 🏎 Может стать узким местом при большом количестве запросов
    
- 📦 Работает по принципу «thin layer»: сам не выполняет операции, а только координирует
    

---

### 📊 **Архитектура**

```
   Пользователь / kubectl
             |
             v
       +-------------+
       |  API Server |
       +-------------+
             |
    +--------+---------+
    |                  |
  etcd          Другие компоненты
 (хранение)   (Scheduler, Controller Manager, kubelet)
```

---

### 🎯 **Типичные вопросы на собеседовании**

1. ❓ Что делает API Server?  
    👉 Принимает запросы, проверяет их, сохраняет данные в [[etcd|etcd]] и передаёт другим компонентам.
    
2. ❓ Можно ли обойти API Server?  
    👉 Нет, это единственная точка входа в [[Cluster|кластер]].
    
3. ❓ Кто взаимодействует с API Server?  
    👉 [[kubectl|kubectl]], [[Scheduler|Scheduler]], [[Controller Manager|Controller Manager]], [[kubelet|kubelet]] и внешние клиенты.
    
4. ❓ Где хранится состояние кластера?  
    👉 В [[etcd|etcd]], но доступ к нему всегда идёт через API Server.
    

---

### 🔗 **Связанные термины**

- [[Kubernetes|Kubernetes]]
    
- [[etcd|etcd]]
    
- [[Scheduler|Scheduler]]
    
- [[Controller Manager|Controller Manager]]
    
- [[kubectl|kubectl]]
    
- [[RBAC|RBAC]]
    

---

### 🏷 **Теги**

#kubernetes #api #cloud #infrastructure

---