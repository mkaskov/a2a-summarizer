# A2A Summarizer Agent

Простой A2A-совместимый агент для суммаризации текста.

## Запуск

```bash
docker compose up --build
```


## Проверка

### 1. Проверка discovery endpoint
```bash
curl http://localhost:8080/.well-known/agent.json
```

### 2. Проверка суммаризации

Запрос

```bash
curl -X POST "http://localhost:8080/a2a/summarize" \
  -H "Content-Type: application/json" \
  -d '{"text":"Это первое предложение. Второе предложение важно. Третье предложение содержит детали. Четвертое — заключение.", "max_sentences":2}'
```

Ответ

```json
{
  "summary": "Второе предложение важно. Третье предложение содержит детали.",
  "sentences_selected": [
    "Второе предложение важно.",
    "Третье предложение содержит детали."
  ]
}
```