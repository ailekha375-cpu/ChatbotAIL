# API reference

This is a practical route summary, not a full schema spec.

## Frontend proxy routes

Location:

- `invite-rsvp-app/src/app/api/*`

These routes sit between the browser and Azure Functions.

### Chat and sessions

- `POST /api/chat`
  - send prompt to backend
- `GET /api/sessions`
  - load chat sessions
- `GET /api/sessions/[conversationId]`
  - load one conversation
- `DELETE /api/sessions/[conversationId]`
  - delete one conversation

### Events

- `GET /api/events`
  - list events
- `POST /api/events`
  - create event
- `GET /api/events/[eventId]`
  - get event
- `DELETE /api/events/[eventId]`
  - delete event
- `GET /api/events/[eventId]/campaign-kit`
  - load event campaign kit
- `PATCH /api/events/[eventId]/campaign-kit`
  - update event campaign kit
- `GET /api/events/[eventId]/guests`
  - list event guests
- `POST /api/events/[eventId]/guests`
  - assign recipients to event
- `GET /api/events/[eventId]/responses`
  - list RSVP responses for event
- `POST /api/events/[eventId]/send`
  - send emails for event

### Contacts

- `GET /api/contacts`
  - list guest-book contacts
- `POST /api/contacts`
  - create contact
- `PATCH /api/contacts/[contactId]`
  - update contact
- `DELETE /api/contacts/[contactId]`
  - delete contact

### RSVP

- `GET /api/rsvp/[token]`
  - load public RSVP page data
- `POST /api/rsvp/[token]`
  - submit RSVP

## Azure Function routes

Location:

- [lekha_function_app/function_app.py](https://github.com/ailekha375-cpu/ChatbotAIL/blob/main/lekha_function_app/function_app.py)

Main route groups:

- `chat`
- `sessions`
- `events`
- `events/{eventId}`
- `events/{eventId}/campaign-kit`
- `events/{eventId}/guests`
- `events/{eventId}/responses`
- `events/{eventId}/send`
- `contacts`
- `contacts/{contactId}`
- `rsvp/{token}`

## Important behavior notes

### `POST /api/events/[eventId]/guests`

This is not just a raw guest-creation route anymore.

It can:

- create guests from contact IDs
- reuse an existing guest if the same contact is already assigned to that event
- generate RSVP tokens for new event guests

### `POST /api/events/[eventId]/send`

This sends invite emails using:

- the saved event campaign kit
- selected event guests
- current email subject/body

It is intentionally confirmation-based in the UI.

### `PATCH /api/events/[eventId]/campaign-kit`

This is used to persist:

- saved invite image
- saved email draft
- linked AI chats
