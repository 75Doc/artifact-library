---
id: rf-01
title: Ramverk för kravspecifikation av fastighetssystem
version: 1.0
status: stable
type: framework
domain: requirements-engineering
tags: [requirements, property-management, system-neutral, procurement, framework]
created: 2026-02-05
last_updated: 2026-02-05
created_with: ChatGPT (Strukturarkitekt-läge)
related_artifacts: [DL-01, CL-01, PR-01]
applicability: [property-management, public-sector, procurement, system-specification]
---

# RF-01 – Ramverk för kravspecifikation av fastighetssystem

**Version:** v1  
**Status:** Stabil – avsedd för återanvändning  
**Typ:** Ramverk  
**Skapad via:** ChatGPT (Strukturarkitekt-läge)

## Syfte

Att möjliggöra framtagning och iterering av en kravspecifikation för fastighetssystem som:

- är systemneutral i tidiga skeden
- kan användas oavsett om lösningen blir ett eller flera system
- fungerar som gemensam struktur för verksamhet, IT och upphandling
- stödjer både utforskande och beslutsfattande

**Ramverket ska minska risken för tidig inlåsning i teknik, leverantör eller arkitektur.**

## Ramverkets struktur

### Lager 1 – Funktionsområden (vad, inte hur)

Identifiera och strukturera verksamhetens behov i tydliga funktionsområden, exempelvis:

- Hyresavisering
- Ärendehantering / serviceanmälan
- Myndighetsbesiktningar
- Fastighetsregister

**Princip:** Funktionsområden definieras oberoende av systemgränser.

### Lager 2 – Kravtyper

För varje funktionsområde delas kraven upp i:

- **Funktionella krav**
- **Informationskrav** (data, metadata, spårbarhet)
- **Icke-funktionella krav** (säkerhet, tillgänglighet, prestanda m.m.)
- **Integrationskrav**

**Syfte:** Undvika sammanblandade krav som försvårar analys, prioritering och upphandling.

### Lager 3 – Mognads- och ambitionsnivå

Varje krav uttrycks med en tydlig ambitionsnivå, t.ex.:

- **Bas** – måste fungera vid införande
- **Utökad** – effektivisering eller förbättring
- **Strategisk** – möjliggör framtida utveckling

**Syfte:** Stödja stegvis införande och realistisk kravställning.

### Lager 4 – Systemneutralitet

Varje krav granskas mot frågan:

> "Förutsätter detta ett visst system, en viss teknisk lösning eller leverantör?"

**Om ja** → kravet omformuleras.

**Syfte:** Säkerställa lång livslängd och återanvändbarhet.

## Användningsområden

### A. Tidig kravinsamling

- Strukturera behov utan att ta arkitekturbeslut
- Fokusera på problem, flöden och information

### B. Upphandling

- Använd ramverket oavsett om lösningen blir ett eller flera system
- Underlag för jämförbar utvärdering

### C. Workshop & förankring

- Ger gemensamt språk mellan verksamhet och IT
- Fungerar även för deltagare med låg teknisk mognad

## Relaterade / framtida artefakter

- **DL-01** – Beslutslogik: ett fastighetssystem vs flera
- **CL-01** – Checklista: systemneutrala krav
- **PR-01** – Princip: verksamhetsbehov före systemstruktur

## Kommentar

Ramverket är avsett att användas och vidareutvecklas.

**Perfektion är inte målet – användbarhet är det.**
