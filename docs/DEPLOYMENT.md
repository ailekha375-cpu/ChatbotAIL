# Deployment

## Frontend

Platform:

- Vercel

Repo used for deployment:

- `ailekha375-cpu/lekha-ai`

Important frontend env vars:

- `AZURE_FUNCTION_URL`

- `NEXT_PUBLIC_APP_BASE_URL`
  - example:
  - `https://www.lekhaai.com`

## Backend

Platform:

- Azure Function App

Source folder used for deployment:

- [C:\Users\yashv\Lekha.ai\lekha_function_app](C:\Users\yashv\Lekha.ai\lekha_function_app)

Important backend env vars:

- `FUNCTIONS_WORKER_RUNTIME=python`
- `AzureWebJobsStorage`
- `OPENAI_API_KEY`
- `FIREBASE_SERVICE_ACCOUNT_JSON`
- `COSMOS_URL`
- `COSMOS_KEY`
- `COSMOS_DB_NAME`
- `COSMOS_CONTAINER_EVENTS`
- `COSMOS_CONTAINER_GUESTS`
- `COSMOS_CONTAINER_RSVP_RESPONSES`
- `COSMOS_CONTAINER_CONVERSATIONS`
- `COSMOS_CONTAINER_MESSAGES`
- `COSMOS_CONTAINER_CONTACTS`
- `EMAIL_PROVIDER`
- `EMAIL_API_KEY`
- `EMAIL_FROM`
- `APP_BASE_URL`

## Cosmos containers used

- `events`
- `guests`
- `rsvpResponses`
- `conversations`
- `messages`
- `contacts`

## Public URL configuration

Two URL settings matter:

- `APP_BASE_URL`
  - backend-side public site URL used in sent emails
- `NEXT_PUBLIC_APP_BASE_URL`
  - frontend-side public site URL used when copying/opening RSVP links from host views

## Email setup

Current provider:

- Resend

Example sender:

- `EMAIL_FROM=Lekha <invites@lekhaai.com>`

## Current deployment split

- Vercel hosts frontend
- Azure hosts backend
- frontend proxies to Azure using `AZURE_FUNCTION_URL`
