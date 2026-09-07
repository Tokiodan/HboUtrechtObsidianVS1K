# MOD - Modelleren & Databases spiekbriefje

  

Overzicht van de stof uit MOD1 (introductie modelleren + databases) en MOD2 (conceptueel datamodel / ERD).

Met uitleg, voorbeelden, een stappenplan en veelgemaakte foutjes.

  

---

  

## DEEL 1: MODELLEREN

  

## 1. Wat is een model?

  

Een model is een **schematische, vereenvoudigde weergave van de werkelijkheid**. Het benadrukt een paar belangrijke aspecten en laat de rest weg. Denk aan een architect die tekeningen maakt: geen echt gebouw, maar een abstractie ervan.

  

Waarom modelleren?

- **Grip krijgen** op een complex probleem (opdelen in stukjes)

- **Structureren** van informatie

- **Communiceren** met opdrachtgevers, ontwerpers en bouwers

- **Compacte documentatie** (een plaatje zegt meer dan veel tekst)

- **Alternatieven vergelijken** en afspraken **eenduidig vastleggen**

  

Belangrijk: een model wordt altijd gemaakt voor een **specifiek doel en een specifieke gebruikersgroep**.

  

---

  

## 2. Twee soorten modellen

  

| Soort | Beschrijft | Kenmerk | Voorbeeld |

|-------|-----------|---------|-----------|

| **Structuurmodel** | hoe iets in elkaar zit | statisch (tijd speelt geen rol) | anatomie van het hart, ERD |

| **Gedragsmodel** | hoe iets werkt | dynamisch (tijd speelt wel een rol) | stappen van een hartslag, activity diagram |

  

Vaak heb je beide nodig om een compleet beeld te krijgen.

  

---

  

## 3. Syntax en semantiek

  

- **Syntax** = de symbolen en de regels om ze te combineren (de "grammatica").

- **Semantiek** = de betekenis van die symbolen.

  

Belangrijke regel: **een model heeft alleen betekenis als het wel-gevormd is** (juiste syntax). Vergelijk met taal:

- "De kat zit op de mat" = wel-gevormd, heeft betekenis.

- "De zit de op kat mat" = fout gecombineerd, geen betekenis.

  

ICT-diagrammen hebben een **eenduidige semantiek** (een formele taal): geen dubbele uitleg mogelijk. De bekendste standaard is **UML**.

  

---

  

## DEEL 2: DATABASES

  

## 4. Wat is een database?

  

Een database is een **opslagplaats voor data**. Formeel: "een collectie van persistente data".

- **Persistent** = blijft bewaard, ook als je de computer uitzet (permanent geheugen).

  

Een databasesysteem bestaat uit:

- **De database(s)** = de opslag zelf

- **Het DBMS** (Database Management System) = de software die de database beheert

  

Alle interactie (opzoeken, toevoegen, wijzigen, verwijderen) gaat via het DBMS.

  

---

  

## 5. Belangrijke functies van een databasesysteem

  

- Grote hoeveelheden gegevens opslaan, wijzigen, verwijderen

- Zorgen dat gegevens correct en compleet zijn

- Meerdere gebruikers tegelijk laten werken

- Snel zoeken en teruggeven

- Datazekerheid en -bescherming garanderen

  

**De zes pijlers:** beschikbaarheid, beheerbaarheid, herstelbaarheid, consistentie, prestaties, schaalbaarheid.

  

---

  

## 6. Relationele database (het type dat we gebruiken)

  

Gegevens worden opgeslagen in **tabellen**.

  

| Begrip | Betekenis |

|--------|-----------|

| **Tabel** | verzameling van rijen (over één soort ding, bijv. "boeken") |

| **Rij / record** | één item (bijv. één specifiek boek) |

| **Kolom / attribuut** | een eigenschap (bijv. titel, auteur) |

  

Vergelijk het met een Excel-sheet: elke rij is een item, elke kolom een eigenschap.

  

**Waarom meerdere tabellen?** Om **dubbele data te voorkomen**. Voorbeeld: als elk todo-item de gegevens van de eigenaar herhaalt (naam, email, wachtwoord), moet je bij een wachtwoordwijziging overal aanpassen. Oplossing: eigenaar in een aparte tabel, en verwijzen met een verwijskolom.

  

**RDBMS** = Relational Database Management System. Voorbeelden: MySQL, PostgreSQL, SQLite, SQL Server, Oracle. Ze praten meestal via **SQL** (Structured Query Language).

  

---

  

## DEEL 3: HET DATAONTWERPPROCES (4 fasen)

  

| Fase | Doel | Resultaat |

|------|------|-----------|

| 1. Informatie verzamelen | domein/wensen leren kennen | use cases, procesbeschrijvingen |

| 2. Conceptueel datamodel | welke gegevens, hoe gegroepeerd? | ERD met entiteiten, attributen, identificaties (merk-onafhankelijk) |

| 3. Logisch datamodel | vertalen naar relationele DB | tabellen, kolommen, sleutels (merk-onafhankelijk) |

| 4. Fysiek datamodel | vertalen naar één merk (bijv. PostgreSQL) | echte database + datatypes |

  

In dit vak begin je meestal bij fase 2, omdat je de tekst (resultaat van fase 1) al krijgt.

  

---

  

## DEEL 4: CONCEPTUEEL DATAMODEL (ERD) MAKEN

  

## 7. De belangrijkste begrippen

  

