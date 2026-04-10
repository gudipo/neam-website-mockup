# Agent Instructions

You're working inside the **WAT framework** (Workflows, Agents, Tools). This architecture separates concerns so that probabilistic AI handles reasoning while deterministic code handles execution. That separation is what makes this system reliable.

## The WAT Architecture

**Layer 1: Workflows (The Instructions)**
- Markdown SOPs stored in `workflows/`
- Each workflow defines the objective, required inputs, which tools to use, expected outputs, and how to handle edge cases
- Written in plain language, the same way you'd brief someone on your team

**Layer 2: Agents (The Decision-Maker)**
- This is your role. You're responsible for intelligent coordination.
- Read the relevant workflow, run tools in the correct sequence, handle failures gracefully, and ask clarifying questions when needed
- You connect intent to execution without trying to do everything yourself
- Example: If you need to pull data from a website, don't attempt it directly. Read `workflows/scrape_website.md`, figure out the required inputs, then execute `tools/scrape_single_site.py`

**Layer 3: Tools (The Execution)**
- Python scripts in `tools/` that do the actual work
- API calls, data transformations, file operations, database queries
- Credentials and API keys are stored in `.env`
- These scripts are consistent, testable, and fast

**Why this matters:** When AI tries to handle every step directly, accuracy drops fast. If each step is 90% accurate, you're down to 59% success after just five steps. By offloading execution to deterministic scripts, you stay focused on orchestration and decision-making where you excel.

## How to Operate

**1. Look for existing tools first**
Before building anything new, check `tools/` based on what your workflow requires. Only create new scripts when nothing exists for that task.

**2. Learn and adapt when things fail**
When you hit an error:
- Read the full error message and trace
- Fix the script and retest (if it uses paid API calls or credits, check with me before running again)
- Document what you learned in the workflow (rate limits, timing quirks, unexpected behavior)
- Example: You get rate-limited on an API, so you dig into the docs, discover a batch endpoint, refactor the tool to use it, verify it works, then update the workflow so this never happens again

**3. Keep workflows current**
Workflows should evolve as you learn. When you find better methods, discover constraints, or encounter recurring issues, update the workflow. That said, don't create or overwrite workflows without asking unless I explicitly tell you to. These are your instructions and need to be preserved and refined, not tossed after one use.

## The Self-Improvement Loop

Every failure is a chance to make the system stronger:
1. Identify what broke
2. Fix the tool
3. Verify the fix works
4. Update the workflow with the new approach
5. Move on with a more robust system

This loop is how the framework improves over time.

## File Structure

**What goes where:**
- **Deliverables**: Final outputs go to cloud services (Google Sheets, Slides, etc.) where I can access them directly
- **Intermediates**: Temporary processing files that can be regenerated

**Directory layout:**
```
.tmp/           # Temporary files (scraped data, intermediate exports). Regenerated as needed.
tools/          # Python scripts for deterministic execution
workflows/      # Markdown SOPs defining what to do and how
.env            # API keys and environment variables (NEVER store secrets anywhere else)
credentials.json, token.json  # Google OAuth (gitignored)
```

**Core principle:** Local files are just for processing. Anything I need to see or use lives in cloud services. Everything in `.tmp/` is disposable.

## Bottom Line

You sit between what I want (workflows) and what actually gets done (tools). Your job is to read instructions, make smart decisions, call the right tools, recover from errors, and keep improving the system as you go.

Stay pragmatic. Stay reliable. Keep learning.

## Costs
give regularly information about the costs of the operations

---

## Projekt: neam.de Website-Optimierung

### Unternehmen

**neam IT-Services GmbH** – IT-Dienstleister und Informationssicherheitsberater mit Sitz in Paderborn (HQ) und Wiesbaden.  
Gegründet 1996 · 100+ IT-Fachleute · deutschlandweit tätig  
Teil der **Connexta Unternehmensgruppe** – einem Verbund aus 15 spezialisierten IT-Unternehmen ("IT. Gemeinsam. Stärker").  
~700 Mitarbeitende · 18 Standorte · ~5.500 Kunden · ~180 Mio. € Gruppenumsatz  
**Lünendonk-Liste 2025:** Connexta auf Rang 18 der größten IT-Dienstleister Deutschlands (Inlandsumsatz) · **ChannelPartner 2026:** 8 Connexta-Gesellschaften unter "Deutschlands beste IT-Dienstleister" (von ~900 evaluierten nur 76 ausgezeichnet)  
Zertifizierungen (neam): ISO 9001, ISO 27001 · Mitglied im BSI-Cybersicherheitsnetzwerk · Sophos Campaign of the Year 2025

### Leistungssäulen

1. **IT Services** – Microsoft 365 Modern Workplace, Managed IT, Datacenter, Netzwerk, 24/7-Support
2. **Informationssicherheit** – ISMS-Beratung, ISO 27001, BSI IT-Grundschutz, TISAX, NIS2, KRITIS, Penetration Testing, Incident Response
3. **Schulungen & Webinare** – BSI- und ISO-zertifizierte Trainings, NIS2, Security Awareness; Trainer sind aktive Praktiker aus dem Kundengeschäft (kein reines Dozententum)

### USPs (Alleinstellungsmerkmale)

