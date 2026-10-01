# Security Policy

## Handling

UNCLASSIFIED // FOR OFFICIAL USE // SAC-219 PANEL ONLY.
Do not enter classified, controlled, or personally identifying information into any field of this instrument.

## Architecture

WinterStorm2045 is a **client-side-only** single HTML file. There is no Auracelle-operated backend, database, or account system.

- All game logic, scoring, and scenario data run in the user's browser.
- Third-party libraries (pdf.js, mammoth.js, tesseract.js, three.js) are embedded in `index.html` and unpacked at load time. The only remaining CDN reference is a fallback path for the pdf.js worker, used only if the embedded worker fails to load.
- Session state is stored in the browser's `localStorage` on the local device only.

## Access control — important limitation

The login screen is a **soft access gate for presentation purposes, not authentication.** Credentials are checked in client-side JavaScript, so anyone who can load the page can read them from the page source. Do not treat the login as protecting the content, and do not reuse these access codes anywhere else.

If the repository or Pages site must be genuinely restricted, use a private repository with access controls at the hosting layer (e.g. GitHub Enterprise private Pages, or an authenticated reverse proxy).

## Outbound network requests

The page may attempt requests to the following third parties. Each fails gracefully when unreachable.

| Purpose | Destination |
|---|---|
| Environmental conditions | `api.weather.gov`, `api.tidesandcurrents.noaa.gov` (NOAA / NWS) |
| OSINT Feed | `api.gdeltproject.org` |
| 3D terrain imagery / elevation | `server.arcgisonline.com`, `s3.amazonaws.com` (Terrarium tiles) |
| Agentic AI moves | `api.anthropic.com` (no key is embedded; falls back to local move pools) |
| pdf.js worker fallback | `cdnjs.cloudflare.com` |

These requests reveal the viewer's IP address and approximate request timing to the destination services. For air-gapped or sensitive venues, run the file on a machine with network access disabled; the core wargame remains functional.

## File uploads

Documents loaded into Narrative Analysis (PDF, DOCX, images for OCR) are parsed locally in the browser and are not uploaded anywhere by the instrument.

## Reporting a vulnerability

Please report suspected vulnerabilities privately to Grace-Alice Evans, Auracelle AI Governance Labs LLC, rather than opening a public issue. Include the affected build (shown on the login screen), steps to reproduce, and impact. Reports will be acknowledged as soon as practicable.
