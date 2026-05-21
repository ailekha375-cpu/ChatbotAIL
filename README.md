# Lekha

Lekha is an invitation and RSVP workflow app.

It started as an AI invite generator and evolved into an event workspace where a user can:

- generate or edit invite concepts
- save an invite image to an event
- save email copy to an event
- manage contacts and recipients
- send invitation emails
- collect RSVP responses
- review RSVP summaries

This repo contains both the frontend and the Azure backend.

## Repo structure

- [C:\Users\yashv\ChatbotAIL\invite-rsvp-app](C:\Users\yashv\ChatbotAIL\invite-rsvp-app)
  - Next.js frontend
  - frontend API proxy routes
  - chat UI, event hub, guest book, RSVP pages
- [C:\Users\yashv\ChatbotAIL\lekha_function_app](C:\Users\yashv\ChatbotAIL\lekha_function_app)
  - Azure Functions backend
  - Cosmos access
  - Firebase auth verification
  - email sending
  - RSVP token routes

## Main workflow

1. User opens AI Studio and generates invite ideas or email copy.
2. User saves the final invite image and email draft to an event.
3. User manages contacts in `My Guests`.
4. User opens an event and selects which contacts should receive invites.
5. Backend creates event-level guest assignments and RSVP tokens.
6. Backend sends invite emails.
7. Guests open personal RSVP links and respond.
8. Host reviews responses in the event dashboard.

## Current feature set

- AI chat for invite/image prompts and email drafting
- invite editor with image + text overlay flow
- event creation and event workspace
- account-level contact book
- recipient selection modal when sending
- email sending through Azure backend
- personal RSVP links
- RSVP response dashboard

## Tech stack

Frontend:

- Next.js 16
- React 19
- TypeScript
- Firebase Web SDK

Backend:

- Azure Functions Python v2
- Azure Cosmos DB
- Firebase Admin
- Resend
- Azure Storage Blob support present in backend

Deployment:

- Vercel for frontend
- Azure Functions for backend

## Key docs

- [C:\Users\yashv\ChatbotAIL\docs\PRODUCT.md](C:\Users\yashv\ChatbotAIL\docs\PRODUCT.md)
- [C:\Users\yashv\ChatbotAIL\docs\ARCHITECTURE.md](C:\Users\yashv\ChatbotAIL\docs\ARCHITECTURE.md)
- [C:\Users\yashv\ChatbotAIL\docs\DEPLOYMENT.md](C:\Users\yashv\ChatbotAIL\docs\DEPLOYMENT.md)
- [C:\Users\yashv\ChatbotAIL\docs\TROUBLESHOOTING.md](C:\Users\yashv\ChatbotAIL\docs\TROUBLESHOOTING.md)
- [C:\Users\yashv\ChatbotAIL\docs\INTERVIEW_NOTES.md](C:\Users\yashv\ChatbotAIL\docs\INTERVIEW_NOTES.md)

## Important note about repo history

There are older backend artifacts inside the frontend tree, including:

- `invite-rsvp-app/AZURE_FUNCTION_COMPLETE.py`
- `invite-rsvp-app/lekha_function_app/`

The active backend source of truth is:

- [C:\Users\yashv\ChatbotAIL\lekha_function_app\function_app.py](C:\Users\yashv\ChatbotAIL\lekha_function_app\function_app.py)

Those older files should be treated as historical copies unless the repo is cleaned up later.
