---
id: int-01
title: Generell kravspecifikation – Integration Fastighetssystem ↔ Ekonomisystem (Raindance)
version: 1.0
status: stable
type: specification
domain: integration-architecture
tags: [integration, property-management, finance-system, raindance, api, data-model, architecture]
created: 2026-02-09
last_updated: 2026-02-09
related_artifacts: [RF-01]
applicability: [property-management, public-sector, procurement, system-integration, finance]
---

# INT-01 – Generell kravspecifikation: Integration Fastighetssystem ↔ Ekonomisystem (Raindance)

**Typ:** Grundartefakt / huvudspec  
**Status:** Stabil, generell, återanvändbar

## Syfte och omfattning

Denna specifikation definierar krav för integration mellan fastighetssystem och ekonomisystem (Raindance) avseende:

- Överföring av kund- och fakturaunderlag
- Säkerställande av datakvalitet och spårbarhet
- Hantering av fel och avvikelser
- Säkerhets- och driftkrav

Specifikationen är systemneutral på fastighetssystemsidan och kan användas oavsett vilken teknisk lösning som väljs.

## Avgränsning

- **Mottagande system:** Raindance (ekonomisystem)
- **Sändande system:** Fastighetssystem (systemoberoende)
- **Omfattning:** Kund- och fakturaflöden
- **Omfattar ej:** Interna processer i respektive system

## Arkitekturprinciper

### Lös koppling
- Integration ska ske via väldefinierade gränssnitt
- Systemen ska kunna utvecklas oberoende av varandra
- Ändringar i ett system ska minimalt påverka det andra

### Standard före special
- Använd standardprotokoll och format där möjligt (REST API, JSON, XML, CSV)
- Speciallösningar endast när affärsmässigt motiverat
- Dokumentera och motivera alla avvikelser från standard

### Spårbarhet
- Varje transaktion ska vara spårbar från källa till mottagare
- Loggning av alla överföringar och händelser
- Möjlighet till återkoppling och felsökning

### Idempotens
- Samma meddelande ska kunna skickas flera gånger utan att skapa duplikat
- System ska hantera återförsök på ett kontrollerat sätt
- Unikt transaktions-ID för varje överföring

## Tekniska alternativ

Integrationen ska stödja **både**:

### A. API-integration (föredraget)
- RESTful API med JSON-format
- Synkron eller asynkron kommunikation
- Autentisering via API-nycklar eller OAuth 2.0

### B. Filintegration
- Strukturerade filer (CSV, XML, JSON)
- SFTP eller motsvarande säker filöverföring
- Schemalagd överföring eller händelsestyrd

## Logisk informationsmodell

### Kund
**Obligatoriska attribut:**
- Kund-ID (unikt)
- Kundtyp (privatperson / företag / organisation)
- Namn
- Kontaktinformation (adress, e-post, telefon)

**Valfria attribut:**
- Organisations-/personnummer
- Faktureringsadress (om avvikande)
- Betalningsvillkor
- Referensperson

### Faktura
**Obligatoriska attribut:**
- Faktura-ID (unikt)
- Kund-ID (referens)
- Fakturadatum
- Förfallodatum
- Totalt belopp (inklusive moms)
- Momsbelopp
- Valuta
- Status (utkast / godkänd / skickad / betald)

**Valfria attribut:**
- Referensnummer
- OCR-nummer
- Betalningsreferens
- Noteringar

### Fakturarad
**Obligatoriska attribut:**
- Rad-ID (unikt inom faktura)
- Faktura-ID (referens)
- Beskrivning
- Antal
- À-pris
- Totalt belopp (exklusive moms)
- Momssats (%)
- Momsbelopp

**Valfria attribut:**
- Artikelnummer
- Enhet (st, m², kvm, etc.)
- Period (från-datum, till-datum)
- Objektreferens

### Konteringsrad
**Obligatoriska attribut:**
- Konteringsrad-ID (unikt)
- Fakturarad-ID (referens)
- Konto
- Belopp
- Kostnadsställe