- **IT-Service + vollständige IT-Sicherheit aus einer Hand** – Über 100 Spezialisten decken beide Bereiche ab, ohne externe Schnittstellen-Verluste
- **Connexta-Gruppe (15 spezialisierte IT-Unternehmen, Lünendonk Rang 18)** – "IT. Gemeinsam. Stärker": ~700 Experten, ~5.500 Kunden, ~€180 Mio. Umsatz; Zugang zu Kompetenzen in allen IT-Bereichen inkl. Multi-Cloud und KI; neam ist der Security- und Infrastruktur-Spezialist im Verbund
- **Erfahrung im öffentlichen Sektor** – Langjährige Betreuung öffentlicher Einrichtungen, KRITIS-Know-how
- **Praxistrainer** – Security-Schulungen von Experten, die täglich im Kundenprojekt arbeiten
- **Deutschlandweit** – Kein regionaler Nischenanbieter

### Zielgruppe (Entscheider-Triade)

- **IT-Leiter / CIO** – Sucht verlässlichen, langfristigen IT-Partner
- **Geschäftsführer / CFO** – Fokus: Compliance-Risiko, Haftung, ROI
- **CISO / Security-Manager** – Sucht kompetenten Partner für Zertifizierung und Risikoreduktion

Alle drei können Entscheider oder Beeinflusser sein → Inhalte müssen auf allen drei Ebenen funktionieren.

### Projekt-Ziele

1. **AI SEO / Authority** – Sichtbarkeit in KI-generierten Antworten (Google SGE, ChatGPT, Perplexity) durch Longtail-Content, klare Expertise-Signale, strukturierte Daten (E-E-A-T)
2. **Trustworthiness** – Referenzen, Zertifizierungen, Connexta-Gruppe und praxisnahe Experten stärker in den Vordergrund
3. **Conversion / Leadgenerierung** – User soll nicht abspringen, um andere Anbieter zu suchen; klare CTAs, niedrigschwellige Einstiegspunkte
4. **Strukturbereinigung IT-Services** – Aktuell zu kleinteilig und inhaltlich doppelt; Konsolidierung und bessere Übersicht nötig

### Priorisierte Seiten (Phase 1)

| Priorität | Seite | Kern-Problem |
|-----------|-------|--------------|
| 1 | NIS2-Compliance | Hohe Suchnachfrage, aktuelles Thema – maximaler Traffic-Impact |
| 2 | Informationssicherheit / ISMS / ISO 27001 | Kern-USP, Authority stärken |
| 3 | IT-Services (Übersicht) | Struktur komplett überarbeiten, Doppelungen entfernen |
| 4 | Startseite | Übergreifende Positionierung, USPs, Trust-Signale, CTAs |

### Tone of Voice

Mischung aus:
- **Kompetent & sachlich** – Auf Augenhöhe mit IT-Profis
- **Persönlich & vertrauensvoll** – Menschlich, nahbar, nicht kühl-korporativ
- **Klar & handlungsorientiert** – Konkreter Nutzen, klarer nächster Schritt

Sprache: Deutsch. Kein Fachjargon-Overkill, aber keine Vereinfachung auf Kosten der Glaubwürdigkeit.

### Trust-Content (verfügbar)

- Referenzen und Case Studies vorhanden (freigegeben zur Nutzung)
- Zertifizierungen: ISO 9001, ISO 27001, BSI-Netzwerk, Sophos Partner
- Connexta-Gruppe als starker Trust-Anker: Lünendonk-Liste 2025 Rang 18, 8 Gesellschaften bei ChannelPartner "Deutschlands beste IT-Dienstleister 2026", ~€180 Mio. Umsatz
- Quantifizierbare Aussagen wo möglich (25+ Jahre, 100+ Experten, deutschlandweit etc.)

### AI SEO Strategie

- **Longtail-First:** Spezifische Anfragen (z.B. "NIS2 Umsetzung Mittelstand", "ISO 27001 Beratung öffentliche Einrichtungen") werden von KI-Systemen eher direkt verlinkt als generische Begriffe
- **E-E-A-T stärken:** Experience, Expertise, Authoritativeness, Trustworthiness durch Autorenprofile, Zertifizierungshinweise, konkrete Projekterfahrungen
- **Strukturierte Daten:** Schema.org Markup für Organization, Service, FAQPage, BreadcrumbList
- **Connexta-Verbund nutzen:** neam als Security- und Infrastruktur-Spezialist innerhalb eines 15-Unternehmen-Netzwerks positionieren

### Technischer Stack

- **CMS:** WordPress mit Elementor Page Builder
- **Zugriff:** Direkter CMS-Zugriff vorhanden
- **Workflow:** Inhaltsoptimierungen werden in WordPress umgesetzt; ggf. HTML/CSS-Anpassungen direkt im Editor

### Scope & Einschränkungen

- **Design bleibt unverändert** – Layout, Farbwelt, Typografie und grundlegende Designsprache werden nicht angefasst. Kein Redesign, keine Layout-Umbauten.
- **Bilder können ausgetauscht werden** – wenn Bildmotive inhaltlich nicht passen oder die Bildwelt gestärkt werden soll.
- **Fokus liegt auf Inhalt** – Texte, Überschriften, Struktur der Inhalte, CTAs, Trust-Elemente.
- Aufwand soll überschaubar bleiben – keine unnötigen technischen Umbauten.

### Arbeitsweise in diesem Projekt

- Vor jeder Überarbeitung die aktuelle Seite per WebFetch analysieren
- Immer zuerst Struktur und Botschaft klären, dann Text formulieren
- Conversion-Elemente (CTAs, Lead-Magneten, Trust-Blöcke) stets mitdenken
- Änderungsvorschläge immer mit Begründung (warum besser für AI SEO / Conversion)
- Keine Design- oder Layout-Änderungen vorschlagen – ausschließlich Inhalte
- Keine Änderungen ohne Freigabe durch den User einspielen
