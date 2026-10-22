# Operator setup: Gemini CLI OAuth

The package uses the existing MCP OAuth dynamic client registration flow with the fixed local browser callback:

```text
http://localhost:18539/oauth/callback
```

Before advertising installation, add this exact URI to the existing `allowedRedirects` array of the UAT MCP configuration, restart only that service, and verify client registration plus authorization-page access. Repeat against production after the UAT check passes. Preserve all existing entries. Do not enable wildcard hosts, arbitrary ports or external HTTP redirects.

Treat the callback addition as a configuration release: keep a protected backup outside the repository, preserve file ownership and permissions, write atomically, and check service health after restarting. Restore the protected backup and restart the affected service if validation fails. Application source, database schema and customer permissions do not need changes.

Do not publish runtime configuration, client registrations, OAuth state, session cookies, credentials or token responses. Report only HTTP status and pass/fail evidence. The callback accepts a short-lived OAuth code on the user's own computer; it is not a public webhook.
