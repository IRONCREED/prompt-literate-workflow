# Instantiate a governed PLW workspace

**Inputs**:

- accepted assessment from `01-assess.prompt.md`;
- explicit human decisions for every founding value used in this pass;
- allowed file list;
- Code Constitution and PLW full commit SHAs.

Create a candidate governance and PLW overlay. Do not modify application code,
merge, ratify, release, or claim that an unexecuted check passed.

1. Reverify both source pins and stop on drift.
2. Create `governance/GOVERNANCE_SOURCES.md` from the integration template.
3. Instantiate the project Founding Profile and applicable legislation only
   from approved facts. Preserve unresolved values as explicit blockers.
4. Create
   `methodology/extensions/CODE_CONSTITUTION.md` from the integration template.
5. Create the neutral PLW plan, contracts, scenarios, prompts, candidate
   directory, tests, and TRACE structure.
6. Record the source hierarchy: governance controls authority and acceptance;
   the human-authored plan controls the intent and bounded structure of each
   operation.
7. Add project-specific scenarios for source-pin drift, unauthorised scope,
   missing normative translation, unregistered technical regulators, failed
   deterministic checks, and attempted self-acceptance.
8. Run planning-state PLW validation and every safe structural check available.
9. Record a real phase 0 TRACE entry with actual changes and results.

**Return**:

- changed files;
- unresolved blockers;
- commands executed and actual results;
- review points;
- readiness: `blocked`, `planning`, or `generation-ready-candidate`.
