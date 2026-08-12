# Review a governed candidate

**Inputs**:

- candidate and full diff;
- normative-translation record;
- adopted governance sources and full commit SHAs;
- plan, contracts, scenarios, and TRACE;
- declared validation commands;
- identity of the authorised reviewer and accepting role.

Review and prepare an acceptance recommendation. Do not merge, ratify, release,
or exercise a protected action unless the user separately authorises that
specific action and the Founding Profile grants it.

1. Verify source pins and target revision.
2. Confirm every changed file or chunk is authorised and attributed.
3. Check the candidate against the Constitution, Profile, legislation, plan,
   contracts, and scenarios in source-hierarchy order.
4. Review the normative translation for omitted conditions, defaults,
   remaining discretion, affected participants, and contestability.
5. Verify every material technical regulator has an exact normative basis,
   owner, configuration path, observable effect, and change or disable
   procedure.
6. Run all declared deterministic checks. Report actual commands, exit status,
   and evidence paths. Treat unexecuted checks as missing evidence.
7. Confirm TRACE records the real model/tool, prompt, inputs, candidate,
   accepted and rejected scope, manual edits, checks, and reviewer.
8. Separate four conclusions:
   - implementation conforms to specification;
   - specification conforms to source norm;
   - observed behaviour conforms to the accepted candidate;
   - authorised human acceptance is present or still required.

**Return**:

- findings ordered by severity;
- check results and missing evidence;
- required corrections;
- recommendation: `reject`, `revise`, or `eligible-for-authorised-acceptance`;
- exact action still reserved to the accepting or ratifying role.
