# 📄 **Controller Manager**

### 📝 **Что это и зачем нужно**

**Controller Manager** — это компонент [[Kubernetes|Kubernetes]], который управляет контроллерами, отвечающими за поддержание желаемого состояния объектов в кластере.  
Он взаимодействует с [[API Server|API Server]] и сравнивает фактическое состояние ресурсов с описанным в [[YAML|YAML]]-манифестах.  
Главная цель: автоматизация управления ресурсами, чтобы система сама исправляла отклонения.

---

### ⚡ **Основные задачи**

- 📍 Управление контроллерами ([[Deployment|Deployment Controller]], [[ReplicaSet|ReplicaSet Controller]], [[Node|Node Controller]] и др.)
    
- 🔄 Слежение за изменениями в [[etcd|etcd]] через [[API Server|API Server]]
    
- ⚖ Обеспечение соответствия текущего состояния и желаемого описания
    
- 🚦 Реакция на события (например, создание [[Pod|Pod]] или сбой [[Node|узла]])
    
- 🧩 Поддержка работы нескольких контроллеров одновременно
    

---

### 📌 **Пример работы**

1. Администратор описывает в манифесте [[Deployment|Deployment]]:
    
    ```yaml
    replicas: 3
    ```
    
2. [[API Server|API Server]] сохраняет данные в [[etcd|etcd]]
    
3. **Controller Manager** проверяет, сколько [[Pod|Pod]] реально запущено
    
4. Если, например, запущено только 2 [[Pod|Pod]], Controller Manager создаёт ещё один
    

---

### 🧠 **Особенности и подводные камни**

- ❗ Если Controller Manager не работает, кластер перестаёт автоматически восстанавливаться
    
- 📦 Работает с помощью цикла «наблюдай — сравнивай — исправляй»
    
- 🔍 Не взаимодействует напрямую с [[Node|узлами]], а делает всё через [[API Server|API Server]]
    
- 🏎 При большом количестве ресурсов нагрузка на Controller Manager возрастает
    

---

### 📊 **Архитектура**

```
+----------------+
| API Server     |
+--------+-------+
         |
         v
+----------------+
| Controller     |
| Manager        |
+---+---+---+---+
    |   |   | 
    v   v   v
 ReplicaSet   Node   Deployment
 Controller   Controller   Controller
```

---

### 🎯 **Типичные вопросы на собеседовании**

1. ❓ Что делает Controller Manager?  
    👉 Управляет контроллерами, которые поддерживают желаемое состояние объектов [[Kubernetes|Kubernetes]].
    
2. ❓ Какие бывают контроллеры?  
    👉 [[Deployment|Deployment Controller]], [[ReplicaSet|ReplicaSet Controller]], [[Node|Node Controller]], [[Job|Job Controller]] и др.
    
3. ❓ Как Controller Manager узнаёт о событиях?  
    👉 Через [[API Server|API Server]], который читает и пишет данные в [[etcd|etcd]].
    
4. ❓ Может ли работать несколько Controller Manager?  
    👉 Обычно запускается один процесс, но он содержит много разных контроллеров внутри.
    

---

### 🔗 **Связанные термины**

- [[Kubernetes|Kubernetes]]
    
- [[API Server|API Server]]
    
- [[etcd|etcd]]
    
- [[Scheduler|Scheduler]]
    
- [[Deployment|Deployment]]
    
- [[ReplicaSet|ReplicaSet]]
    

---

### 🏷 **Теги**

#kubernetes #controller #cloud #infrastructure