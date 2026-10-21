# Figma integration proof — notification component discovery

**Status:** Technical proof completed; UX validation and implementation mapping pending  
**Evidence date:** 21 October 2026  
**Execution environment:** Organisational Bitbucket Pipelines (manual custom runs)  
**Project:** CX Communication Governance  
**Figma file:** Top 5 Notifications  
**Figma file key:** `gVaJt8flh9g1VuMthG7B4H`  
**Target design page:** `02/04/2026 - v6` (`289:1649`)  
**Record type:** Sanitised summary of pipeline logs supplied during the test. This GitHub record is not a direct Bitbucket run-log export.

## Purpose

Test whether Bitbucket can read Figma design metadata, identify existing UX components and establish traceable candidates for reuse in governed customer communications. No design, Salesforce template or governance rule was changed by the API tests.

## Tests and observed outcomes

| Test | Focus | Result | Evidence / limitation |
| --- | --- | --- | --- |
| 01 — Connection | Authenticate Bitbucket to Figma file API | PASS | Read `Top 5 Notifications`; retrieved 17 pages. |
| 02 — Node | Read targeted node | PASS | `106:16244` is `01. Overview` (`CANVAS`), not a design component. |
| 03 — Inventory | Read file-level `components` and `componentSets` with `depth=1` | PASS (limited discovery) | Returned 0 components and 0 sets; not evidence that no instances exist deeper in the file. |
| 04 — Hierarchy | Traverse Overview page | PASS | 12 nodes; maximum depth 5; 3 multi-child FRAME/GROUP candidates; 0 formal component-related nodes on this page. |
| 05 — Target workspace | Locate notification design page | PASS | Located `02/04/2026 - v6` (`289:1649`), with seven top-level notification frames. |
| 06 — Structure comparison | Compare seven notification frames | PASS | Each had 69 nodes, 14 FRAME, 17 TEXT and 4 GROUP nodes, plus 7 component-related nodes; common layer names included `header`, `heading and body` and `.email template footer`. Similar structure alone does not prove identical design properties. |
| 07 — Component relationships | Inspect `Case received` frame | PASS | Seven `INSTANCE` nodes and seven unique source component IDs. `.Email template header` instance `289:1811` referenced `66:2737`. |
| 08 — Header validation | Resolve source and instance | PASS | `66:2737` resolved as a `COMPONENT` named `Type=Left aligned, Links=False`; `289:1811` resolved as an `INSTANCE` referencing it and exposing `Type` and `Links` variant properties. Available variant options and approval state remain unverified. |

All eight tests returned success in the logs provided. These results validate read-only API access, not an end-to-end component publishing or governance workflow.

## Seven notification frames inspected

| Design | Node ID |
| --- | --- |
| Closed: resolved | `289:1650` |
| Customer cancelled | `289:1680` |
| Closed: Duplicate | `289:1710` |
| Not CoM — within boundary | `289:1740` |
| Not CoM — outside boundary | `289:1770` |
| Case received — A | `289:1800` |
| Case received — B | `392:1176` |

## Confirmed component relationships in Case received — A

| Instance name | Source component ID | Observed instance properties |
| --- | --- | --- |
| `.Email template header` | `66:2737` | Type, Links |
| Logo | `1:3467` | Type, Colour, Size |
| Avatar (iOS) | `66:2541` | Initials, Presence, Size, Style |
| Presence badge (iOS) | `66:2396` | State, Size, Out of office |
| Icon | `66:2311` | State, Size, Theme |
| More Horizontal | `66:2238` | Size, Theme |
| `.iPhone-Status Bar` | `66:2151` | Mode, Device |

The iOS-related instances may be presentation/mockup components, not governed email elements. Do not automatically treat all seven as reusable customer communication components.

## Interpretation and architectural boundary

**Validated:** Bitbucket Pipelines can authenticate to Figma with a scoped token and read file, page, node, instance and source-component metadata. A real email header instance references a resolvable Figma component definition.

**Not yet validated:** UX approval, full variant options, consistency of source component IDs across all seven notifications, whether header/footer are the appropriate governance boundaries, production Salesforce implementation alignment, change detection, or write-back/synchronisation of component registry records.

**Source authority:** Figma remains the UX design authority; organisational Bitbucket is the intended governed-knowledge source; Salesforce remains the authority for deployed communications; Confluence and Jira retain their existing review/change roles. Public GitHub is a working mirror, not the source for controlled design assets or credentials.

The proposed reusable registry should store metadata and reference links, not duplicate original Figma designs. It must distinguish candidate from UX-approved components and exclude incidental preview-interface elements. No approved organisational design system is claimed.

## Next contained actions

1. **Compare header instances across all seven designs:** verify each `.Email template header` instance's `componentId`, selected `Type` / `Links` values and material variation without printing customer-facing text.
2. **Review with Mindy (UX) and Dennis (CX):** confirm which components should be reused, the authoritative Figma library/owner, approval expectations and permissible variants.
3. **Register one candidate:** only after confirming the appropriate component boundary, add a proposed `design-components/email-template-header.yaml` mapping in the organisational Bitbucket source, with source reference, usage, ownership and approval state. Keep the GitHub mirror sanitised.
4. **Test governance value:** map that candidate to an existing communication intent, then assess whether the governance agent can suggest reuse and flag differences without automatically approving or editing a Salesforce template.

## Record and sync status

- Test logs: supplied from Bitbucket execution; no Bitbucket build numbers or run URLs captured here.
- GitHub: this evidence record only.
- Bitbucket: **sync pending, to be performed manually by repository owner**.
- UX approval: pending.
- Agent/runtime or Salesforce integration: not implemented in this proof.

## Security

Personal access tokens are stored as secured Bitbucket pipeline variables and must never appear in public GitHub. Do not export raw Figma responses, unredacted customer copy, private design assets or controlled organisational material into the public mirror.
