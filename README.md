# NNC Events Interactive Product Prototype

This is a responsive, developer-facing prototype for the NNC Events multi-tenant B2B SaaS platform. It translates the product requirements into a coherent operating console rather than a collection of disconnected wireframes.

## Production Deployment

- Live prototype: https://nnc-events-mvp.vercel.app
- Vercel project: https://vercel.com/nnc-growth/nnc-events-mvp
- Deployment repository: https://github.com/naderize/nnc-events-mvp
- Verified production branch: `main`

The Vercel deployment is connected to the `naderize/nnc-events-mvp` repository. Pushes to its `main` branch create production deployments automatically.

## Preview

![Desktop portfolio view](preview-desktop.jpg)

The package also includes `preview-mobile.jpg` for a full-page narrow-screen reference.

## Run Locally

From this directory:

```bash
python3 -m http.server 4173
```

Open `http://127.0.0.1:4173`.

The prototype is plain HTML, CSS, and JavaScript with a bundled Lucide icon library. No build step or external asset request is required.

Integration logos are bundled locally. See [Third-Party Integration Marks](THIRD_PARTY_ASSETS.md) for asset provenance and the production approval requirement.

## Primary Journeys

1. Portfolio administrator reviews events, issues, account usage, and cross-event performance.
2. Event manager creates a draft from a governed template using the five-step event wizard.
3. Event manager configures website, registration, ticket inventory, agenda, attendee rules, and communications.
4. Event director reviews launch readiness and explicitly approves publishing.
5. Onsite manager rehearses devices, monitors offline readiness, and processes arrivals.
6. Marketing and operations teams inspect event and portfolio outcomes.
7. Workspace administrator manages integrations, plan usage, billing, roles, and policy.
8. Product and event teams preview the attendee journey from discovery through post-event follow-up on desktop and mobile.

## Screen Map

### Portfolio

- Home dashboard
- Events list with active and archived states
- People directory
- Governed templates
- Portfolio analytics
- Needs-attention queue
- Plan and billing
- Workspace settings

### Event Workspace

- Event overview and launch readiness
- Website and brand builder
- Registration form builder
- Tickets, payments, and reconciliation
- Agenda and content schedule
- Attendee operations
- Communications and delivery health
- Onsite devices, check-in, badges, and offline state
- Event analytics
- Integrations and synchronization health

### Attendee Experience

- Public event discovery and agenda preview
- Ticket selection, registration, consent, checkout, and confirmation
- Issued QR credential, calendar, wallet, and attendee app entry
- Personalized event home, Klik-style timeline, personal agenda, and offline state
- Networking recommendations, meeting requests, and privacy-aware contact exchange
- Virtual session player with resources, Q&A, polling, and captions
- Onsite credential, venue map, accessible directions, and support
- Post-event recordings, contacts, feedback, and certificate

### Overlay Flows

- Global command search
- Create-event wizard
- Event preview
- Publish approval gate with validation
- Add-ticket flow
- Campaign creation
- Toast confirmations and empty states
- Responsive mobile navigation drawer
- Desktop and mobile attendee journey preview with ten selectable stages

## Prototype Behaviors

- Routes are stored in the URL hash for direct navigation.
- Create Event provisions a new draft and opens its readiness overview.
- Publish Event requires an explicit acknowledgement before changing state.
- Simulate Check-in updates onsite and attendee metrics.
- Registration fields are selectable and reveal field-level rules.
- Save, campaign, ticket, rehearsal, toggle, search, and archive interactions provide realistic feedback.
- The layout adapts from dense desktop operations to a single-column mobile view.
- Attendee journey actions update ticket choice, payment confirmation, session saves, meeting requests, live polls, and feedback state.

## Development Interpretation

The interface assumes one canonical tenant-aware domain model shared by portfolio, event, attendee, content, commerce, communications, onsite, and analytics services. Every production command should carry organization, workspace, event, actor, permission, correlation, and idempotency context.

The readiness checklist represents a server-evaluated policy engine. Publish is a guarded command, not a client-only status change. The same pattern should govern refunds, bulk sends, integration replays, data deletion, and other high-impact operations.

This prototype uses local in-memory data. It does not implement authentication, tenancy isolation, persistence, payments, messaging, media, hardware, or external integrations. Those rows and states illustrate the expected contracts and operational observability.

## Source Requirements

The governing requirements are in [NNC Events PRD v1.1](../nnc-events-prd-handoff-v1.1.md). Requirement IDs, priorities, release phases, accessibility, privacy, auditability, and failure-recovery conditions in that PRD remain authoritative when implementation detail differs from this prototype.

## Suggested Engineering Slices

1. Tenant, workspace, role, event, and audit foundations.
2. Draft event creation, template inheritance, and readiness evaluation.
3. Public event site, registration, identity, consent, and ticket inventory.
4. Orders, provider-hosted payments, refunds, webhooks, and reconciliation.
5. Agenda, attendees, transactional communications, and operational exports.
6. Check-in Progressive Web App with offline queue and device observability.
7. Event activity ledger, analytics semantics, integrations, and portfolio reporting.

Each slice should include permissions, loading and error states, idempotency, audit events, accessibility checks, telemetry, and support tooling before it is considered complete.
