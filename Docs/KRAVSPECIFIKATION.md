# Kravspecifikation: Bastion

*Tower defense-spel med WPF-klient, webb-API och molndrift*

**Tidsram:** 2 veckor (ish)  
**Plattform:** .NET 8, WPF, ASP.NET Core, Azure

## 1. Bakgrund och syfte

I uppgiften ska du designa och bygga ett komplett system bestående av ett spel (WPF-klient), ett backend-API och en molndriftsatt databas. Syftet är att träna på lagerindelad arkitektur, MVVM, REST-API:er, databasåtkomst, autentisering och driftsättning i molnet.

Spelet "Bastion" är ett tower defense-spel där spelaren placerar torn längs en bana för att stoppa vågor av fiender. Resultat sparas online i en topplista.

## 2. Systemöversikt och arkitektur

Lösningen ska bestå av en solution med följande projekt:

| Projekt | Typ | Ansvar |
|---|---|---|
| Bastion.Core | Class Library | Spellogik (fiender, torn, projektiler, vågor, poäng). Inga beroenden till WPF, nätverk eller databas. |
| Bastion.Contracts | Class Library | DTO:er som delas mellan klient och API. |
| Bastion.Api | ASP.NET Core Web API | Autentisering, highscore, databasåtkomst. |
| Bastion.Wpf | WPF-applikation | Användargränssnitt, spelloop, API-anrop. |
| Bastion.Tests | Testprojekt | Enhetstester för Core och API. |

## 3. Funktionella krav

Prioritet: **Ska** = måste uppfyllas, **Bör** = bör uppfyllas, **Kan** = bonus.

### 3.1 Spelet (klient)

| ID | Krav | Prio |
|---|---|---|
| F1 | Spelet visar en karta med en förutbestämd bana på ett rutnät. | Ska |
| F2 | Fiender följer banan och har liv som visas med en HP-stapel. | Ska |
| F3 | Spelaren kan placera torn på tillåtna rutor med musklick. | Ska |
| F4 | Torn väljer mål inom räckvidd och skjuter projektiler som gör skada. | Ska |
| F5 | Spelaren tjänar pengar för besegrade fiender och betalar för torn. | Ska |
| F6 | Fiender organiseras i vågor med stigande svårighetsgrad. | Ska |
| F7 | Spelaren har ett antal liv. Spelet är slut när liven tar slut. | Ska |
| F8 | Minst två tornstyper och två fiendetyper med olika egenskaper. | Bör |
| F9 | Torn kan uppgraderas och säljas. | Bör |
| F10 | Pausfunktion och dubbel hastighet. | Kan |
| F11 | Ljudeffekter. | Kan |

### 3.2 Konton och highscore

| ID | Krav | Prio |
|---|---|---|
| F12 | Användare kan registrera konto och logga in. | Ska |
| F13 | Efter avslutat spel skickas resultatet till API:t och sparas. | Ska |
| F14 | Klienten visar en topplista över de bästa resultaten. | Ska |
| F15 | Topplistan kan filtreras (t.ex. senaste veckan). | Kan |
| F16 | Spelet kan sparas till och laddas från molnet. | Kan |
| F17 | Daglig utmaning med ett gemensamt seed för alla spelare. | Kan |

## 4. Tekniska krav

| ID | Krav |
|---|---|
| T1 | Klienten ska följa MVVM-mönstret: inga spelregler i code-behind, kommandon via `ICommand`, databindning via `INotifyPropertyChanged`. |
| T2 | Spellogiken ska ligga i Bastion.Core utan referenser till `System.Windows`. |
| T3 | Core ska uppdateras med delta-tid (`Update(double deltaSeconds)`), driven av en spelloop i klienten. |
| T4 | API:t ska vara RESTful och returnera lämpliga HTTP-statuskoder. |
| T5 | Data lagras i en relationsdatabas via Entity Framework Core med migreringar. |
| T6 | Autentisering sker med JWT. Lösenord ska lagras hashade. |
| T7 | Hemligheter (connection strings, nycklar) får inte ligga i källkoden. |
| T8 | API:t och databasen ska vara driftsatta i molnet (Azure eller motsvarande). |
| T9 | Bygg, test och driftsättning ska automatiseras med CI/CD (t.ex. GitHub Actions). |
| T10 | Klienten ska hantera nätverksfel utan att krascha och ge användaren begripligt felmeddelande. |

## 5. Kvalitetskrav

- Koden ska vara läsbar och konsekvent namngiven.
- Core ska ha enhetstester som täcker minst skademodell, målval och vågsgenerering.
- API:t ska ha minst ett integrationstest eller enhetstester för sina endpoints.
- Indata till API:t ska valideras.
- Versionshantering med Git, med tydliga commit-meddelanden.

## 6. Avgränsningar

- Spelet behöver inte ha avancerad grafik. Enkla former och färger är tillräckligt.
- Ingen flerspelarfunktion i realtid.
- Ingen mobil- eller webbklient.

## 7. Leverabler

1. Källkod i ett Git-repository med solution enligt avsnitt 2.
2. En körande, driftsatt instans av API:t (länk till publik URL).
3. README med instruktioner för att bygga och köra lokalt, samt beskrivning av arkitekturen.
4. Ett arkitekturdiagram över klient, API, databas och molnmiljö.
5. Kort reflektion (ca en sida) om designval, svårigheter och vad som skulle förbättras.
6. Demonstration av systemet.

## 8. Rekommenderad tidsplan

**Vecka 1**
- Dag 1–2: Projektstruktur, rutnät och bana.
- Dag 3: Spelloop och fiender som följer banan.
- Dag 4: Torn, projektiler och skada.
- Dag 5: API-skelett, EF Core och databas lokalt.

**Vecka 2**
- Dag 6: Registrering, inloggning och highscore-endpoints.
- Dag 7: Klienten ansluter till API:t, topplistevy.
- Dag 8: Driftsättning i molnet och CI/CD.
- Dag 9: Extrafunktioner (molnsparning eller daglig utmaning).
- Dag 10: Polish, tester, dokumentation och reflektion.

## 9. Bedömning

**Godkänt:** Alla krav med prioritet *Ska* är uppfyllda, systemet är driftsatt och leverablerna är inlämnade.

**Väl godkänt:** Dessutom uppfylls de flesta krav med prioritet *Bör*, koden har god struktur och testtäckning, och reflektionen visar förståelse för designval och alternativ.

**Utmärkt:** Dessutom har minst ett *Kan*-krav implementerats väl, till exempel molnsparning eller daglig utmaning med servervalidering via Core.