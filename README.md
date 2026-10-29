# Membership Paid Share and Trial Tracking Automation

This workflow measures the current balance of paid members and active free trials using GoHighLevel contact fields. It stores a current membership snapshot in Airtable.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Contact retrieval:** Pages through GoHighLevel contacts, with a maximum of 40 pages of 100 records.
- **Paid-member count:** Counts a contact as paid when Membership Due Collected is set.
- **Active free trials:** Counts an unpaid contact as free when the Proximity expiration date is today or later.
- **Paid-share calculation:** Calculates paid members divided by paid plus active free members, multiplied by 100 and rounded to one decimal place.
- **Current snapshot:** Updates the Airtable row using the fixed Snapshot Key current.

## Workflow

1. Start a manual or weekly run.
2. Retrieve contacts and read the configured membership fields.
3. Count paid contacts and active unpaid trial contacts.
4. Calculate the member total and paid-share percentage.
5. Upsert the current Membership Conversion row.

## Tools

| Tool | Purpose |
| --- | --- |
| GoHighLevel API | Membership and trial contact fields. |
| n8n | Manual and scheduled execution. |
| JavaScript | Pagination, membership counts and percentage calculation. |
| Airtable | Current membership snapshot. |

## Repository contents

- [`workflows/workflow-v01.json`](workflows/workflow-v01.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `workflow-v01.json` | 4 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `airtableTokenApi`.

## Export limitations and configuration notes

- Inactive in the export. Paid Conversion % is the current paid-member share, not a measured historical free-to-paid cohort conversion.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