**Valfria attribut:**
- Projekt
- Aktivitet
- Dimension 1-5 (enligt ekonomisystemets struktur)

## Generella krav

### Datakvalitet

**Krav INT-01-DQ-001:**  
Alla obligatoriska fält ska vara ifyllda före överföring.

**Krav INT-01-DQ-002:**  
Dataformat ska följa definierad standard (datum: ISO 8601, belopp: decimal med 2 decimaler, etc.).

**Krav INT-01-DQ-003:**  
Kund-ID och Faktura-ID ska vara globalt unika inom organisationen.

**Krav INT-01-DQ-004:**  
Belopp ska summera korrekt (fakturarad → faktura, konteringsrad → fakturarad).

### Validering

**Krav INT-01-VAL-001:**  
Fastighetssystemet ska validera data före sändning.

**Krav INT-01-VAL-002:**  
Raindance ska validera mottagen data och returnera valideringsresultat.

**Krav INT-01-VAL-003:**  
Vid valideringsfel ska tydliga felmeddelanden returneras med:
- Felkod
- Fältnamn
- Felbeskrivning
- Förslag på åtgärd

### Felhantering

**Krav INT-01-ERR-001:**  
Alla fel ska loggas med:
- Tidsstämpel
- Transaktions-ID
- Feltyp
- Felmeddelande
- Berörd data (anonymiserad vid behov)

**Krav INT-01-ERR-002:**  
Systemet ska stödja automatisk återförsök vid temporära fel (nätverk, timeout).

**Krav INT-01-ERR-003:**  
Vid permanenta fel (datafel, valideringsfel) ska transaktionen markeras för manuell hantering.

**Krav INT-01-ERR-004:**  
Felmeddelanden ska vara begripliga för både teknisk och verksamhetspersonal.

### Säkerhet

**Krav INT-01-SEC-001:**  
All kommunikation ska ske över krypterad anslutning (TLS 1.2 eller senare).

**Krav INT-01-SEC-002:**  
Autentisering ska krävas för alla API-anrop eller filöverföringar.

**Krav INT-01-SEC-003:**  
Åtkomst ska loggas för säkerhetsrevision.

**Krav INT-01-SEC-004:**  
Känslig data (t.ex. personnummer) ska hanteras enligt GDPR.

**Krav INT-01-SEC-005:**  
API-nycklar och lösenord ska aldrig lagras i klartext.

### Drift & förvaltning

**Krav INT-01-OPS-001:**  
Integrationen ska ha en tillgänglighet på minst 99% under kontorstid.

**Krav INT-01-OPS-002:**  
Systemet ska stödja övervakning och alerting vid:
- Misslyckade transaktioner
- Ökad feltakt
- Prestandaproblem

**Krav INT-01-OPS-003:**  
Loggning ska behållas i minst 12 månader för revision och felsökning.

**Krav INT-01-OPS-004:**  
Det ska finnas dokumenterad driftinstruktion och kontaktvägar för support.

**Krav INT-01-OPS-005:**  
Planerade driftstopp ska meddelas minst 5 arbetsdagar i förväg.

## Användningsområden

- **Upphandling:** Använd som kravbilaga för fastighetssystem
- **Arkitekturunderlag:** Bas för teknisk design och implementation
- **Kontraktuell kravbilaga:** Referensdokument i avtal med leverantörer
- **Bas för fler ekonomisystem:** Kan anpassas för andra ekonomisystem än Raindance

## Relaterade artefakter

- **RF-01** – Ramverk för kravspecifikation av fastighetssystem (metodisk grund)

## Vidareutveckling

Denna specifikation kan utökas med:
- Specificering av API-endpoints och dataformat
- Exempel på JSON/XML-scheman
- Testfall och acceptanskriterier
- Integrationsmönster för specifika fastighetssystem
- Anpassningar för andra ekonomisystem

## Kommentar

Specifikationen är medvetet generell för att vara återanvändbar. Projektspecifika anpassningar ska göras i separata dokument som refererar till denna grundspec.
