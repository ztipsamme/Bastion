# Teknisk leveransrapport

**Uppdrag:** Bastion

**Konsultteam:** [Teammedlemmarnas namn]

**Datum:** [Datum]

**Version:** 1.0

---

## Sammanfattning

[2–4 meningar]

---

## Vad som levereras

### Inkluderat i leveransen

| Komponent | Teknisk lösning | Status      |
| --------- | --------------- | ----------- |
|           |                 | ✅ Levererat |


### Utanför leveransens scope

Följande punkter identifierades under uppdraget men ingår inte i denna leverans. De rekommenderas som nästa steg.

| Punkt  | Motivering |
| ------ | ---------- |
| [Text] | [Text]     |

---

## Arkitektur

### Systemdiagram

```
Some Mermaid-diagram
```

> Ersätt med ett faktiskt Mermaid-diagram eller bild.

### Motiverade arkitekturval

[2–4 meningar per grej]

---

## Säkerhetsarkitektur

### Identitet och åtkomst

| Resurs | Åtkomstkontroll |
| ------ | --------------- |
| [Text] | [Text]          |

### Hemlighetshantering

Inga credentials lagras i källkod eller git-historik. Alla hemligheter hanteras via Azure DevOps pipeline-secrets och refereras som miljövariabler i Container App.

### Kvarvarande risker

| Risk   | Sannolikhet | Åtgärd |
| ------ | ----------- | ------ |
| [Text] | [Text]      | [Text] |

---

## Kostnadskalkyl

### Månadskostnad vid lansering

| Resurs | SKU    | Uppskattad kostnad/mån |
| ------ | ------ | ---------------------- |
| [Text] | [Text] | [Text]                 |


> Beräknat med [antal] X per månad. Källa: Azure Pricing Calculator.

### Skalningspunkt

[Beskriv var flaskhalsen uppstår om trafiken ökar. Vilken resurs når sin gräns först? Vad händer då, och vad kostar det att skala upp?]

---

## Rekommendationer inför produktionssättning

1.
2.
3.

---

## Överlämning

| Leverabel | Plats  |
| --------- | ------ |
| [Text]    | [Text] |   

---

*Rapporten är upprättad av konsultteamet som ett avslutande leveransdokument. Frågor hänvisas till teamet via [X].*