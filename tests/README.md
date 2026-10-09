# Tests

## Purpose

Hold synthetic fixtures, controlled proof-of-concept scenarios and recorded results used to validate the communication-governance operating model.

Test content must remain clearly separated from governed production knowledge.

## Initial capability test

The first test validated whether one governed communication definition could support:

- assessment;
- quality checking;
- change-request generation;
- drift detection; and
- reuse suggestions.

Result:

`tests/results/communication-governance-capability-test-01.md`

## Atlassian creation proof

A second controlled test validated whether a Bitbucket Pipeline could create downstream Jira and Confluence artefacts while retaining repository traceability.

Result:

`tests/results/atlassian-creation-proof-01.md`

## Fixtures

Synthetic Salesforce fixtures live under:

`tests/fixtures/salesforce/`

Synthetic fixtures must not be represented as production Salesforce templates.
