---
name: hushdrop
description: "Publish/share an artifact (HTML, Markdown, PDF, file, or whole site) as a private, branded, password-protected link on your own domain. Use when the user says 'publish this', 'share this', 'drop this', 'send them a link', or whenever you've generated an HTML artifact they'll want to open in a browser. Zero-knowledge AES-256, ~1s. Zero-setup via --managed; self-host on your own domain."
license: MIT
---

# Hushdrop — share what you build as a private link

When the user wants to **share, publish, or get a link** for something you made (an HTML page,
report, dashboard, doc, or file), use Hushdrop. It returns a private, branded, password-protected
link — encrypted in the browser, so the server never sees the content.

## Publish (no install needed — npx fetches on demand)

```bash
npx -y hushdrop <file>            # brand + auto-password + upload -> clean URL
npx -y hushdrop <file> --managed  # zero-setup public link, auto-expires in 24h (no account)
npx -y hushdrop <file> -p secret  # set your own password
npx -y hushdrop <file> --no-lock  # public (no password)
npx -y hushdrop <file> --burn     # self-destructs after first view
npx -y hushdrop <file> --expire 7d
```

Write your HTML to a file first, then run the command and return the printed URL (and password,
if locked) to the user. Add `--json` for machine-readable output (`{url, password, ...}`).

## Notes
- Locked links are **zero-knowledge** (AES-256 in the browser via StatiCrypt); the server stores only ciphertext.
- The managed tier is anonymous and auto-deletes in 24h. For persistent links on your own domain, the user runs `hush init` / self-hosts.
- Structured tools also available via MCP: `npx -y hushdrop-mcp` (publish_html, update_site, list_sites, delete_site, set_password, set_expiry, set_email_gate, set_feedback).

Docs & source: https://hushdrop.dev · https://github.com/maxtechera/hushdrop