| Begrip | Betekenis | Voorbeeld |

|--------|-----------|-----------|

| **Entiteit** | een "iets", concreet of abstract (wordt later een tabel) | Boek, Lener, Uitlening |

| **Attribuut** | een eigenschap van een entiteit (wordt later een kolom) | titel, naam, begindatum |

| **Relatie** | verband tussen twee entiteiten | "een lener leent een exemplaar" |

| **Identificatie** | verplicht attribuut dat een rij uniek maakt (markeer met `*`) | ISBN bij Boek, BSN bij Persoon |

| **Kardinaliteit** | hoe vaak een relatie mag voorkomen | 1-op-veel, 0-op-veel, etc. |

  

---

  

## 8. Entiteiten en attributen vinden (de zelfstandig-naamwoord-truc)

  

1. Lees de tekst goed door.

2. **Onderstreep alle zelfstandige naamwoorden** (boek, lener, datum, ...).

3. Zet ze in een lijst.

4. Beslis per woord: is het een **entiteit** (een ding waar meerdere eigenschappen bij horen) of een **attribuut** (een losse eigenschap)?

  

Vuistregel:

- Een woord met meerdere eigenschappen eromheen → **entiteit**

- Een losse eigenschap van iets → **attribuut**

- De instelling zelf (bijv. "bibliotheek") of een actor → vaak **weglaten**

  

Voorbeeld bibliotheek: entiteiten werden **Boek, Exemplaar, Lener, Uitlening, Reservering**. Attributen bij Boek: ISBN, titel, auteur, uitgever.

  

Let op: deze truc is niet waterdicht. Je vindt niet altijd alles en soms iets verkeerds. Verder nadenken blijft nodig.

  

---

  

## 9. Relaties vinden

  

Lees de tekst nog eens en zoek **verbanden** tussen entiteiten. Schrijf ze als zin op:

- "Een boek heeft meerdere exemplaren"

- "Een uitlening registreert de lener en het exemplaar"

- "Een reservering legt vast welk boek door welke lener"

  

---

  

## 10. Kardinaliteiten (kraaienpootnotatie)

  

De kardinaliteit zegt **hoe vaak** een relatie mag voorkomen. Je bepaalt hem **altijd voor beide richtingen**.

  

De symbolen (crow's foot / kraaienpoot):

  

```

   ─┤        precies één (verplicht, 1)

   ─○┤       nul of één (optioneel, 0..1)

   ─<        veel (1 of meer aan die kant)

   ─○<       nul of veel (0 of meer)

   ─│<       één of veel (1..*)

```

- Een streepje `|` = "één" (verplicht)

- Een cirkel `○` = "nul" (optioneel / mag ook geen)

- Een kraaienpootje `<` = "veel"

  

Voorbeeld (lezen in beide richtingen):

- Boek → Exemplaar: een boek heeft **één of meer** exemplaren; een exemplaar hoort bij **precies één** boek.

- Lener → Uitlening: een lener heeft **nul, één of meer** uitleningen; een uitlening hoort bij **precies één** lener.

  

---

  

## 11. Veel-op-veel relaties

  

Soms hoort aan beide kanten "veel". Bijvoorbeeld: een lener leent veel exemplaren, en een exemplaar wordt door veel leners geleend (in de tijd). Dat is een **veel-op-veel relatie**.

  

In het conceptueel model mag dat. In het **logisch datamodel** los je het op met een **tussentabel** (koppeltabel), die dan vaak een eigen entiteit wordt (zoals "Uitlening" of "Reservering").

  

---

  

## 12. Model compleet maken

  

Voeg toe:

- Alle **attributen** per entiteit

- De **identificaties** (markeer met een `*`, bijv. `*ISBN`, `*lenersnr`)

  

Dan heb je een compleet **conceptueel datamodel**: een goede basis om met iedereen over de eisen te praten, merk-onafhankelijk.

  

---

  

## Tools voor het tekenen

  

- Pen en papier (foto/scan inleveren) voor simpele modellen

- **Visual Paradigm** (veel gebruikt door software engineers)

- Visio (Windows) of Lucidchart (Mac/Linux)

- Niet Word gebruiken voor de diagrammen

  

---

  

## Veelgemaakte foutjes

  

| Fout | Waarom het misgaat | Beter |

|------|-------------------|-------|

| De "bibliotheek" als entiteit opnemen | dat is de instelling/actor, niet de data | weglaten |

| Losse eigenschap als eigen entiteit | te veel opsplitsen | maak het een attribuut |

| Kardinaliteit maar één richting bepalen | een relatie heeft altijd 2 kanten | bepaal beide richtingen |

| Identificatie vergeten | dan kun je rijen niet onderscheiden | markeer een uniek attribuut met `*` |

| Veel-op-veel laten staan in logisch model | relationele DB kan dat niet direct | tussentabel maken |

  

---

  

## Stappenplan bij een ERD-opdracht

  

1. **Lees de beschrijving** en vat kort samen waar het over gaat.

2. **Onderstreep de zelfstandige naamwoorden.**

3. **Kies de entiteiten** (dingen met eigenschappen) en verzamel per entiteit de **attributen**.

4. **Zoek de relaties** en schrijf ze als zin op.

5. **Bepaal de kardinaliteiten** in beide richtingen (kraaienpoot).

6. **Markeer de identificaties** met een `*`.

7. **Teken het model** in Visual Paradigm (of op papier) en controleer of het klopt met de tekst.