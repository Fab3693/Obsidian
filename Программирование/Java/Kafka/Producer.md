### 📄 **Producer**

**Простыми словами:** Producer — это **отправитель сообщений** в системе обмена данными (например, в [[Kafka]]). Он публикует события или данные в определённый [[Topics]], откуда их потом читают [[Consumer]].

---

### 🧩 **Что делает Producer**

- ✍️ Создаёт сообщение (например, "Order #123 created")
    
- 📤 Отправляет его в топик Kafka
    
- ⚡ Работает с высокой скоростью и асинхронно
    
- 🎯 Может сам выбирать партицию для записи или доверить это Kafka
    

---

### 📌 **Пример (Kafka Producer)**

```java
ProducerRecord<String, String> record =
        new ProducerRecord<>("orders", "Order #123 created");

producer.send(record);
```

📍 Здесь producer отправляет строку `"Order #123 created"` в топик `orders`.

---

### 🧠 **Особенности**

- Producer'ов может быть много, все они пишут в один или разные топики
    
- Сообщения не теряются: Kafka гарантирует их сохранность
    
- Можно настроить режим: ждать подтверждение от брокера или нет (acknowledgment)
    

---

### 🔗 **Связанные термины**

- [[Kafka]]
    
- [[Broker]]
    
- [[Consumer]]
    
- [[Topics]]
    

---

#producer #kafka #messaging #streaming #eventdriven #microservices