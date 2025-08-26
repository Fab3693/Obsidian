### 📄 **Logstash**

**Простыми словами:** Logstash — это инструмент для **сбора, обработки и передачи логов** (и любых данных). Он помогает централизовать данные из разных источников и отправить их, например, в [[Elasticsearch]].

---

### 🧩 **Что делает Logstash**

- 📥 Сбор данных из разных источников (файлы логов, БД, очереди, API)
    
- 🔄 Обработка: фильтрация, парсинг, преобразование
    
- 📤 Отправка данных в разные хранилища (чаще всего в [[Elasticsearch]])
    

---

### 📌 **Пример конфигурации (logstash.conf)**

```conf
input {
  file {
    path => "/var/log/app.log"
  }
}

filter {
  grok {
    match => { "message" => "%{TIMESTAMP_ISO8601:timestamp} %{LOGLEVEL:level} %{GREEDYDATA:msg}" }
  }
}

output {
  elasticsearch {
    hosts => ["http://localhost:9200"]
    index => "app-logs"
  }
}
```

📍 Здесь Logstash читает файл логов, разбирает каждую строку и сохраняет её в Elasticsearch.

---

### 🧠 **Особенности**

- Часть стека **ELK** (Elasticsearch + Logstash + Kibana)
    
- Очень гибкая система фильтров для обработки данных
    
- Работает с JSON, CSV, XML, syslog и многими другими форматами
    
- Может использоваться не только для логов, но и для ETL-процессов (извлечение → трансформация → загрузка данных)
    

---

### 🔗 **Связанные термины**

- [[Elasticsearch]]
    
- [[Kibana]]
    
- [[Логирование]]
    
- [[JSON]]
    

---

#logstash #elk #logging #elasticsearch #bigdata #etl