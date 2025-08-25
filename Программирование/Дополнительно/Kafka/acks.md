### 📄 **acks (Acknowledgments) в Kafka**

**Простыми словами:** `acks` — это настройка [[Producer]] в [[Kafka]], которая определяет, **сколько подтверждений от [[Broker]] требуется**, чтобы считать сообщение успешно отправленным.

---

### 🧩 **Варианты значения acks**

- `acks=0` — Producer **не ждёт подтверждения** от брокера. Быстро, но нет гарантии доставки.
    
- `acks=1` — Producer ждёт подтверждения от **лидера партиции**. Сообщение считается доставленным, когда лидер записал его.
    
- `acks=all` или `acks=-1` — Producer ждёт подтверждения от **всех реплик** партиции. Максимальная надёжность доставки.
    

---

### 📌 **Пример настройки Producer**

```java
Properties props = new Properties();
props.put("bootstrap.servers", "localhost:9092");
props.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");
props.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");
props.put("acks", "all");

KafkaProducer<String, String> producer = new KafkaProducer<>(props);
```

📍 Здесь Producer ждёт подтверждения от всех реплик перед подтверждением отправки сообщения.

---

### 🧠 **Особенности**

- Влияет на **надёжность и скорость** отправки сообщений
    
- `acks=0` — максимально быстро, но ненадёжно
    
- `acks=all` — максимально безопасно, но чуть медленнее
    
- Настройка полезна для балансировки между производительностью и безопасностью данных
    

---

### 🔗 **Связанные термины**

- [[Kafka]]
    
- [[Producer]]
    
- [[Broker]]
    
- [[Partitions|партиция]]
    
- [[Replication]]
    

---

#kafka #acks #producer #broker #messaging #streaming #microservices