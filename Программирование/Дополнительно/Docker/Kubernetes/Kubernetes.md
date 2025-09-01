# 📄 **Kubernetes**

### 📝 **Что это и зачем нужно**

Kubernetes — это система оркестрации [[Container|контейнеров]], которая управляет их запуском, масштабированием и обновлением.  
Используется для автоматизации работы [[Microservices|микросервисов]] и управления [[Cluster|кластерами]] [[Node|узлов]].  
Главная цель: упростить развертывание и эксплуатацию приложений в [[Cloud|облаке]] или на собственных серверах.

Ключевыми компонентами Kubernetes являются [[API Server|API Server]], [[Controller Manager|Controller Manager]], [[Scheduler|Scheduler]] и [[etcd|etcd]], которые вместе обеспечивают работу всего кластера.

---

### ⚡ **Основные возможности**

- 📍 Масштабирование — автоматическое увеличение или уменьшение количества [[Pod|подов]]
    
- 🔑 Балансировка нагрузки — распределение трафика между [[Service|сервисами]]
    
- ➕ Автоматическое восстановление — перезапуск упавших [[Container|контейнеров]] с помощью [[Controller Manager|Controller Manager]]
    
- ➖ Сложность настройки — требуется знание [[YAML|YAML]], понимание работы [[API Server|API Server]] и архитектуры [[Cluster|кластера]]
    
- 🔄 Обновления без простоя — пошаговое развертывание новых версий ([[Rolling update|rolling update]]) под контролем [[Scheduler|Scheduler]]
    
- 🚫 Ограничения — требует ресурсов и правильной конфигурации [[Network|сети]], а также надежной работы [[etcd|etcd]]
    

---

### 📌 **Пример кода**

```yaml
# Определяем Deployment для приложения
apiVersion: apps/v1  # Указываем версию API
kind: Deployment  # Тип ресурса — Deployment
metadata:
  name: my-app  # Имя деплоймента
spec:
  replicas: 3  # Количество копий приложения
  selector:
    matchLabels:
      app: my-app  # Метка для выбора подов
  template:
    metadata:
      labels:
        app: my-app  # Метка для пода
    spec:
      containers:
      - name: my-app-container  # Имя контейнера
        image: my-app:1.0  # Образ контейнера
        ports:
        - containerPort: 8080  # Порт внутри контейнера
```

---

### 🧠 **Особенности и подводные камни**

- ❗ [[API Server|API Server]] — единственная точка входа в [[Cluster|кластер]], и его отказ делает управление невозможным
    
- 📦 Все конфигурации управляются через [[YAML|YAML]], обрабатываются [[API Server|API Server]] и сохраняются в [[etcd|etcd]]
    
- 🔍 [[Scheduler|Scheduler]] может неправильно распределять нагрузку, если ресурсы [[Node|узлов]] заданы некорректно
    
- 🏎 [[Controller Manager|Controller Manager]] автоматически создаёт новые [[Pod|поды]], но при ошибках конфигурации возможен бесконечный цикл пересозданий
    

---

### 📊 **Визуальное представление**

```
        +--------------------+
        |   API Server       |  <-- принимает запросы kubectl
        +--------------------+
                 |
        +--------------------+
        |   etcd             |  <-- хранение состояния кластера
        +--------------------+
                 |
   +-------------+--------------+
   |                            |
+---------+              +--------------+
|Scheduler|              |Controller Mgr|
+---------+              +--------------+
     |                          |
   распределяет           управляет Pod,
   поды по узлам           ReplicaSet и т.д.
```

---

### 💼 **Использование на практике**

1. **Развертывание микросервиса**
    
    ```yaml
    kind: Deployment  # Описываем деплоймент
    replicas: 2  # Две копии сервиса
    ```
    
    ✅ [[Controller Manager|Controller Manager]] будет следить, чтобы всегда было 2 работающих пода.
    
2. **Создание сервиса для доступа**
    
    ```yaml
    kind: Service  # Определяем сервис
    spec:
      type: LoadBalancer  # Тип — балансировщик нагрузки
      ports:
      - port: 80  # Внешний порт
        targetPort: 8080  # Порт контейнера
    ```
    
    ✅ [[API Server|API Server]] применит манифест, сохранив его в [[etcd|etcd]], а [[Scheduler|Scheduler]] обеспечит работу нужных подов.
    
3. **Горизонтальное автоскейлинг**
    
    ```yaml
    kind: HorizontalPodAutoscaler  # Определяем HPA
    spec:
      minReplicas: 1  # Минимум подов
      maxReplicas: 10  # Максимум подов
      targetCPUUtilizationPercentage: 50  # Целевой уровень загрузки
    ```
    
    ✅ [[Controller Manager|Controller Manager]] будет автоматически увеличивать или уменьшать количество подов.
    
4. **Обновление приложения**
    
    ```yaml
    spec:
      strategy:
        type: RollingUpdate  # Обновление без простоя
    ```
    
    ✅ [[Scheduler|Scheduler]] постепенно заменяет старые поды на новые.
    
