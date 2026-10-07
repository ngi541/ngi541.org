# ngi541.org

Minimal static landing page for **NGI541**.

## Architecture

- Pure HTML + CSS
- No client-side JavaScript
- No framework
- No runtime dependencies
- Cloudflare Workers Static Assets
- Security headers via `public/_headers`

## Local preview

Any static HTTP server is sufficient:

```bash
python3 -m http.server 8080 --directory public
```

Then open:

```text
http://localhost:8080
```

For Cloudflare-local behavior:

```bash
npx wrangler dev
```

## Deploy

```bash
npx wrangler deploy
```

The production custom domain should be configured as:

```text
https://ngi541.org
```

## GitHub links

The initial HTML assumes the public core repository will be:

```text
https://github.com/ngi541/ngi541
```

If the final organization/repository path differs, replace that URL in `public/index.html`
before production deployment.

## Logo

The first implementation contains a CSS wordmark matching the intended monochrome
NGI + boxed 541 direction and a temporary `public/favicon.svg`.

When the final SVG logo assets are added, replace the `.brand` content in
`public/index.html` with the final logo image and keep a textual `aria-label`.
No external fonts are required.

## Security

The deployed static site sets:

- strict Content Security Policy
- `X-Content-Type-Options: nosniff`
- `Referrer-Policy: no-referrer`
- restrictive `Permissions-Policy`
- same-origin opener/resource policies
- `/.well-known/security.txt`

HSTS is intentionally not set in `_headers` yet. Enable it only after HTTPS and all
relevant subdomains have been verified, because `includeSubDomains` can affect other
services under `ngi541.org`.

## Content policy

The landing intentionally avoids comparative performance claims until a controlled
benchmark dataset exists.

The NIST wording must remain specific to **ACVTS Demo validation A11030** and must not
be changed to “CAVP validated”, “FIPS validated”, or “NIST certified” without a future
formal validation basis.

## License

Website source is provided under Apache License 2.0.
