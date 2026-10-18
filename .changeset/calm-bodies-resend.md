---
"wrangler": patch
---

Resend a small request body when `wrangler dev` meets a dropped connection to your Worker

A request that arrives just as an idle internal connection closes fails with `Network connection lost.`, even though your Worker never received it. `wrangler dev` already retried `GET` and `HEAD` requests in this case; it now also retries a bodyless `OPTIONS` (a CORS preflight), and resends any other request once if its body is under 1 MB with a known `Content-Length`, from a copy read on arrival. Larger or streamed bodies are forwarded as before and are not retried. If your Worker had in fact started handling the first attempt, its handler runs twice; this applies to local development only.
