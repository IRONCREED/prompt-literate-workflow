# Project-local extension

## Extension: `code-constitution`

- **Purpose:** Apply the adopted project Constitution, Founding Profile, and
  legislation to every PLW run.
- **Scope:** Planning, candidate generation, review, validation, acceptance,
  and release inside the target project.
- **Type:** restrictive
- **Base invariants preserved:** The human-authored plan remains the source of
  truth for the intent and bounded structure of the operation; contracts remain
  mandatory; generated output remains a candidate; one run creates one TRACE
  entry; deterministic checks and review remain required.
- **Allowed adjustments:** Add governance preflight, immutable source pins,
  normative-translation records, technical-regulator checks, role checks, and
  stricter acceptance gates.
- **Forbidden adjustments:** Granting authority through a prompt; inferring
  unresolved holders or ratification values; changing upstream pins during a
  run; allowing a lower source to amend a higher source implicitly; accepting
  model output without the authorised human decision.
- **Validation expectations:** Validate the PLW structure, verify source pins,
  review the normative translation, run every applicable project check, and
  record actual evidence in TRACE.
- **Conflict-handling rule:** Stop the run, identify the conflicting sources
  and exact scope, and request a decision from the role named in the Founding
  Profile. Task instructions operate only inside already granted authority.
- **Review owner:** `<role or holder from the Founding Profile>`
- **Promotion candidate:** no
- **Notes:** `governance/GOVERNANCE_SOURCES.md` identifies the exact adopted
  revisions and paths.
