# Artifact Library

Ett bibliotek av återanvändbara konceptuella artefakter för organisationsutveckling, systemutveckling och processer.

## Syfte

Detta bibliotek samlar strukturerade, systemneutrala artefakter som kan:
- Återanvändas i olika projekt och kontexter
- Konsumeras av LLM:er och andra tjänster
- Användas som grund för beslut och dokumentation
- Vidareutvecklas och itereras över tid

## Struktur

```
artifact-library/
├── concepts/
│   ├── organizational-models/    # Organisationsstrukturer och styrmodeller
│   ├── frameworks/                # Ramverk och metodiker
│   ├── processes/                 # Processmodeller
│   └── decision-models/           # Beslutslogik och mallar
├── templates/                     # Återanvändbara mallar
└── visualizations/                # Diagram och visualiseringar
```

## Artefakter

### Konceptuella modeller

#### Organisationsmodeller
- **[A1 - Projekt- och portföljkarta v0.2](concepts/organizational-models/project-portfolio-map-v0.2.md)** (LÅST)
  - Styrmodell för projekt, program och portföljer
  - Organisation som dimension, inte nivå
  - Anpassad för offentlig sektor

#### Ramverk
- **[RF-01 - Ramverk för kravspecifikation av fastighetssystem](concepts/frameworks/rf-01-requirements-framework.md)** (STABIL)
  - Systemneutral kravhantering
  - Stöd för upphandling och beslutsfattande
  - Fyrlagarmodell: Funktionsområden → Kravtyper → Ambitionsnivå → Systemneutralitet

## Hur artefakterna används

### För människor
- Navigera genom mappstrukturen
- Läs markdown-filerna direkt i GitHub
- Använd som grund för diskussioner och beslut

### För LLM:er och tjänster
- Varje artefakt har YAML frontmatter med metadata
- Direkt åtkomst via raw GitHub URLs
- Strukturerad formatering för enkel parsing

**Exempel på URL för programmatisk åtkomst:**
```
https://raw.githubusercontent.com/75Doc/artifact-library/main/concepts/frameworks/rf-01-requirements-framework.md
```

## Metadata-format

Varje artefakt innehåller:
```yaml
---
id: [unik identifierare]
title: [beskrivande titel]
version: [versionsnummer]
status: [locked/stable/draft]
type: [organizational-model/framework/process/template]
domain: [ämnesområde]
tags: [sökbara nyckelord]
created: [datum]
last_updated: [datum]
related_artifacts: [kopplingar till andra artefakter]
applicability: [användningsområden]
---
```

## Status-nivåer

- **LOCKED** (LÅST) - Fastställd, används i produktion, inga ändringar utan formellt beslut
- **STABLE** (STABIL) - Testad och godkänd för återanvändning, kan itereras
- **DRAFT** (UTKAST) - Under utveckling, inte redo för produktion

## Bidra

Artefakter läggs till genom:
1. Skapa ny fil i rätt kategori
2. Använd metadata-formatet
3. Skriv tydlig, systemneutral text
4. Länka till relaterade artefakter

## Principer

- **Systemneutralitet** - Undvik tekniska låsningar
- **Återanvändbarhet** - Skriv generellt, inte projektspecifikt
- **Användbarhet före perfektion** - Släpp tidigt, iterera ofta
- **Tydlig versionering** - Spåra förändringar över tid

## Framtida utveckling

Planerade artefakter:
- DL-01 - Beslutslogik: ett fastighetssystem vs flera
- CL-01 - Checklista: systemneutrala krav
- PR-01 - Princip: verksamhetsbehov före systemstruktur

## Licens

[Lägg till licensinformation efter behov]

## Kontakt

[Lägg till kontaktinformation efter behov]
