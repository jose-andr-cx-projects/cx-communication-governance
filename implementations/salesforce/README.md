# Salesforce Implementations

## Purpose

Map governed CX communication definitions to operational Salesforce implementations.

Salesforce remains the source of truth for deployed templates and operational configuration.

Files in this folder should contain references and mappings required for governance and assessment.

Do not store raw Salesforce exports, customer information or rendered production communications here.

## Current proof

The first architecture test uses synthetic Salesforce templates stored under:

`tests/fixtures/salesforce/`

Synthetic fixtures must not be represented as production Salesforce templates.

## Current integration gap

Direct, repeatable access to Salesforce `EmailTemplate` has not yet been established.

The controlled proof therefore simulated the template estate using synthetic records informed by communication patterns observed during discovery.

The next operational step is controlled read-only API access to `EmailTemplate` so the proven assessment pattern can run against the real template estate.

A reported estate of 40+ graffiti communications is a candidate real-world pilot once access is available. The count and scope require validation before use.
