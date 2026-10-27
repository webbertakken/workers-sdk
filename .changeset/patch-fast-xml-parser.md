---
"miniflare": patch
"wrangler": patch
---

Harden XML handling in local R2 S3 requests and `wrangler pipelines` against malicious documents

Local R2's S3-compatible API and the S3 client used by `wrangler pipelines` now use a release of `fast-xml-parser` with fixes for several published advisories. Crafted XML can no longer bypass entity encoding, exhaust memory through unbounded entity expansion, or inject comments and CDATA into generated responses.
