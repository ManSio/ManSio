<div align="center">

# Михаил / ManSio

**Инженер-практик.** Техник-строитель (ПГС) по образованию — программы строю так же, как строят конструкции: с допусками, актами освидетельствования и следом в документах.

[🇺🇸 English version](README.md) · [Живое портфолио](https://mansio.github.io/MSPortfolio/) · [Статьи](https://dev.to/mansio) · [LinkedIn](https://www.linkedin.com/in/ManSio)

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white&labelColor=111418)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white&labelColor=111418)
![MCP](https://img.shields.io/badge/MCP-00d9ff?style=flat-square&labelColor=111418)
![SQLite FTS5](https://img.shields.io/badge/SQLite_FTS5-003B57?style=flat-square&logo=sqlite&logoColor=white&labelColor=111418)
![tree-sitter](https://img.shields.io/badge/tree--sitter-2f3b45?style=flat-square&labelColor=111418)
![Cloudflare Workers](https://img.shields.io/badge/Workers-F38020?style=flat-square&logo=cloudflare&logoColor=white&labelColor=111418)

</div>

## Что я строю

| Проект | Что это | Состояние |
|---|---|---|
| [**mscodebase-intelligence**](https://github.com/ManSio/mscodebase-intelligence) | Локальный code intelligence поверх MCP: BM25/FTS5 + AST-граф, impact analysis, память проекта, безопасные записи. Text-first по умолчанию, dense — опционально. Работает с OpenCode и Zed. | `v3.5.0` · Python 3.14 · MIT |
| [**MSPortfolio**](https://github.com/ManSio/MSPortfolio) | Портфолио, которое одновременно MCP-сервер и движок доказательств: каждое утверждение агента прослеживается до записи в данных, каждый ответ чата показывает сделанные вызовы инструментов. | live · GitHub Pages + Workers |
| [**gemma_agent**](https://github.com/ManSio/gemma_agent) | Telegram-ассистент для узкого круга — память, маршрутизация, инструменты только когда нужны. | Python |

## Цифры и их границы

Каждое число ниже опубликовано вместе с командой, которая его пересчитывает, —
в [`docs/FACTS.md`](https://github.com/ManSio/mscodebase-intelligence/blob/main/docs/FACTS.md).
Числа, которые не подтвердились, тоже опубликованы.

| Утверждение | Значение | Граница |
|---|---:|---|
| Качество поиска по коду, `hit@5` | **0.900** | панель из 48 запросов, замер 2026-10-25 — снимок, не пересчитывается на каждый коммит |
| Быстрый режим, `hit@5` | **0.729** | та же панель и дата |
| Инструментов зарегистрировано / видно по умолчанию | **69 / 17** | число зависит от `MSCODEBASE_MCP_PROFILE` |
| Грамматик языков | **31** | глубина графа зависит от грамматики |
| Локализация коммитов на внешних репозиториях | **12/25** и **17/40** | `grep` на тех же корпусах дал 19/25 и 20/40 — он выигрывает, и это записано |

Ни заявленных 95%, ни «лучше RAG», ни «лучше grep»: измеренные числа этого не подтвердили.

## Паспорт

Эти числа — записи, а не прилагательные. Семь листов A4 сдают репозиторий так,
как сдают объект: титул с ведомостью состава, замеры с правилом устаревания,
журнал работ с датами, акты скрытых работ (ADR), условия эксплуатации, реестр
брака, где красный оставлен только открытому, и акт приёмки.

<img src="https://raw.githubusercontent.com/ManSio/MSPortfolio/main/docs/passport/passport-sheet2.ru.svg" width="860" alt="Паспорт качества, лист 2: протоколы испытаний">

<details>
<summary><b>Лист 6 — реестр брака</b> (единственный лист с красным)</summary>

<img src="https://raw.githubusercontent.com/ManSio/MSPortfolio/main/docs/passport/passport-sheet6.ru.svg" width="860" alt="Паспорт качества, лист 6: реестр брака">

</details>

[Все семь листов, RU и EN →](https://github.com/ManSio/MSPortfolio/tree/main/docs/passport)

[Все четыре листа, RU и EN →](https://github.com/ManSio/MSPortfolio/tree/main/docs/passport)

## Как я работаю

- **Отрицательный результат — тоже результат.** Четыре реранкера (MiniLM, BGE-base, BGE-M3, Qwen3-0.6B) проверены и отклонены: BGE-base уронил `hit@1` с 0.688 до 0.625 при 3.1 с на запрос, Qwen3-0.6B отвечал 29–55 с на пилоте из 16 запросов с `hit@1` 0.500. Отказ остаётся в журнале, а не удаляется.
- **Тест, который не умеет падать, — не тест.** Перед сдачей фикса реализация намеренно ломается, чтобы убедиться, что тест краснеет.
- **Живая документация.** Код и его документация меняются в одном коммите; устаревшее число — это баг.
- **Принцип «Тумблера».** Технология не диктует архитектуру: база, модель и транспорт — сменные части.

## Статьи

- [**PageRank против RAG на реальной кодовой базе**](https://dev.to/mansio/i-measured-pagerank-token-savings-on-a-real-codebase-the-result-will-surprise-you-5bnj) — семантический и структурный поиск, с двумя раундами самокоррекции метрик.
- [**Я попросил одну ИИ проверить факты в аудите другой**](https://dev.to/mansio/i-asked-one-ai-to-fact-check-another-ais-audit-of-my-own-code-1ac3) — перекрёстная проверка против уверенных галлюцинаций в security-ревью.
- [**Тихий баг контаминации векторов**](https://dev.to/mansio/the-silent-vector-contamination-bug-why-your-concurrent-embeddings-might-be-lying-to-you-5fg7) — потокобезопасность и изоляция памяти при конкурентных эмбеддингах (OpenVINO).

## Спросить портфолио

Портфолио — это MCP-сервер, поэтому агент может интервьюировать его, а не скрапить:

```sh
claude mcp add --transport http msp-portfolio https://msp-portfolio.mansio-dev.workers.dev/mcp
```

Спрашивайте о проектах выше — оно отвечает через инструменты (`get_projects`, `analyze_stack`, `verify_claim`, `get_known_issues`), а не по наитию.

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=ManSio&show_icons=true&hide_title=true&bg_color=0d1117&title_color=00d9ff&text_color=c9d1d9&icon_color=00d9ff&border_color=30363d" alt="GitHub stats" height="150" />
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ManSio&layout=compact&hide_title=true&bg_color=0d1117&title_color=00d9ff&text_color=c9d1d9&border_color=30363d" alt="Top languages" height="150" />

</div>
