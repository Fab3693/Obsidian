### 📄 **Consumer**

**Простыми словами:** Consumer — это **получатель сообщений** в системе обмена данными (например, в [[Kafka]]). Он читает события из [[Topics]]ов, куда их отправил [[Producer]].

---

### 🧩 **Что делает Consumer**

- 📥 Подписывается на один или несколько топиков
    
- 📤 Получает сообщения от [[Broker]]
    
- ⚙️ Обрабатывает данные (сохраняет в БД, вызывает сервис, логирует и т.д.)
    
- 🔄 Может работать в группе (consumer group), чтобы делить нагрузку
    

---

### 📌 **Пример (Kafka Consumer)**

```java
consumer.subscribe(List.of("orders"));

while (true) {
    ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(100));
    for (ConsumerRecord<String, String> record : records) {
        System.out.println("Получено сообщение: " + record.value());
    }
}
```

📍 Здесь consumer читает сообщения из топика `orders` и выводит их в консоль.

---

### 🧠 **Особенности**

- Несколько consumer'ов в одной **consumer group** делят между собой сообщения
    
- Kafka отслеживает, какие сообщения уже прочитаны каждым consumer'ом
    
- Поддерживает масштабирование и высокую производительность
    

---

### 🔗 **Связанные термины**

- [[Kafka]]
    
- [[Broker]]
    
- [[Producer]]
    
- [[Topics]]
    

---

#consumer #kafka #messaging #streaming #eventdriven #microservices