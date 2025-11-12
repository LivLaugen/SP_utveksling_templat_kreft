# Strukturert kreftjournal – Sosialanamnese

## Innholdsfortegnelse
- [Utdanningssammendrag](#utdanningssammendrag)
- [Arbeidsstatus](#arbeidsstatus)
- [Samlivsstatus](#samlivsstatus)
- [Samlivsform](#samlivsform)
- [Omsorgsansvar_kartlegging](#omsorgsansvar_kartlegging)
- [Fritekst relatert til sosialanamnese](#fritekst-relatert-til-sosialanamnese)

---

I Strukturert kreftjournal er det utviklet et standardisert templat for opptak av sosialanamnese.  
Templatet består av følgende komponenter.

## Utdanningssammendrag

Dette brukes for å registrere et individs utdanningsnivå i forbindelse med prosjektet Strukturert kreftjournal.  

Verdisettet for dataelementet **"Høyeste fullførte utdanningsnivå"** er standardisert basert på krav utarbeidet av Helsedirektoratet.  

Templatet benyttes i sosialanamnese-delen av Strukturert kreftjournal, men småtemplatet med det standardiserte verdisettet kan også brukes utenfor prosjektet, for eksempel ved registrering av arbeidsstatus.

### Modellering

Informasjonsmodellen for registrering av utdanningssammendrag er basert på følgende arketype:  
[Utdanningssammendrag – arketyper.no](https://arketyper.no/ckm/archetypes/1078.36.2192)

#### Overordnet beskrivelse av arketyper og felter som brukes

| NodeId | Attr. | RM Type | Name | Description |
|--------|--------|---------|------|-------------|
| **Utdanningssammendrag** |  | EVALUATION: _openEHR-EHR-EVALUATION.education_summary.v1_ |  |  |
| at0002 | 0..1 | DV_CODED_TEXT | Høyeste fullførte utdanningsnivå | - Ingen utdanning (no.utdanningsnivaa: 0)  <br> - Grunnskole (no.utdanningsnivaa: 1) <br> - Videregående (no.utdanningsnivaa: 2) <br> - Universitet/Høyskole < 4 år (no.utdanningsnivaa: 3) <br> - Universitet/Høyskole ≥ 4 år (no.utdanningsnivaa: 4) <br> - Ukjent (no.utdanningsnivaa: 9) |
| at0028 | 0..1 | DV_DATE_TIME | Sist oppdatert | Oppdateres når utdanning registreres eller endres i `CLUSTER.education_record` (Utdanning). |

---

## Arbeidsstatus

Brukes for å registrere et individs arbeidsstatus i forbindelse med prosjektet Strukturert kreftjournal.  

Verdisettet for dataelementet **"Arbeidsstatus"** er standardisert basert på krav utarbeidet av Helsedirektoratet.  

Dette templatet vil bli brukt i prosjektet Strukturert Kreftjournal under sosialanamnese.

Småtemplatet med det standardiserte verdisettet kan også benyttes utenfor prosjektet.

### Modellering

Informasjonsmodellen er basert på følgende arketyper:  
- [Arbeidssammendrag – arketyper.no](https://arketyper.no/ckm/archetypes/1078.36.1945)  
- [Arbeidsforhold/rolle – arketyper.no](https://arketyper.no/ckm/archetypes/1078.36.543)  
- [Sykemelding – arketyper.no](https://arketyper.no/ckm/archetypes/1078.36.3004)

#### Overordnet beskrivelse av arketyper og felter

| NodeId | Attr. | RM Type | Name | Description |
|--------|--------|---------|------|-------------|
| **Arbeidssammendrag** |  | EVALUATION: _openEHR-EHR-EVALUATION.occupation_summary.v1_ | Arbeidsstatus | - I arbeid (no.arbeidsstatus: 1) <br> - Ikke i arbeid (no.arbeidsstatus: 2) <br> - Alderspensjonist (no.arbeidsstatus: 3) <br> - Under utdanning/studerer (no.arbeidsstatus: 4) <br> - Ukjent (no.arbeidsstatus: 9) |
| **Arbeidsforhold/rolle** |  | CLUSTER: _openEHR-EHR-CLUSTER.occupation_record.v1_ | Tittel/rolle |  |
| **Sykemelding** |  | CLUSTER: _openEHR-EHR-CLUSTER.sick_note_ous.v1_ | - Sykemelding fra dato <br> - Varighet <br> - Sist oppdatert | Beskriver periode og varighet av sykemelding. |

---

## Samlivsstatus

Brukes for å registrere et individs samlivsstatus i forbindelse med prosjektet Strukturert Kreftjournal.  
Ikke juridisk sivilstand (det registreres i PAS-delen av EPJ).  

Verdisettet er basert på SSB: [Klassifikasjon 19](https://www.ssb.no/klass/klassifikasjoner/19)

#### Modellering

Basert på: [Sosialt nettverk – arketyper.no](https://arketyper.no/ckm/archetypes/1078.36.2295)

| NodeId | Attr. | RM Type | Name | Description |
|--------|--------|---------|------|-------------|
| **Sosialt nettverk** |  | EVALUATION: _openEHR-EHR-EVALUATION.social_network.v1_ | Samlivsstatus | - Ugift/enslig (1) <br> - Gift/samboer/partner (2) <br> - Enke/enkemann/gjenlevende (3) <br> - Skilt/separert (4) <br> - Ukjent (9) |
| at0018 | 0..1 | DV_TEXT | Kommentar |  |
| at0011 | 0..1 | DV_DATE_TIME | Sist oppdatert | Når samlivsstatus sist ble oppdatert. |

---

## Samlivsform

Brukes for å registrere om individet bor alene, med noen, eller på institusjon.  
Basert på arketypen [Kartleggingsspørsmål om sosiale forhold – arketyper.no](https://arketyper.no/ckm/archetypes/1078.36.2380).

| NodeId | Attr. | RM Type | Name | Description |
|--------|--------|---------|------|-------------|
| **Kartleggingspørsmål om sosiale forhold samlivsform** |  | OBSERVATION: _openEHR-EHR-OBSERVATION.social_context_screening.v1_ | Kartleggingsformål | Samlivsform (no.onk.sosiale_forhold: SAM) |
| **Spesifikt sosialt forhold** |  | CLUSTER: _at0022_ | Hvilken samlivsform har pasienten? | - Bor alene (1) <br> - Bor med noen (2) <br> - Bor på institusjon/sykehjem (3) <br> - Ukjent (9) |

---

## Omsorgsansvar_kartlegging

Kartleggingsspørsmål om et individ har ansvar/omsorg for barn eller voksne.

Basert på [Kartleggingsspørsmål om sosiale forhold – arketyper.no](https://arketyper.no/ckm/archetypes/1078.36.2380).

| NodeId | Attr. | RM Type | Name | Description |
|--------|--------|---------|------|-------------|
| **Kartlegging omsorgsansvar** |  | OBSERVATION: _openEHR-EHR-OBSERVATION.social_context_screening.v1_ | Kartleggingsformål | Kartlegging av om individet har omsorgsansvar (no.onk.sosiale_forhold: OA) |
| **Omsorgsperson for barn under 18 år** |  | CLUSTER: _at0022_ | Har pasienten ansvar for barn under 18 år? | Ja / Nei / Ukjent |
| **Barn som pårørende** |  | CLUSTER: _at0022_ | Finnes det barn som pårørende? | Ja / Nei / Ukjent |
| **Omsorgsperson for personer over 18 år** |  | CLUSTER: _at0022_ | Har pasienten ansvar for egne barn/andre over 18 år? | Ja / Nei / Ukjent |

---

## Fritekst relatert til sosialanamnese

Basert på [Tidfestet fritekst – arketyper.no](https://arketyper.no/ckm/archetypes/1078.36.1999)

| NodeId | Attr. | RM Type | Name | Description |
|--------|--------|---------|------|-------------|
| **Fritekst relatert til sosial anamnese** |  | OBSERVATION: _openEHR-EHR-OBSERVATION.progress_note.v1_ | Fritekst relatert til sosial anamnese | Skal ikke være med i eksport til register. |
| **Semistrukturert metadata DIPS** |  | CLUSTER: _openEHR-EHR-CLUSTER.semistrukturert_metadata_dips.v1_ | Klassifisering av informasjon | Sosial anamnese (no.dips.Freetext.Classification: 01-Oncology-Sosial-anamnese) |
"""

