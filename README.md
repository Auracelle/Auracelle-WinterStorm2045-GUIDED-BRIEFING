# Auracelle WinterStorm2045 — Decision Intelligence Instrument

**Live v27 · Guided Briefing build** (login build tag: `Demo v1-093026`)

WinterStorm2045 is a governance-capacity wargaming instrument developed for **NATO STO SAC-219 — High North Scenarios for Wargaming and Analysis**. It measures where NATO's institutional decision architecture holds, slows, or breaks under Arctic High North grey-zone competition, using the **E-IAIG-HT** framework (Evans — Intent / Autonomy / Interaction / Governance — Hierarchical Theory).

> UNCLASSIFIED // FOR OFFICIAL USE // SAC-219 PANEL ONLY
> © 2026 Auracelle AI Governance Labs LLC. Developed independently by Grace-Alice Evans. All rights reserved — see [LICENSE](LICENSE).

---

## Live demo

Hosted via GitHub Pages from the repository root:

```
https://<org-or-user>.github.io/<repository-name>/
```

Access is login-gated. Credentials are distributed to panel members separately and are not published in this repository.

---

## What this build adds: the Guided Briefing

The landing page offers two narrated, auto-played tours. Each step moves an on-screen cursor to the control being demonstrated, and audio narration (browser speech synthesis) accompanies every step. Both tours can be paused, resumed, restarted, muted, or exited at any time.

| Tour | Scope |
|---|---|
| **Simulation Tour** | 12 chapters, 56 steps — Orientation, Scenario Build, Live Theatre, every analysis tab, through to the After-Action Report |
| **Workbench Tour** | 6 chapters, 12 steps — Narrative Analysis, Governance Lab, Governance Analytics, Capability Cards, OSINT Feed |

---

## Core concept — NATO Capability Gap (Cap Gap)

Cap Gap aggregates six domain deficits into a single 0–100% value. 0% means NATO can fully respond to the current threat; 100% means governance capacity has collapsed. Every Blue decision, Red Team move, and environmental shift moves it in real time. Above 65% corresponds to the Article 4 threshold and above 85% to an Article 5 condition.

These thresholds, and the Win-Win / Win-Loss outcome bands, are **provisional analyst-defined design thresholds pending panel calibration**, not validated findings.

Two analytical layers feed Cap Gap independently: a **Technology Layer** (emerging and disruptive capabilities) and a **Science Layer** (the physical Arctic environment). A separate **Blue-Score / Red-Score** ledger tracks decision quality by risk tier, including penalties for premature or incorrect attribution.

---

## Module map

**Game section**

| # | Tab |
|---|---|
| 00 | Scenario Build |
| 01 | Live Theatre |
| 02 | Environments |
| 03 | Overview |
| 04 | Actor Analysis |
| 05 | Concession Engine |
| 06 | Cognitive Warfare |
| 07 | NATO Cap Gap |
| 08 | Decision Intelligence |
| 09 | Players Cognitive Behavior |

**Analyst Workbench section**

| # | Tab |
|---|---|
| 00 | Narrative Analysis |
| 01 | Governance Lab |
| 02 | Governance Analytics |
| 03 | Capability Cards |
| 04 | OSINT Feed |

Supporting mechanics include the Contested Negotiation Table (Access / Resource / Narrative-Legal concession trades), a five-stage Arbitration Track, the Article 4/5 Escalation Ladder, Fog of War, the Shared Move Feed, Human-vs-Human (synchronous and asynchronous) play, and an end-of-game After-Action Report.

---

## Running it

`index.html` is a single self-contained file. Fonts are system-font fallbacks, and the four supporting libraries (pdf.js and its worker, mammoth.js, tesseract.js, three.js) are embedded inside the file and unpacked in the browser on load. No build step and no install.

- **GitHub Pages:** Settings → Pages → Source: *Deploy from a branch* → `main` / root. The empty `.nojekyll` file stops Jekyll from processing the site.
- **Locally:** open `index.html` directly in a current Chromium-based browser, Firefox, or Safari. JavaScript must be enabled.

### Network behaviour

The core wargame runs without a network connection. Several features *attempt* live requests and fall back to cached or procedural data when they fail:

| Feature | Endpoint | Offline behaviour |
|---|---|---|
| Live environment intel | NOAA / NWS (`api.weather.gov`, `api.tidesandcurrents.noaa.gov`) | Falls back to scenario baseline values |
| OSINT Feed | GDELT (`api.gdeltproject.org`) | Cached fallback items |
| 3D Terrain View | ArcGIS World Imagery, AWS Terrarium elevation tiles | Procedural terrain |
| Agentic AI Red Team / suggested moves | Anthropic API | Local, scenario-keyed move pools (the standalone file carries no API key, so this path normally uses the local fallback) |

The in-app header currently reads *"Attempts live NOAA/NWS fetch — NOT for offline/air-gapped use."* For air-gapped events, treat live-data panels as illustrative.

---

## Session data

Sessions autosave to the browser's `localStorage` on the device in use, with a resume prompt and a Session Archive (capped at 50 completed sessions). Nothing is sent to a server operated by Auracelle. Clearing site data in the browser removes saved sessions.

---

## Related components

- **Lab Environment (Python)** — the quantitative companion that processes data derived from HTML wargame sessions. Maintained separately; not included in this repository.

---

## Intellectual property

The methods and systems implemented in this instrument are the subject of pending USPTO provisional patent applications. No licence is granted by publication of this repository. See [LICENSE](LICENSE) and [SECURITY.md](SECURITY.md).

## Contact

Grace-Alice Evans — Founder & Principal Investigator, Auracelle AI Governance Labs LLC
LinkedIn: [linkedin.com/in/grace-alice-evans-5a9632a3](https://www.linkedin.com/in/grace-alice-evans-5a9632a3)
