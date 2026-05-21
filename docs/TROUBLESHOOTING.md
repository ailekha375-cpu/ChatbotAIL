# Troubleshooting and issues encountered

This section lists the actual issues hit during development and deployment.

## Firebase service account JSON parsing failed

Symptom:

- backend chat route failed

Root cause:

- invalid `FIREBASE_SERVICE_ACCOUNT_JSON`

Fix:

- paste the full JSON content into the app setting

## Azure Function host returned `503 Function host is not running`

Symptom:

- frontend showed backend unavailable

Root cause:

- host restarting after config changes or failing startup

Fix:

- restart Function App
- use Log Stream instead of only detector cards

## Cosmos `Owner resource does not exist`

Symptom:

- chat and event operations failed with Cosmos not found errors

Root cause:

- wrong database/container config
- confusion between Cosmos account name and database name

Fix:

- verify exact database name and containers in Data Explorer

## Delete looked successful but data came back after reload

Symptom:

- item disappeared in UI and returned later

Root cause:

- optimistic frontend removal with stale backend data

Fix:

- tighten backend checks
- stop assuming all `404` deletes are success

## Event page showed backend `404`

Symptom:

- `/events/[eventId]` page reported backend `404`

Root cause:

- frontend expected newer backend routes that Azure had not picked up yet

Fix:

- redeploy Azure Function App from correct folder
- verify Functions list

## Azure deploy succeeded in zip/build but not in active runtime

Symptom:

- VS Code deploy said zip/build succeeded but host runtime returned `ServiceUnavailable`

Root cause:

- package uploaded but host indexing/startup lagged or failed

Fix:

- inspect `/home/data/SitePackages`
- inspect zip contents directly
- restart Function App

## New `contacts` routes missing even though local code had them

Symptom:

- `contacts` did not show in Functions list

Root cause:

- Azure had not reloaded the newest backend package

Fix:

- verify deployed zip contains `contacts` routes
- restart Function App

## Vercel build failed on `/chat`

Symptom:

- prerender error on `/chat`

Root cause:

- `useSearchParams()` needed `Suspense`

Fix:

- wrap `/chat` page in `Suspense`

## Frontend deployment could not reach backend

Symptom:

- deployed event pages showed `fetch failed` or `Backend unreachable`

Root cause:

- missing or incorrect `AZURE_FUNCTION_URL`

Fix:

- set `AZURE_FUNCTION_URL` correctly in Vercel

## RSVP links pointed to localhost

Symptom:

- copied or emailed RSVP links opened `http://localhost:3000`

Root cause:

- backend `APP_BASE_URL` or frontend `NEXT_PUBLIC_APP_BASE_URL` still pointed to localhost

Fix:

- set both to the public domain

## Resend reported delivered but email was not visible

Symptom:

- app said invite sent
- user could not see it in inbox

Resolution:

- email was in Promotions tab

## Recipient modal was too large and not scrollable

Symptom:

- bottom action buttons were hard to reach

Fix:

- reduce modal width
- add internal scroll

## Contact book and assigned recipients felt disconnected

Symptom:

- existing event recipients did not appear in new guest-book flow

Fix:

- show assigned recipients in send modal
- add import path into guest book

## Background visuals interfered with content

Symptom:

- decorative background overlapped text/cards

Fix:

- removed floating poppers
- replaced with calmer gradient background

## Chat page scroll behavior felt wrong

Symptom:

- whole page scrolled
- right rail moved
- composer moved too much

Fix:

- make chat column the main scroll region
- keep right rail stable
- keep composer pinned

## Chat UI had too much label noise

Symptom:

- labels and helper blocks made the UI feel heavy

Fix:

- remove redundant labels
- shrink action pills
- replace bigger helper text with lighter hints

## Event page hierarchy felt off

Symptom:

- campaign kit and recipients used space poorly

Fix:

- move campaign kit above recipients
- compress image area
- tighten recipient rows
