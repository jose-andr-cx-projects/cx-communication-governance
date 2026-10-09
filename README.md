# CX Communication Governance

## Purpose

Create a governed, reusable source of CX communication knowledge that can be used across operational systems, human guidance, AI-assisted assessment and change workflows.

The repository supports a model where CX business rules are defined once and reused across multiple communication implementations.

## Core principle

> Govern the communication intent and CX rules once. Reuse them across implementations, assessment, quality assurance, change and maintenance.

Operational systems such as Salesforce remain responsible for deployed communications.

This repository governs reusable CX communication knowledge rather than rendered operational templates.

## Current status

**Prototype — core feasibility demonstrated under controlled synthetic conditions.**

The first architecture test has demonstrated that one governed communication definition can support:

1. communication assessment;
2. quality checking;
3. Jira-ready change-request generation;
4. drift detection; and
5. reuse suggestions.

A dedicated **CX Communication Governance Agent** was used for the test after existing PenPal and CoMpanion agents proved too constrained for this governance use case.

The test used a synthetic Salesforce template estate informed by communication patterns observed during discovery. Synthetic fixtures are not authoritative Salesforce EmailTemplate records.

A Bitbucket Pipeline also successfully created both a Jira work item and a Confluence page from the governed repository while carrying Bitbucket build and commit traceability.

See:

- `tests/results/communication-governance-capability-test-01.md`
- `tests/results/atlassian-creation-proof-01.md`

## Current architecture hypothesis

```text
Salesforce operational templates
        ↓
Bitbucket governed CX communication knowledge
        ↓
CX Communication Governance Agent
        ↓
Human review
        ├── Confluence — human-readable governance view
        └── Jira — governed change workflow
        ↓
Approved operational implementation
```

This remains a prototype operating model, not an approved organisational architecture.

## Next operational step

The main gap between the synthetic proof and a real pilot is controlled, repeatable, read-only access to Salesforce `EmailTemplate`.

Once that access exists, the same assessment pattern can run against the actual template estate rather than synthetic fixtures.

A reported estate of 40+ graffiti communications is a candidate real-world pilot. The count and scope require validation before use.

## Repository structure

```text
communications/
  Governed communication intents and reusable communication definitions.

quality/
  Cross-cutting CX communication quality rules.

implementations/
  Mappings between governed communication definitions and operational implementations.

agents/
  Agent contracts for using governed knowledge safely.

tests/
  Synthetic fixtures, controlled scenarios and recorded proof results.
```

## Source-of-truth model

### Bitbucket

Organisational repository and intended authoritative source for governed CX communication definitions, reusable rules, implementation mappings and automation.

### GitHub

Controlled working mirror/proxy used where external AI tooling cannot access the enterprise Bitbucket environment.

Changes made here for assisted repository maintenance should be treated as equivalent working changes for the Bitbucket repository and kept aligned with the organisational source.

Do not place credentials, raw organisational data, customer information or controlled source material in this public mirror.

### Salesforce and other operational platforms

Authoritative source for deployed operational implementations.

### Confluence

Human-readable governance and review surface.

Confluence should expose governed knowledge rather than become an independently maintained rule source.

### Jira

Change workflow and implementation tracking.

### CX Communication Governance Agent

AI-assisted reasoning layer.

The agent may assess, compare, identify gaps, suggest reuse, detect drift and generate proposed change requests.

It does not approve governance or operational implementation changes.

## Governance boundary

Human approval is required for:

- creation or approval of governed CX rules;
- consolidation or retirement of communication patterns;
- business-policy decisions;
- Jira change requests;
- operational implementation changes; and
- changes that create stakeholder or customer commitments.

AI output is evidence and decision support, not approval.
