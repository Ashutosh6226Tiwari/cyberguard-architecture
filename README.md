# CyberGuard Architecture & System Design

Interactive architectural diagrams and system models for [CyberGuard](https://github.com/Ashutosh6226Tiwari/app.cyberguard), a native Android link-safety firewall and browser interceptor.

## Overview

CyberGuard intercepts incoming links (`ACTION_VIEW` and `ACTION_SEND` intents) from messaging apps, SMS, and emails, evaluating them against 15 on-device lexical heuristics, Google DNS-over-HTTPS (DoH), and ICANN RDAP registration age before opening the target in a browser—guaranteeing zero-fetch safety against phishing and credential harvesters.

## Diagrams

All diagrams are self-contained, interactive offline HTML artifacts built with [Archify](https://archify.si):

1. **[Runtime Architecture (`architecture.html`)](architecture.html)**
   * **Scope**: High-level component topology across 12 components.
   * **Highlights**: Android OS sandbox boundary, zero-fetch scan engine, Room SQLite persistence, and loop prevention via `BrowserHelper`.
   * **Source**: [`architecture.json`](architecture.json)

2. **[Interception Sequence (`sequence.html`)](sequence.html)**
   * **Scope**: Request execution trace for an intercepted link.
   * **Highlights**: Intent interception &rarr; URI sanitization &rarr; parallel async heuristics & DNS/RDAP queries &rarr; risk scoring &rarr; browser handoff.
   * **Source**: [`sequence.json`](sequence.json)

3. **[Trust Boundary & Data Flow (`dataflow.html`)](dataflow.html)**
   * **Scope**: 5-stage data custody and privacy lineage.
   * **Highlights**: Proves that raw URLs, query tokens, and auth secrets stay exclusively in volatile device memory, while only isolated domain names leave the device for DoH and RDAP lookups.
   * **Source**: [`dataflow.json`](dataflow.json)

4. **[Scanned Link Lifecycle (`lifecycle.html`)](lifecycle.html)**
   * **Scope**: Link state transition graph.
   * **Highlights**: Maps the full lifecycle across `Received`, `Scanning`, `Safe`, `Suspicious`, `Blocked`, and `Opened` states.
   * **Source**: [`lifecycle.json`](lifecycle.json)

## Quick Start

Open `index.html` in any modern web browser:
```bash
# Windows
start index.html

# macOS
open index.html

# Linux
xdg-open index.html
```
No build step, Node.js server, or external network access is required to view the diagrams.
