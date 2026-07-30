# Code Constitution + PLW workspace schema

## Required source declarations

`governance/GOVERNANCE_SOURCES.md` records:

- adoption mode: `reference` or `derived`;
- Code Constitution repository URL, full commit SHA, constitutional source
  path, and SHA-256 of the adopted text;
- PLW repository URL, full commit SHA, method version, and method path;
- paths of the project Constitution, Founding Profile, legislation, PLW plan,
  contracts, scenarios, prompts, TRACE, candidates, and checks;
- named holders for review, acceptance, amendment, and release;
- conflict and stop rule.

A branch, unqualified tag, latest release label, chat attachment, or remembered
text is insufficient as a source revision.

## Required project files

```text
<project-root>/
├── governance/
│   ├── GOVERNANCE_SOURCES.md
│   ├── PROFILE.md
│   ├── legislation/
│   └── normative-translations/
├── methodology/
│   └── extensions/
│       └── CODE_CONSTITUTION.md
├── project.plan.md
├── CONTRACTS.md
├── SCENARIOS.md
├── TRACE.md
├── prompts/
├── generated/
├── tests/
└── external/
    ├── code-constitution/
    └── prompt-literate-workflow/
```

`governance/CONSTITUTION_CODE.md` is additionally required in `derived` mode.
In `reference` mode, `GOVERNANCE_SOURCES.md` points to the pinned read-only
upstream text.

## Source hierarchy

1. Applicable external law and obligations.
2. Adopted project Constitution.
3. Ratified Founding Profile.
4. Effective project legislation.
5. Approved human-authored PLW plan.
6. Contracts and scenarios.
7. Bounded prompt.
8. Candidate output and TRACE evidence.

Lower sources operate inside the authority supplied by higher sources. They do
not amend higher sources by implication.

## Readiness states

### Assessed

- repository inventory exists;
- immutable upstream revisions are resolved;
- unresolved founding decisions are listed;
- no project files have been changed.

### Instantiated

- governance sources and adoption mode are recorded;
- Profile and applicable legislation have project-local paths;
- PLW extension, plan, contracts, scenarios, prompts, and TRACE exist;
- unresolved authority fields block generation.

### Generation-ready

- every LLM-fillable chunk has a contract and acceptance criteria;
- every scenario declares test backing;
- the task is authorised and bounded;
- the normative-translation record exists;
- relevant technical regulators are registered;
- PLW and project validation commands are declared.

### Accepted

- the candidate changed only authorised files or chunks;
- plan, contract, scenario, and governance review passed;
- deterministic checks were executed and reported;
- TRACE records model, inputs, output, edits, evidence, and decision;
- the authorised project role accepted the candidate;
- any constitutional or legislative change completed its own procedure.

## Conflict rule

An instruction that exceeds a granted power, changes a pinned source, bypasses
an applicable gate, or contradicts a higher source is invalid for the run. The
executor reports the exact conflict and requests a decision from the competent
role.
