# Product overview

## What the project does

Lekha helps a host create invitation assets, attach them to an event, send invites, and collect RSVPs.

The project combines:

- AI-assisted drafting
- event management
- contact management
- invite sending
- RSVP collection

## Main user flow

1. Create an event.
2. Use AI Studio to generate invite ideas or email copy.
3. Save a final invite image and email draft to the event.
4. Add contacts to the guest book.
5. Choose recipients for the event.
6. Send invites.
7. Guests respond using personal RSVP links.
8. Host reviews responses.

## Product decisions

### Contacts are account-level

Contacts live in a reusable guest book so the user does not need to re-enter the same people for every event.

### Guests are event-level

Each event still needs its own guest assignments because RSVP tokens, send status, and responses are event-specific.

### Campaign kit is event-level

Each event keeps:

- saved invite image
- saved email draft
- linked AI chats

This makes the event page the send-ready workspace.

## Current pages

- `/`
- `/chat`
- `/events`
- `/events/[eventId]`
- `/events/[eventId]/responses`
- `/guests`
- `/rsvp/[token]`

## Current gaps

- delivery/open tracking is still basic
- no background job system yet
- no bulk CSV import yet
- no account-level guest groups yet
- no provider webhook processing yet
