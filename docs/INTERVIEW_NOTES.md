# Interview notes

## Short summary

Lekha is an AI-assisted invitation and RSVP workflow system. A user can generate invite content, save a final invite image and email draft to an event, select recipients from a reusable contact book, send invites, and track RSVP responses.

## Two-minute explanation

I built a full-stack invitation workflow app. The frontend is in Next.js and the backend is in Azure Functions with Cosmos DB. The product started as an invite generator, but I turned it into an event workspace with reusable contacts, event-level recipients, email sending, and RSVP tracking. One of the main engineering challenges was keeping Vercel and Azure deployments in sync while debugging Firebase auth, Cosmos configuration, and serverless route indexing issues.

## Main technical choices

### Why Next.js

- good fit for product UI
- route handlers work well as a proxy layer to Azure
- simple Vercel deployment

### Why Azure Functions

- enough for current traffic
- easy route-based API model
- good fit for auth + Cosmos + email sending

### Why Cosmos DB

- flexible document model
- simple for event, guest, contact, and RSVP records
- easy to evolve during product changes

### Why contacts and guests are separate

- contacts are reusable across events
- guests are event-specific because RSVP token, send state, and response state belong to the event

## Good points to emphasize

- product evolved based on real UX problems
- architecture clearly separated frontend, backend, and data responsibilities
- handled real deployment and runtime debugging, not only local coding

## Hard problems solved

- fixing malformed Firebase credential config in Azure
- resolving Cosmos database/container mismatches
- debugging Azure package deployment versus runtime indexing
- fixing Vercel static build issues on `/chat`
- fixing public URL generation for RSVP links
- redesigning data model from event-only guests to account-level contacts plus event guests

## Honest limitations

- email delivery tracking is still basic
- no background queue or worker system yet
- no CSV import yet
- repo structure still has some historical backend copies inside the frontend tree

## If asked about scaling

Next steps would be:

- clean repo boundaries
- add background jobs for email sending and retries
- add provider webhooks for delivery status
- move reporting into a proper analytics pipeline

## If asked about data engineering

The app already generates event, guest, RSVP, and send data. The next data engineering step would be to treat the app as the transactional source, export raw data into storage, build cleaned reporting layers with PySpark or Databricks, orchestrate jobs with Airflow, and manage infrastructure with Terraform.
