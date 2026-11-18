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
├── methodology/
│   ├── METHOD.en.md
│   ├── METHOD.ru.md
│   ├── METHOD.uk.md
│   └── METHOD.be.md
├── schemas/
├── scripts/validate-project.py
├── starter/
└── integrations/code-constitution/
```

### Start Here

* [Method description in English](methodology/METHOD.en.md)
* [Описание метода на русском языке](methodology/METHOD.ru.md)
* [Опис методу українською мовою](methodology/METHOD.uk.md)
* [Апісанне метаду па-беларуску](methodology/METHOD.be.md)
* [Chunk-contract schema](schemas/CONTRACTS.schema.md)
* [Validation-scenario schema](schemas/SCENARIOS.schema.md)
* [TRACE phase 0 schema](schemas/TRACE.phase-0.schema.md)
* [TRACE phase 1 schema](schemas/TRACE.phase-1.schema.md)

## File Roles

* `*.plan.md` — canonical human-authored plan with named chunks, constraints, and intent;
* `CONTRACTS.md` — contract layer between plan and generation;
* `SCENARIOS.md` — acceptance and validation scenarios;
* `prompts/*.prompt.md` — bounded LLM operations over the plan and contracts;
* `generated/` — candidate generated artifacts before acceptance;
* `scripts/validate-project.py` — validation of the required method structure;
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

## Optional Integrations

The [Code Constitution integration kit](integrations/code-constitution/README.md) combines PLW with a separately adopted constitutional and legislative project order. The governance corpus remains authoritative for powers, rules, and acceptance; the human-authored PLW plan remains authoritative for the intent and bounded structure of a concrete operation. Both upstream revisions are pinned, conflicts stop the run, and LLM output remains a candidate until deterministic checks and authorised human acceptance.

## Use as a Template or Submodule

This repository is intentionally compact.

It can be used:

* as a GitHub template repository for a new PLW-based project;
* as a pinned Git submodule inside a larger repository;
* as a methodological reference accompanied by project-local additive extensions.

Project-specific rules should remain outside the universal core unless they have been separately generalised and intentionally promoted into the method.

<details>
<summary><strong>Русская версия</strong></summary>

## Prompt-Literate Workflow

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
├── methodology/
│   ├── METHOD.en.md
│   ├── METHOD.ru.md
│   ├── METHOD.uk.md
│   └── METHOD.be.md
├── schemas/
├── scripts/validate-project.py
├── starter/
└── integrations/code-constitution/
```

### Начать отсюда

* [Описание метода на английском языке](methodology/METHOD.en.md)
* [Описание метода на русском языке](methodology/METHOD.ru.md)
* [Опис методу українською мовою](methodology/METHOD.uk.md)
* [Апісанне метаду па-беларуску](methodology/METHOD.be.md)
* [Схема контрактов чанков](schemas/CONTRACTS.schema.md)
* [Схема сценариев валидации](schemas/SCENARIOS.schema.md)
* [Схема TRACE фазы 0](schemas/TRACE.phase-0.schema.md)
* [Схема TRACE фазы 1](schemas/TRACE.phase-1.schema.md)

## Роли файлов

* `*.plan.md` — канонический human-authored план с именованными чанками, ограничениями и зафиксированным замыслом;
* `CONTRACTS.md` — контрактный слой между планом и генерацией;
* `SCENARIOS.md` — сценарии принятия и валидации;
* `prompts/*.prompt.md` — ограниченные операции LLM над планом и контрактами;
* `generated/` — кандидатные сгенерированные артефакты до их принятия;
* `scripts/validate-project.py` — проверка обязательной структуры метода;
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

## Необязательные интеграции

[Комплект интеграции с «Конституцией кода»](integrations/code-constitution/README.md) соединяет PLW с отдельно принятой Конституцией, Учредительным профилем и производным Законодательством проекта. Нормативный корпус сохраняет силу в вопросах полномочий, правил и принятия; human-authored PLW-план сохраняет силу в отношении замысла и ограниченной структуры конкретной операции. Редакции обоих внешних источников закрепляются, конфликт останавливает запуск, а вывод LLM остаётся кандидатным артефактом до детерминированных проверок и человеческого принятия уполномоченным субъектом.

## Использование как template repository или submodule

Репозиторий намеренно остаётся компактным.

Его можно использовать:

* как GitHub template repository для нового PLW-проекта;
* как pinned Git submodule внутри более крупного репозитория;
* как методологическую основу с локальными additive-расширениями проекта.

Специфические правила проекта должны оставаться за пределами универсального ядра, пока они не были отдельно обобщены и намеренно перенесены в основу метода.
</details>

<details>
<summary><strong>Українська версія</strong></summary>

## Prompt-Literate Workflow

Prompt-Literate Workflow (PLW) — експериментальний метод використання великої мовної моделі в literate-інженерному процесі.

Це не скорочена схема `prompt -> code`.

Метод розглядає LLM як виконавця або редактора в межах структури, заданої людиною, а не як системного архітектора за замовчуванням. Промпт є операцією над джерелом та його контрактами, а не самостійним джерелом істини. Вивід LLM залишається артефактом-кандидатом, доки не пройде review, детерміновану валідацію та трасовану процедуру прийняття.

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

## Навіщо потрібен цей метод

Класичне literate programming пов’язує пояснення, код і згенеровані артефакти через структуроване джерело.

LLM-assisted розробка додає нову проблему: генерація має ймовірнісний характер. Модель може створювати корисний код, але її вивід не можна вважати еквівалентом детермінованого етапу збирання.

Prompt-Literate Workflow зберігає пояснювальну дисципліну literate programming і явно розділяє:

* human-authored задум;
* контракти та критерії прийняття;
* обмежені операції LLM;
* кандидатний вивід;
* детерміновану валідацію;
* трасоване прийняття.

## Основні правила

1. Джерело істини — human-authored literate plan.
2. Контрактний шар є обов’язковим між планом і генерацією.
3. Промпт — операція над планом і контрактами, а не джерело істини.
4. Історія чату — матеріал трасування, а не джерело істини.
5. Вивід LLM — артефакт-кандидат, а не автоматично прийнята реалізація.
6. LLM може змінювати лише явно дозволені чанки.
7. Кожен згенерований чанк повинен мати контракт до запуску генерації.
8. Кожен заповнюваний чанк повинен мати критерії прийняття.
9. Один запуск промпту відповідає одному запису в TRACE.
10. Згенерований код не можна прийняти без review і детермінованих перевірок.
11. Ручні правки повинні бути відображені в плані, контрактах або TRACE.
12. Локальні правила проєкту повинні доповнювати ядро, а не мовчазно перевизначати його інваріанти.

## Навігація репозиторієм

```text
.
├── README.md
├── methodology/
│   ├── METHOD.en.md
│   ├── METHOD.ru.md
│   ├── METHOD.uk.md
│   └── METHOD.be.md
├── schemas/
├── scripts/validate-project.py
├── starter/
└── integrations/code-constitution/
```

### Почати звідси

* [Опис методу англійською мовою](methodology/METHOD.en.md)
* [Опис методу українською мовою](methodology/METHOD.uk.md)
* [Опис методу російською мовою](methodology/METHOD.ru.md)
* [Схема контрактів чанків](schemas/CONTRACTS.schema.md)
* [Схема сценаріїв валідації](schemas/SCENARIOS.schema.md)
* [Схема TRACE фази 0](schemas/TRACE.phase-0.schema.md)
* [Схема TRACE фази 1](schemas/TRACE.phase-1.schema.md)

## Ролі файлів

* `*.plan.md` — канонічний human-authored план з іменованими чанками, обмеженнями та зафіксованим задумом;
* `CONTRACTS.md` — контрактний шар між планом і генерацією;
* `SCENARIOS.md` — сценарії прийняття та валідації;
* `prompts/*.prompt.md` — обмежені операції LLM над планом і контрактами;
* `generated/` — кандидатні згенеровані артефакти до їх прийняття;
* `scripts/validate-project.py` — перевірка обов’язкової структури методу;
* `tests/smoke-check.*` — детермінована перевірка прийнятих артефактів;
* `output.expected.*` — очікувані маркери виводу або snapshots;
* `TRACE.md` — журнал запусків промптів, рішень, review, прийняття та відхилення змін.

## Мінімальний процес

1. Написати або зафіксувати human-authored plan.
2. Визначити іменовані чанки.
3. Додати контракти для всіх LLM-fillable чанків.
4. Визначити сценарії та критерії прийняття.
5. Позначити дозволені точки генерації через `LLM-TODO`.
6. Запустити структурну валідацію.
7. Виконати bounded prompt.
8. Прийняти лише дозволені заміни чанків.
9. Виконати review кандидатного виводу.
10. Запустити tests або smoke-check.
11. Зафіксувати запуск, правки, перевірки та рішення в `TRACE.md`.
12. Оновити canonical source лише після прийняття.

## Граничний статус

Prompt-Literate Workflow залишається експериментальним методом.

Він не є еквівалентом детермінованих literate-workflows: WEB, CWEB, noweb, Org Babel, Quarto, Jupyter або R Markdown. Детермінований шар методу утворюють human-authored plan, contracts, scenarios, tests і trace. Вивід LLM залишається залежним від моделі, версії, контексту та режиму виконання.

Метод було спочатку сформульовано в огляді [*Literate Programming: Donald Knuth, WEB, and Contemporary Workflows*](https://github.com/Zhovten-Games/literate-programming), а згодом уточнено під час практичного застосування до незалежного ядра проєкту.

## Необов’язкові інтеграції

[Комплект інтеграції з «Конституцією коду»](integrations/code-constitution/README.md) поєднує PLW з окремо прийнятими Конституцією, Установчим профілем і похідним Законодавством проєкту. Нормативний корпус зберігає силу в питаннях повноважень, правил і прийняття; human-authored PLW-план зберігає силу щодо задуму та обмеженої структури конкретної операції. Редакції обох зовнішніх джерел закріплюються, конфлікт зупиняє запуск, а вивід LLM залишається артефактом-кандидатом до детермінованих перевірок і людського прийняття уповноваженим суб’єктом.

## Використання як template repository або submodule

Репозиторій навмисно залишається компактним.

Його можна використовувати:

* як GitHub template repository для нового PLW-проєкту;
* як pinned Git submodule у складі більшого репозиторію;
* як методологічну основу з локальними additive-розширеннями проєкту.

Специфічні правила проєкту повинні залишатися за межами універсального ядра, доки їх не буде окремо узагальнено та навмисно перенесено до основи методу.
</details>

<details>
<summary>Беларуская</summary>

Prompt-Literate Workflow (PLW) — эксперыментальны метад выкарыстання вялікай моўнай мадэлі ў літаратурным інжынерным працэсе.

Метад вызначае LLM як выканаўцу або рэдактара ў межах структуры, зададзенай чалавекам. Запыт выконвае аперацыю над крыніцай і яе кантрактамі. Вынік LLM захоўвае статус кандыдата да праверкі, дэтэрмінаванай валідацыі і прасочвальнага прыняцця.

```text
літаратурны план, створаны чалавекам
  → кантракты фрагментаў
  → абмежаваны запыт
  → кандыдат, згенераваны LLM
  → праверка
  → тэсты / smoke-check
  → TRACE
  → прынятае абнаўленне кананічнай крыніцы
```

## Навошта гэта патрэбна

Традыцыйнае літаратурнае праграмаванне звязвае тлумачэнне, код і вытворныя артэфакты праз структураваную крыніцу.

Распрацоўка з LLM дадае асобную праблему: генерацыя мае імавернасны характар. Мадэль можа ствараць карысны код, але яе вывад нельга прыраўноўваць да дэтэрмінаванага кроку зборкі.

Prompt-Literate Workflow захоўвае тлумачальную дысцыпліну літаратурнага праграмавання і яўна раздзяляе:

* намер, сфармуляваны чалавекам;
* кантракты і крытэрыі прыёмкі;
* абмежаваныя аперацыі LLM;
* вынік-кандыдат;
* дэтэрмінаваную валідацыю;
* прасочвальнае прыняцце.

## Асноўныя прынцыпы

1. Крыніцай ісціны служыць літаратурны план, створаны чалавекам.
2. Паміж планам і генерацыяй абавязковы пласт кантрактаў.
3. Запыт — аперацыя над планам і кантрактамі; ён не мае статусу крыніцы.
4. Гісторыя чата мае статус матэрыялу трасіроўкі.
5. Вывад LLM мае статус артэфакта-кандыдата і патрабуе асобнага прыняцця.
6. LLM можа змяняць толькі яўна дазволеныя фрагменты.
7. Кожны фрагмент для генерацыі LLM павінен атрымаць кантракт да генерацыі.
8. Кожны запаўняльны фрагмент павінен мець крытэрыі прыёмкі.
9. Адзін запуск запыту адпавядае аднаму запісу TRACE.
10. Прыняцце згенераванага кода патрабуе праверкі і дэтэрмінаваных кантрольных працэдур.
11. Ручныя змены адлюстроўваюцца ў плане, кантрактах або TRACE.
12. Лакальныя правілы праекта пашыраюць ядро дадаткова, захоўваючы яго інварыянты.

## Навігацыя па рэпазіторыі

```text
.
├── README.md
├── methodology/
│   ├── METHOD.en.md
│   ├── METHOD.ru.md
│   ├── METHOD.uk.md
│   └── METHOD.be.md
├── schemas/
├── scripts/validate-project.py
├── starter/
└── integrations/code-constitution/
```

### З чаго пачаць

* [Апісанне метаду па-англійску](methodology/METHOD.en.md)
* [Апісанне метаду па-руску](methodology/METHOD.ru.md)
* [Апісанне метаду па-ўкраінску](methodology/METHOD.uk.md)
* [Апісанне метаду па-беларуску](methodology/METHOD.be.md)
* [Схема кантракта фрагмента](schemas/CONTRACTS.schema.md)
* [Схема сцэнарыяў валідацыі](schemas/SCENARIOS.schema.md)
* [Схема TRACE фазы 0](schemas/TRACE.phase-0.schema.md)
* [Схема TRACE фазы 1](schemas/TRACE.phase-1.schema.md)

## Ролі файлаў

* `*.plan.md` — кананічны аўтарскі план з названымі фрагментамі, абмежаваннямі і намерам;
* `CONTRACTS.md` — пласт кантрактаў паміж планам і генерацыяй;
* `SCENARIOS.md` — сцэнарыі прыёмкі і валідацыі;
* `prompts/*.prompt.md` — абмежаваныя аперацыі LLM над планам і кантрактамі;
* `generated/` — згенераваныя артэфакты-кандыдаты да прыняцця;
* `scripts/validate-project.py` — праверка абавязковай структуры метаду;
* `tests/smoke-check.*` — дэтэрмінаваная праверка прынятых артэфактаў;
* `output.expected.*` — маркеры або здымкі чаканага вываду;
* `TRACE.md` — журнал запускаў запытаў, рашэнняў, праверак і прыняцця або адхілення.

## Мінімальны працэс

1. Напішыце або зафіксуйце аўтарскі план.
2. Вызначце названыя фрагменты.
3. Дадайце кантракты для ўсіх фрагментаў, якія запаўняе LLM.
4. Вызначце сцэнарыі і крытэрыі прыёмкі.
5. Пазначце дазволеныя месцы генерацыі праз `LLM-TODO`.
6. Выканайце структурную валідацыю.
7. Запусціце абмежаваны запыт.
8. Прымайце толькі дазволеныя замены фрагментаў.
9. Праверце атрыманы кандыдат.
10. Запусціце тэсты або smoke-check.
11. Запішыце запуск, змены, праверкі і рашэнне ў `TRACE.md`.
12. Абнаўляйце кананічную крыніцу пасля прыняцця.

## Межы метаду

Prompt-Literate Workflow мае эксперыментальны статус.

Метад мае асобныя ўласцівасці ў параўнанні з дэтэрмінаванымі працэсамі WEB, CWEB, noweb, Org Babel, Quarto, Jupyter і R Markdown. Яго дэтэрмінаваны пласт складаюць аўтарскі план, кантракты, сцэнарыі, тэсты і трасіроўка. Вывад LLM залежыць ад мадэлі, версіі, кантэксту і рэжыму выканання.

Першапачаткова метад сфармуляваны ў аглядзе [*Literate Programming: Donald Knuth, WEB, and Contemporary Workflows*](https://github.com/Zhovten-Games/literate-programming) і ўдакладнены праз практычнае прымяненне да ядра самастойнага праекта.

## Неабавязковыя інтэграцыі

[Набор інтэграцыі з Канстытуцыяй кода](integrations/code-constitution/README.md) звязвае PLW з асобна прынятым канстытуцыйным і заканадаўчым парадкам праекта. Корпус кіравання захоўвае паўнамоцную ролю ў пытаннях паўнамоцтваў, правілаў і прыняцця; аўтарскі план PLW вызначае намер і абмежаваную структуру канкрэтнай аперацыі. Рэдакцыі абедзвюх крыніц замацаваныя, канфлікты спыняюць запуск, а вывад LLM захоўвае статус кандыдата да дэтэрмінаваных праверак і прыняцця ўпаўнаважаным чалавекам.

## Выкарыстанне як шаблону або падмодуля

Рэпазіторый наўмысна кампактны.

Яго можна выкарыстоўваць:

* як шаблон GitHub для новага праекта на аснове PLW;
* як замацаваны падмодуль Git у большым рэпазіторыі;
* як метадалагічную крыніцу з дадатковымі лакальнымі пашырэннямі.

Правілы канкрэтнага праекта захоўваюцца па-за ўніверсальным ядром да асобнага абагульнення і свядомага ўключэння ў метад.

</details>
