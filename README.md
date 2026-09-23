# Homework #10 — n8n: сравнение CSV и JSON

Workflow получает календарь России за 2022 год из двух источников:

- CSV: http://xmlcalendar.ru/data/ru/2022/calendar.csv
- JSON: http://xmlcalendar.ru/data/ru/2022/calendar.json

Затем workflow:
1. Загружает CSV.
2. Загружает JSON.
3. Объединяет результаты.
4. Разбирает CSV.
5. Сравнивает год, 12 месяцев и статистику рабочих/выходных дней.
6. Возвращает `identical: true`, если общая информация совпадает.

## Результат

При совпадении:

```json
{
  "identical": true,
  "message": "CSV и JSON содержат идентичные общие данные календаря.",
  "differences": []
}
```

## Импорт в n8n

```text
https://github.com/0ops-null/n8n-workflow/raw/refs/heads/main/worflow.json
```

В n8n выберите импорт workflow из URL и вставьте Raw URL.

> Важно: CSV и JSON имеют разную структуру. Поэтому workflow сравнивает общие данные, представленные в обоих форматах: год, дни по 12 месяцам и статистику. JSON дополнительно содержит `transitions`, которых в CSV нет.

