# ResearchOS

ResearchOS is a web app for turning an early research idea into a more concrete project plan.

A user can describe a problem and get a structured starting point with a research question, hypotheses, evidence to look for, a literature map, and an experiment outline.

## Stack

- Next.js / TypeScript
- Tailwind CSS
- OpenAI API
- Google OAuth
- REST API endpoints
- Render deployment

## How it works

The browser sends the research problem to `/api/research-plan`. The server uses the configured model to generate the project structure and returns it to the app.

There is also a local fallback when no API key is configured, so the project can still be run without exposing a key to the browser.

The app also has an outreach workflow that can connect to a server-side LLM endpoint for generating drafts. Provider keys are kept on the server rather than in client-side code.

## Running locally

Set the API key in the server environment:

```bash
OPENAI_API_KEY="your-key" sh start-ai-server.sh
```

Then open the local app at the port shown by the server.

Do not commit `.env` files, API keys, or other credentials to the repository.

## Deployment

The repository includes a Render configuration. The OpenAI key should be added as an environment secret in the deployed service rather than stored in the repository.

For Google sign-in, configure the deployed application's authorized origins in Google Cloud and keep any OAuth client secret server-side.

## Status

ResearchOS is an actively developed project. The current version is primarily focused on research planning and the underlying LLM workflow.
