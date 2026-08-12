# Execute one governed bounded change

**Inputs**:

- one approved change request;
- current target project revision;
- adopted governance sources and full commit SHAs;
- allowed files or named chunks;
- declared validation commands.

Produce a candidate only.

1. Read the source hierarchy, Founding Profile, applicable legislation, PLW
   plan, contracts, scenarios, and latest TRACE before changing files.
2. Confirm the requesting and executing roles have authority for the exact
   scope. Stop on missing or conflicting authority.
3. Classify the change as editorial, normative, structural, tooling, release,
   or emergency under the adopted legislation.
4. Create
   `governance/normative-translations/<change-id>.md`. Record the source norm,
   preserved content, losses, defaults, remaining discretion, technical
   regulators, and separate checks for source-to-specification and
   specification-to-implementation transitions.
5. If the change requires an unadopted constitutional or legislative
   amendment, stop and return that proposal. Do not implement against an
   obsolete normative basis.
6. Modify only authorised LLM-fillable chunks or explicitly allowed files.
   Preserve author-defined chunks and public declarations outside scope.
7. Write generated implementation only under `generated/` until review.
8. Run generation-readiness and candidate checks that are safe at this stage.
9. Record one phase 1 TRACE entry with actual inputs, model/tool, prompt,
   candidate, changed scope, manual edits, checks, and pending decisions.

**Return**:

- candidate paths;
- exact diff scope;
- normative-translation summary;
- commands executed and actual results;
- rejected or blocked work;
- review checklist.
