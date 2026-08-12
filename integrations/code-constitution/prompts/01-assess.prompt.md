# Assess a governed PLW workspace

**Inputs**:

- target project repository and revision;
- Code Constitution repository and full commit SHA;
- Prompt-Literate Workflow repository and full commit SHA;
- available project requirements and existing governance files.

Perform a read-only assessment. Do not create, modify, stage, commit, push, or
accept files.

1. Verify both upstream revisions as immutable full commit SHAs and identify
   their required source paths.
2. Inventory the target repository, current source hierarchy, checks, release
   process, roles, protected operations, and existing LLM instructions.
3. Compare the target with
   `integrations/code-constitution/WORKSPACE.schema.md`.
4. Separate facts from decisions. List every unresolved P01-P18 value, holder,
   authority, ratification threshold, external obligation, adoption mode, and
   project-local deviation. Do not infer or fill them.
5. Identify conflicts between existing project rules, the proposed governance
   order, and PLW invariants.
6. Propose the exact files to create or update, the checks to run, and the
   smallest safe migration sequence.

**Return**:

- source-pin verification;
- repository inventory;
- unresolved human decisions;
- conflicts and stop conditions;
- proposed workspace tree;
- proposed validation commands;
- readiness: `blocked` or `ready-for-authorised-instantiation`.
