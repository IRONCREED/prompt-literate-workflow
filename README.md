# Prompt-Literate Workflow

Prompt-Literate Workflow (PLW) is an experimental method for using a large language model inside a literate engineering process.

It is not a `prompt -> code` shortcut.

The method treats an LLM as an executor or editor operating inside a human-defined structure, rather than as the default system architect. A prompt is an operation over a source and its contracts, not the source of truth itself. LLM-generated output remains a candidate artifact until it has passed review, deterministic validation, and traceable acceptance.

```text
human-authored literate plan
  → chunk contracts
  → bounded prompt
  → LLM-generated candidate
  → review
  → tests / smoke-check
  → TRACE
  → accepted update to canonical source
```

## Why This Exists

Traditional literate programming connects explanation, code, and generated artifacts through a structured source.

LLM-assisted development introduces a different problem: generation is probabilistic. A model can produce useful code, but its output cannot be treated as equivalent to a deterministic build step.

Prompt-Literate Workflow preserves the explanatory discipline of literate programming while explicitly separating:

* human-authored intent;
* contracts and acceptance criteria;
* bounded LLM operations;
* candidate output;
* deterministic validation;
* traceable acceptance.

## Core Principles

1. The source of truth is a human-authored literate plan.
2. The contract layer is mandatory between plan and generation.
3. A prompt is an operation over the plan and contracts, not a source.
4. Chat history is trace material, not a source.
5. LLM output is a candidate artifact, not an automatically accepted implementation.
6. The LLM may modify only explicitly permitted chunks.
7. Every generated chunk must have a contract before generation.
8. Every fillable chunk must have acceptance criteria.
9. One prompt run corresponds to one TRACE entry.
10. Generated code cannot be accepted without review and deterministic checks.
11. Manual edits must be reflected in the plan, contracts, or TRACE.
12. Local project rules must extend the core additively rather than silently override its invariants.

## Repository Navigation

```text
.
├── README.md
├── METHOD.en.md
├── METHOD.ru.md
├── CONTRACTS.schema.md
├── SCENARIOS.schema.md
└── TRACE.schema.md
```

### Start Here

* [Method description in English](METHOD.en.md)
* [Описание метода на русском языке](METHOD.ru.md)
* [Chunk-contract schema](CONTRACTS.schema.md)
* [Validation-scenario schema](SCENARIOS.schema.md)
* [TRACE schema](TRACE.schema.md)

## File Roles

* `*.plan.md` — canonical human-authored plan with named chunks, constraints, and intent;
* `CONTRACTS.md` — contract layer between plan and generation;
* `SCENARIOS.md` — acceptance and validation scenarios;
* `prompts/*.prompt.md` — bounded LLM operations over the plan and contracts;
* `generated/` — candidate generated artifacts before acceptance;
* `tests/validate-method.sh` — validation of the required method structure;
* `tests/smoke-check.*` — deterministic validation of accepted artifacts;
* `output.expected.*` — expected output markers or snapshots;
* `TRACE.md` — trace log for prompt runs, decisions, reviews, and acceptance or rejection.

## Minimal Workflow

1. Write or freeze the human-authored plan.
2. Define named chunks.
3. Add contracts for every LLM-fillable chunk.
4. Define scenarios and acceptance criteria.
5. Mark permitted generation points with `LLM-TODO`.
6. Run structural validation.
7. Execute a bounded prompt.
8. Accept only permitted chunk replacements.
9. Review the candidate output.
10. Run tests or smoke-checks.
11. Record the run, edits, checks, and decision in `TRACE.md`.
12. Update the canonical source only after acceptance.

## Boundary Status

Prompt-Literate Workflow is experimental.

It is not equivalent to deterministic literate workflows such as WEB, CWEB, noweb, Org Babel, Quarto, Jupyter, or R Markdown. Its deterministic layer consists of the human-authored plan, contracts, scenarios, tests, and trace. LLM output remains dependent on model, version, context, and execution mode.

