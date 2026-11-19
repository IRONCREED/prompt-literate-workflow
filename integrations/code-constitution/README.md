# Code Constitution integration

This optional kit combines Prompt-Literate Workflow (PLW) with a separately
adopted [Code Constitution](https://github.com/FOP-Oksana-Dubinetska/code-constitution).
It is an adapter between two independent methods. Neither repository becomes a
hidden dependency of the other, and project-specific governance remains in the
adopting project.

## Division of authority

| Source | Governs |
| --- | --- |
| Code Constitution | Constitutional boundaries, powers, source hierarchy, amendment, interpretation, and acceptance |
| Project Founding Profile | Identity, scope, roles, applicable acts, evidence, and ratification thresholds |
| Project legislation | Change procedure, technical regulators, checks, exceptions, and release rules |
| Human-authored PLW plan | Intent, named chunks, and bounded structure of one project operation |
| Contracts and scenarios | Permitted generation, acceptance criteria, and deterministic evidence |
| Prompt | One operation over the recognised sources |
| Candidate and TRACE | Proposed output and evidence; neither creates normative authority |

The sources are complementary. Governance determines whether an operation is
authorised and acceptable. The plan determines what the authorised operation is
intended to accomplish. A conflict, missing power, unresolved founding value,
or unpinned source stops the run.

## Adoption modes

- `reference` keeps the upstream Constitution unchanged at an immutable commit
  and creates a project-local Profile and legislation.
- `derived` creates a project edition of the Constitution. The adopting project
  changes its identity, official repository, holders, status statement, and
  attribution as required by the upstream README.

The assessment prompt proposes a mode. An authorised human selects it.

## Two prompts to establish the workspace

1. Run [`01-assess.prompt.md`](prompts/01-assess.prompt.md) without write
   permission. It inventories the target repository, verifies immutable source
   revisions, and lists founding decisions that require human answers.
2. Approve or revise the assessment, then run
   [`02-instantiate.prompt.md`](prompts/02-instantiate.prompt.md). It creates
   only the governance and PLW overlay, records a phase 0 TRACE entry, and
   leaves application code unchanged.

## Two prompts to operate the workspace

1. Run [`03-execute-change.prompt.md`](prompts/03-execute-change.prompt.md) for
   one approved change. It prepares a normative-translation record, changes
   only authorised PLW chunks or files, and returns a candidate.
2. Run [`04-review-and-accept.prompt.md`](prompts/04-review-and-accept.prompt.md)
   to inspect the candidate, execute declared checks, and prepare an acceptance
   recommendation. Merge, ratification, release, and other protected actions
   remain with the role named by the project Profile.

## Required project overlay

The target shape is defined in [`WORKSPACE.schema.md`](WORKSPACE.schema.md).
Copy the templates from `templates/` into the target project and fill them only
from approved facts:

- `governance/GOVERNANCE_SOURCES.md`;
- `methodology/extensions/CODE_CONSTITUTION.md`;
- `governance/normative-translations/<change-id>.md` for each relevant change.

Use the neutral PLW `starter/` for `project.plan.md`, `CONTRACTS.md`,
`SCENARIOS.md`, `TRACE.md`, `prompts/`, `generated/`, and the initial
smoke-check. Preserve the upstream repositories as pinned read-only inputs or
submodules.

## Validation

At minimum, a generation-ready project runs:

```bash
python external/prompt-literate-workflow/scripts/validate-project.py \
  --project . \
  --state generation-ready
```

It also runs the checks declared by the adopted legislation and the target
project. A green PLW validator proves structural readiness. It does not prove
that the Profile was lawfully ratified, that a specification preserves its
source norm, or that an authorised human accepted the candidate.

## Stop conditions

Stop and request a decision when:

- either upstream source is identified only by a mutable branch or tag;
- the Profile contains unresolved authority, identity, or ratification fields;
- the task requires a constitutional or legislative change that has not been
  adopted;
- the plan conflicts with governance;
- the requested file or chunk is outside the allowed scope;
- a technical regulator lacks a normative basis, owner, or change procedure;
- deterministic evidence is unavailable;
- the model would review, accept, and ratify its own output without the
  separation required by the Profile.

<details>
<summary>Русская версия</summary>

## Интеграция с «Конституцией кода»

Комплект соединяет Prompt-Literate Workflow с отдельно принятой
[«Конституцией кода»](https://github.com/FOP-Oksana-Dubinetska/code-constitution).
Он остаётся необязательным адаптером двух независимых методов. Конституция,
Учредительный профиль и Законодательство определяют полномочия, порядок
источников, изменение и принятие. Human-authored PLW-план определяет замысел,
именованные фрагменты и границы одной операции. Контракты, сценарии, проверки
и TRACE переводят эту операцию в проверяемый процесс.

Для учреждения рабочего пространства используются два промпта: первый
проводит аудит без записи и собирает недостающие учредительные решения, второй
создаёт только нормативный и PLW-слой после человеческого утверждения. Для
обычной работы используются ещё два промпта: третий создаёт ограниченный
кандидат с записью нормативного перевода, четвёртый проверяет его и формирует
рекомендацию о принятии. Модель не получает полномочия объединять, ратифицировать
или выпускать собственный результат.

Интеграция останавливается при плавающей редакции источника, незаполненном
Профиле, конфликте плана с нормой, отсутствии полномочия, выходе за разрешённые
файлы, незарегистрированном техническом регуляторе или отсутствии
детерминированного доказательства.

</details>

<details>
<summary>Українська версія</summary>

## Інтеграція з «Конституцією коду»

Комплект поєднує Prompt-Literate Workflow з окремо прийнятою
[«Конституцією коду»](https://github.com/FOP-Oksana-Dubinetska/code-constitution).
Він залишається необов’язковим адаптером двох незалежних методів. Конституція,
Установчий профіль і Законодавство визначають повноваження, порядок
джерел, зміну та прийняття. Human-authored PLW-план визначає задум,
іменовані фрагменти та межі однієї операції. Контракти, сценарії, перевірки
та TRACE перетворюють цю операцію на процес, який можна перевірити.

Для заснування робочого простору використовуються два промпти: перший
проводить аудит без запису та збирає відсутні установчі рішення, другий
створює лише нормативний і PLW-шар після людського затвердження. Для
звичайної роботи використовуються ще два промпти: третій створює обмеженого
кандидата із записом нормативного перекладу, четвертий перевіряє його та формує
рекомендацію щодо прийняття. Модель не отримує повноважень виконувати
злиття, ратифікувати
або випускати власний результат.

Інтеграція зупиняється за плаваючої редакції джерела, незаповненого
Профілю, конфлікту плану з нормою, відсутності повноважень, виходу за межі дозволених
файлів, незареєстрованого технічного регулятора або відсутності
детермінованого доказу.

</details>

<details>
<summary>Беларуская версія</summary>

## Інтэграцыя з «Канстытуцыяй кода»

Камплект спалучае Prompt-Literate Workflow з асобна прынятай [Канстытуцыяй кода](https://github.com/FOP-Oksana-Dubinetska/code-constitution) як неабавязковы адаптар двух самастойных метадаў. Канстытуцыя, Устаноўчы профіль і Заканадаўства вызначаюць паўнамоцтвы, іерархію крыніц, парадак змены і прыняцця. Чалавечы PLW-план задае намер, іменаваныя фрагменты і межы аперацыі. Кантракты, сцэнарыі, праверкі і TRACE забяспечваюць правяральнасць працэсу.

Для заснавання працоўнай прасторы першы промпт праводзіць аўдыт без запісу і збірае адсутныя ўстаноўчыя рашэнні, другі стварае нарматыўны і PLW-слой пасля чалавечага зацвярджэння. Для працы трэці промпт стварае абмежаванага кандыдата з запісам нарматыўнага перакладу, чацвёрты правярае яго і рыхтуе рэкамендацыю аб прыняцці. Зліццё, ратыфікацыя і выпуск захоўваюцца за роляй, вызначанай Профілем праекта.

Інтэграцыя спыняецца пры плаваючай рэдакцыі крыніцы, незапоўненым Профілі, канфлікце плана з нормай, адсутнасці паўнамоцтваў, выхадзе за дазволеныя файлы, незарэгістраваным тэхнічным рэгулятары або адсутнасці дэтэрмінаванага сведчання.

</details>