5. **Использование ConfigMap**
    
    ```yaml
    kind: ConfigMap  # Определяем ConfigMap
    data:
      APP_MODE: "production"  # Храним конфигурацию
    ```
    
    ✅ [[API Server|API Server]] применяет изменения, сохраняя их в [[etcd|etcd]].
    

---

### 🎯 **Типичные вопросы на собеседовании (с ответами)**

1. ❓ Что такое Kubernetes?  
    👉 Это система оркестрации [[Container|контейнеров]], управляющая их запуском, масштабированием и обновлением.
    
2. ❓ Что такое Pod?  
    👉 [[Pod|Под]] — минимальная единица в Kubernetes, содержащая один или несколько [[Container|контейнеров]].
    
3. ❓ Чем Deployment отличается от StatefulSet?  
    👉 [[Deployment|Deployment]] управляет stateless-приложениями, [[StatefulSet|StatefulSet]] — stateful.
    
4. ❓ Что такое Service в Kubernetes?  
    👉 [[Service|Сервис]] — объект для доступа к [[Pod|подам]], скрывающий их динамическую природу.
    
5. ❓ Что делает kube-scheduler?  
    👉 [[Scheduler|Scheduler]] распределяет [[Pod|поды]] по [[Node|узлам]] кластера.
    
6. ❓ Что такое kubelet?  
    👉 Агент, запущенный на каждом [[Node|узле]], управляющий [[Container|контейнерами]].
    
7. ❓ Как работает ConfigMap?  
    👉 Хранит конфигурацию в виде [[Key|ключ-значение]] для использования в [[Pod|подах]].
    
8. ❓ Что такое Secret?  
    👉 Объект для хранения чувствительных данных ([[Password|паролей]], [[Token|токенов]]).
    
9. ❓ Что делает etcd?  
    👉 [[etcd|etcd]] хранит текущее состояние и конфигурацию всего [[Cluster|кластера]].
    
10. ❓ Что такое Ingress?  
    👉 [[Ingress|Ingress]] управляет внешним доступом к [[Service|сервисам]].
    
11. ❓ Как работает автоскейлинг?  
    👉 [[HorizontalPodAutoscaler|HPA]] регулирует количество [[Pod|подов]] в зависимости от нагрузки.
    
12. ❓ Чем отличается ReplicaSet от Deployment?  
    👉 [[ReplicaSet|ReplicaSet]] управляет копиями подов, [[Deployment|Deployment]] добавляет стратегию обновлений.
    
13. ❓ Что такое namespace?  
    👉 [[Namespace|Namespace]] — логическая изоляция ресурсов в кластере.
    
14. ❓ Какие типы сервисов бывают?  
    👉 [[ClusterIP|ClusterIP]], [[NodePort|NodePort]], [[LoadBalancer|LoadBalancer]].
    
15. ❓ Чем отличается StatefulSet от DaemonSet?  
    👉 [[StatefulSet|StatefulSet]] управляет stateful-приложениями, [[DaemonSet|DaemonSet]] — подами, работающими на каждом [[Node|узле]].
    
16. ❓ Что такое Helm?  
    👉 [[Helm|Helm]] — менеджер пакетов для Kubernetes.
    
17. ❓ Что делает kubectl?  
    👉 [[kubectl|kubectl]] — CLI для управления Kubernetes.
    
18. ❓ Что значит self-healing в Kubernetes?  
    👉 Автоматический перезапуск упавших [[Pod|подов]].
    
19. ❓ Что такое PersistentVolume?  
    👉 [[PersistentVolume|PV]] — объект для управления постоянным [[Storage|хранилищем]].
    
20. ❓ Как обновить приложение без простоя?  
    👉 Использовать стратегию [[Rolling update|Rolling update]] в [[Deployment|Deployment]].
    
21. ❓ Что делает API Server?  
    👉 [[API Server|API Server]] — центральный компонент, принимающий все запросы к [[Cluster|кластеру]] и взаимодействующий с [[etcd|etcd]].
    
22. ❓ Что такое Controller Manager?  
    👉 [[Controller Manager|Controller Manager]] запускает контроллеры, которые следят за состоянием [[Cluster|кластера]] и автоматически создают или удаляют [[Pod|поды]].
    

---

### 🔗 **Связанные термины**

- [[Container|Контейнер]]
    
- [[Pod|Под]]
    
- [[Deployment|Deployment]]
    
- [[Service|Сервис]]
    
- [[StatefulSet|StatefulSet]]
    
- [[Helm|Helm]]
    
- [[Namespace|Namespace]]
    
- [[Ingress|Ingress]]
    
- [[API Server|API Server]]
    
- [[Controller Manager|Controller Manager]]
    
- [[Scheduler|Scheduler]]
    
- [[etcd|etcd]]
    

---

### 🏷 **Теги**

#java #frameworks #interview #datastructures