The method was initially formulated in the review [*Literate Programming: Donald Knuth, WEB, and Contemporary Workflows*](https://github.com/Zhovten-Games/literate-programming) and refined through practical application to an independent project core.

## Use as a Template or Submodule

This repository is intentionally compact.

It can be used:

* as a GitHub template repository for a new PLW-based project;
* as a pinned Git submodule inside a larger repository;
* as a methodological reference accompanied by project-local additive extensions.

Project-specific rules should remain outside the universal core unless they have been separately generalised and intentionally promoted into the method.

<details>
<summary><strong>Русская версия</strong></summary>

# Prompt-Literate Workflow

Prompt-Literate Workflow (PLW) — экспериментальный метод использования большой языковой модели внутри literate-инженерного процесса.

Это не сокращённая схема `prompt -> code`.

Метод рассматривает LLM как исполнителя или редактора внутри структуры, заданной человеком, а не как архитектора по умолчанию. Промпт является операцией над источником и его контрактами, а не самостоятельным источником истины. Вывод LLM остаётся кандидатным артефактом до тех пор, пока не пройдёт review, детерминированную валидацию и трассируемую процедуру принятия.

```text
human-authored literate plan
  → chunk contracts
  → bounded prompt
  → LLM-generated candidate
  → review
  → tests / smoke-check
  → TRACE
  → accepted update to canonical source
```

## Зачем нужен этот метод

Классическое literate programming связывает объяснение, код и генерируемые артефакты через структурированный источник.

LLM-assisted разработка добавляет новую проблему: генерация носит вероятностный характер. Модель может создавать полезный код, но её вывод нельзя считать эквивалентом детерминированного этапа сборки.

Prompt-Literate Workflow сохраняет объяснительную дисциплину literate programming и явно разделяет:

* human-authored замысел;
* контракты и критерии принятия;
* ограниченные операции LLM;
* кандидатный вывод;
* детерминированную валидацию;
* трассируемое принятие.

## Основные правила

1. Источник истины — human-authored literate plan.
2. Контрактный слой обязателен между планом и генерацией.
3. Промпт — операция над планом и контрактами, а не источник истины.
4. История чата — материал трассировки, а не источник истины.
5. Вывод LLM — кандидатный артефакт, а не автоматически принятая реализация.
6. LLM может изменять только явно разрешённые чанки.
7. Каждый генерируемый чанк должен иметь контракт до запуска генерации.
8. Каждый заполняемый чанк должен иметь критерии принятия.
9. Один запуск промпта соответствует одной записи в TRACE.
10. Сгенерированный код не может быть принят без review и детерминированных проверок.
11. Ручные правки должны быть отражены в плане, контрактах или TRACE.
12. Локальные правила проекта должны дополнять ядро, а не молча переопределять его инварианты.

## Навигация по репозиторию

```text
.
├── README.md
├── METHOD.en.md
├── METHOD.ru.md
├── CONTRACTS.schema.md
├── SCENARIOS.schema.md
└── TRACE.schema.md
```

### Начать отсюда

* [Описание метода на английском языке](METHOD.en.md)
* [Описание метода на русском языке](METHOD.ru.md)
* [Схема контрактов чанков](CONTRACTS.schema.md)
* [Схема сценариев валидации](SCENARIOS.schema.md)
* [Схема TRACE](TRACE.schema.md)

## Роли файлов

* `*.plan.md` — канонический human-authored план с именованными чанками, ограничениями и зафиксированным замыслом;
* `CONTRACTS.md` — контрактный слой между планом и генерацией;
* `SCENARIOS.md` — сценарии принятия и валидации;
* `prompts/*.prompt.md` — ограниченные операции LLM над планом и контрактами;
* `generated/` — кандидатные сгенерированные артефакты до их принятия;
* `tests/validate-method.sh` — проверка обязательной структуры метода;
* `tests/smoke-check.*` — детерминированная проверка принятых артефактов;
* `output.expected.*` — ожидаемые маркеры вывода или snapshots;
* `TRACE.md` — журнал запусков промптов, решений, review, принятия и отклонения изменений.

## Минимальный процесс

1. Написать или зафиксировать human-authored plan.
2. Определить именованные чанки.
3. Добавить контракты для всех LLM-fillable чанков.
4. Определить сценарии и критерии принятия.
5. Пометить разрешённые точки генерации через `LLM-TODO`.
6. Запустить структурную валидацию.
7. Выполнить bounded prompt.
8. Принять только разрешённые замены чанков.
9. Выполнить review кандидатного вывода.
10. Запустить tests или smoke-check.
11. Зафиксировать запуск, правки, проверки и решение в `TRACE.md`.
12. Обновить canonical source только после принятия.

## Граничный статус

Prompt-Literate Workflow остаётся экспериментальным методом.

Он не эквивалентен детерминированным literate-workflows: WEB, CWEB, noweb, Org Babel, Quarto, Jupyter или R Markdown. Детерминированный слой метода образуют human-authored plan, contracts, scenarios, tests и trace. Вывод LLM остаётся зависимым от модели, версии, контекста и режима выполнения.

Метод был первоначально сформулирован в обзоре [*Literate Programming: Donald Knuth, WEB, and Contemporary Workflows*](https://github.com/Zhovten-Games/literate-programming), а затем уточнён при практическом применении к независимому ядру проекта.

## Использование как template repository или submodule

Репозиторий намеренно остаётся компактным.

Его можно использовать:

* как GitHub template repository для нового PLW-проекта;
* как pinned Git submodule внутри более крупного репозитория;
* как методологическую основу с локальными additive-расширениями проекта.

Специфические правила проекта должны оставаться за пределами универсального ядра, пока они не были отдельно обобщены и намеренно перенесены в основу метода.
</details>