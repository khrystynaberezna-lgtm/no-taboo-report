# NO TABOO — автоматичний звіт Bolt Food UA

Пакет для автооновлюваного звіту партнера **NO TABOO**.
Побудований за зразком rodynna-kovbaska-report (шаблон Hop Hey + блок «Активація мережі»).

## Параметри звіту

| Параметр | Значення |
|----------|----------|
| `PARTNER_NAME` (group_name у Databricks) | `NO TABOO` (40 закладів) |
| `PARTNER_DISPLAY` (заголовок) | `NO TABOO` |
| `DATA_START` | `2025-01-01` |
| Initials (лого) | `NT` |
| Slug публічного репо / Pages | `no-taboo-report` |
| Live URL | https://khrystynaberezna-lgtm.github.io/no-taboo-report/ |

## Файли

```
NO TABOO/
├── generate_report.py                 # тягне дані з Databricks → index.html
├── template.html                      # HTML-шаблон (брендинг Bolt, Chart.js)
├── publish.sh                         # генерація + git push у публічний репо
├── requirements.txt                   # databricks-sql-connector
├── .env                               # конфіг + Databricks PAT (НЕ в git)
├── .env.example                       # шаблон конфігу
├── .gitignore                         # .env та report_data.json не комітяться
├── cursor-rule.mdc                    # правило Cursor для цього звіту
├── README.md                          # цей файл
└── .github/workflows/update-report.yml  # автооновлення щопонеділка 05:00 UTC
```

## Оновлення

- **Автоматично**: GitHub Actions щопонеділка о 05:00 UTC (08:00 Київ).
- **Вручну**: репо → Actions → «Оновлення звіту NO TABOO» → Run workflow.
- **Локально**: `cd "NO TABOO" && ./publish.sh`.

> Databricks PAT живе 90 днів — після прострочення згенеруй новий і онови `.env`
> та секрет `DATABRICKS_TOKEN` у репо.
