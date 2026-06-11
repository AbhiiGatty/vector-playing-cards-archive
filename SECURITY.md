# Security Policy

## Scope

This repository is a **static asset archive** — it contains only SVG and PNG image files plus zip downloads of those same files. There is no executable code, no server, no dependencies, and no build process. The attack surface is essentially zero.

## What "security" means for this repo

| Concern | Status |
|---|---|
| Malicious SVG content (scripts embedded in SVG) | Cards are from a well-known LGPL open-source set; no `<script>` tags present |
| Supply-chain compromise (CDN serving wrong content) | jsDelivr serves files directly from this public GitHub repo — the source of truth is the commit history |
| Typosquatting / impersonation | The canonical repo is `AbhiiGatty/vector-playing-cards-archive` — verify the org name before using a CDN URL |
| Path traversal in CDN URLs | Not applicable; jsDelivr resolves GitHub paths, not arbitrary filesystem paths |

## Reporting a vulnerability

If you believe a card file contains embedded malicious content (e.g., an injected `<script>` in an SVG), or if you find evidence that a CDN URL is serving content that does not match the committed files:

1. **Do not open a public issue.**
2. Email **security@abhiigatty.com** with:
   - The affected file path(s)
   - A description of the concern
   - Steps to reproduce or verify

You will receive a response within 72 hours. If the issue is confirmed, the file will be replaced and the commit history audited.

## CDN caching note

jsDelivr caches files aggressively. If a bad file were ever committed and then corrected, the CDN cache for the old content may persist for up to 7 days. To force-bypass the cache during incident response, pin to the corrected commit SHA in the CDN URL:

```
https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@<sha>/svg/1.3/card_1_1.svg
```

## Supported versions

All versions (`svg/1.0` through `svg/1.3`) are static files committed to this repo and are equally "supported" in the sense that the files are immutable. There are no patches or security updates — the cards are art, not code.
