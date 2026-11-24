# Showcase finalisation — 24 November 2026

Status: presenter-approved HTML v14; prepared for 25 November branch showcase. This is a presentation record, not production approval.

## Deliverable
`curiosity_killed_the_cat_showcase_v14.html` — interactive presentation, Curiosity killed the cat. Finalised with presenter-led answer reveals, compact cards without scrolling as a design requirement, discreet cat illustrations, speaker notes and architecture diagrams. The HTML remains a separate presentation artefact; this record does not assert it has been uploaded here.

## Story and evidence
- Challenge: scaling communication improvements beyond individual templates.
- Architecture: governed knowledge in Bitbucket, Confluence for documentation, Jira for delivery tracking, external tools as separate connections.
- Discovery: individual templates visible but bulk inventory unavailable; attempted SOQL extraction blocked by REST API permissions. Sent-email analysis provided an alternative, not an authoritative template inventory.
- Pivot: recurring communication intent across services rather than individual rendered templates.
- Controlled synthetic comparison: existing writing assistant demonstrated 0/5 target governance capabilities in this test; dedicated configuration demonstrated 5/5 after refinement. Criteria: classify, assess quality, propose improvements, detect drift, recommend reuse. These are scenario outcomes, not general model performance scores.
- Drift refinement: implementation changes to response_method were initially misclassified as rule drift. Contract refined: content drift means implementation changes while rule remains unchanged; rule drift means governed rule changes and implementation has not caught up. Targeted retest correctly classified content drift.
- Workflow proof: controlled pipeline created documentation and work-tracking artefacts with traceability. External design metadata connection also explored; no production synchronisation claim.
- Presenter-reported effort: less than eight hours, from morning brief to late-afternoon output validation. Not a measured productivity benchmark.

## Source references
See repository README and `tests/results/communication-governance-capability-test-01.md` and `tests/results/atlassian-creation-proof-01.md`. The synthetic fixture set is mock-salesforce-template-estate v0.1 (16 simulated records), not authoritative Salesforce templates. The Databricks saved query and detailed source links are retained in the organisational case-study workspace and presenter notes rather than reproduced in this public repository.

## Boundary
Prototype feasibility only; human oversight and approval remain necessary. No production rollout, approved architecture, or automated synchronisation is implied. No customer data, internal links, screenshots or presentation imagery copied into this public reference.

## Final presenter revisions — 25 November 2026
- Added a Git explanation to the Bitbucket card via an information tooltip.
- Corrected slide 5 source reference and speaker notes: recovered synthetic fixture set contains 16 records, nine candidate intents and four matching implementations; identical inputs across both agent tests have not been independently verified.
- Corrected the slide 7 timeline and speaker notes to place the Salesforce-to-Databricks pivot before lunch. Timing remains presenter-reported.
- Presenter approved v14. Presentation HTML remains separate; no production or test evidence was changed by these editorial revisions.
