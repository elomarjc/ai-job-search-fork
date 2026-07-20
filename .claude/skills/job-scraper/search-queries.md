# Search Queries for Job Scraper

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`; Danish demos (`jobindex-search`, `jobnet-search`, `jobdanmark-search`, `jobbank-search`) are included the same way. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

## Search Sites

Primary:
- **jobindex.dk** - Denmark's largest job index
- **linkedin.com/jobs** - LinkedIn job listings (filter: Denmark / Aalborg)
- **jobbank.dk** - Akademikernes Jobbank (highly educated / graduate jobs)
- **jobnet.dk** - Danish Jobnet portal

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for known target companies (e.g. GomSpace, Space Inventor, Norlys, Netcompany, Netic, Trifork)

## Query Categories

Queries are grouped by priority. Each query should be combined with your location terms (e.g., Aalborg, North Denmark / Nordjylland).

### Priority 1: Embedded Software / Signal Processing

These match your strongest and most desired career direction.

```
site:jobindex.dk "embedded software" Aalborg
site:jobindex.dk "signalbehandling" OR "signal processing" Aalborg
site:jobindex.dk "microcontroller" OR "firmware" Aalborg
site:linkedin.com/jobs "embedded software" Denmark
```

### Priority 2: Electronic Systems & AI/ML

These match your electronic systems and ML domain expertise.

```
site:jobindex.dk "elektronik" Aalborg OR Nordjylland
site:jobindex.dk "machine learning" OR "AI" Aalborg
site:linkedin.com/jobs "electronic engineering" Aalborg Denmark
```

### Priority 3: Software Engineering & Web / Mobile Dev

Adjacent roles you could pivot into.

```
site:jobindex.dk "softwareudvikler" C# Aalborg
site:jobindex.dk "software engineer" python Aalborg
site:jobindex.dk "webudvikler" OR "WordPress" Aalborg
site:jobindex.dk "flutter" OR "mobile" Denmark
```

### Priority 4: Network & IT Administration

Wider net for network engineering, IT support, and systems administration.

```
site:jobindex.dk "netværksingeniør" OR "network engineer" Aalborg
site:jobindex.dk "it-support" OR "it-supporter" Aalborg
site:jobindex.dk "systemadministrator" Aalborg
```

## Location Filter

When evaluating results, verify the job location is within reasonable commute distance from your home. Define acceptable areas:
- Aalborg and surrounding areas (Nørresundby, Svenstrup, Gistrup) - **Ideal (0-20 min)**
- Støvring, Nibe, Brønderslev - **Acceptable (~20-30 min)**
- Hjørring, Frederikshavn, Hobro - **Borderline (~45-60 min by transit/car)**
- Aarhus, Copenhagen, Odense - **Too far (unless fully remote)**

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
