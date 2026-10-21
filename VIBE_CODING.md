# Dokumentation Vibe Coding

**Projekt:** Finanzkennzahlen der Big-Tech-Unternehmen im Vergleich
**Modul:** Business Analytics, DHBW Bad Mergentheim, Digital Business Management (Dozent: Thomas Burghardt)
**Studenten:** Kris Lämmermann, Vincent Eckart

---

## 1. Methode

Vibe Coding ist eine Methode der Softwareentwicklung, bei der Anforderungen in Alltagssprache an ein Sprachmodell übermittelt werden und die KI daraufhin den Programmcode erzeugt ([Wikipedia: Vibe-Coding](https://de.wikipedia.org/wiki/Vibe-Coding)).

In diesem Projekt wurde das Sprachmodell eingesetzt, um das Jupyter Notebook mit Datenaufbereitung, Analyse, Diagrammen und Interpretationen zu erstellen. Die fachlichen Vorgaben (Datensatz, Unternehmensauswahl, Forschungsfragen) stammen aus unserem Exposé.

## 2. Eingesetzte Werkzeuge

| Werkzeug | Einsatz |
|---|---|
| Claude (Anthropic), Modell Claude Opus 5.5, in der Claude-App | Sprachmodell für Code, Analyse und Texte |
| Python 3 mit pandas, numpy, matplotlib, scipy | Datenanalyse und Visualisierung |
| Jupyter Notebook | Darstellung von Code, Ergebnissen und Interpretation |
| Git / GitHub | Versionsverwaltung und Abgabe |

Bei der Erstellung verwendete Bibliotheksversionen: pandas 3.0.5, numpy 2.5.3, matplotlib 3.11.2, scipy 1.18.1.

## 3. Prompt-Protokoll

Die folgenden Prompts wurden am **21.10.2026** im Chat mit Claude verwendet (wörtlich übernommen).

### Prompt 1: Kontext übergeben

> Hallo Claude, ich habe dir für meine Prüfungsleistung im Fach Business Analytics meine Prüfungsanforderungen, meine csv Datei als Datenbank ( mit Unternehmensdaten für den S&P 500), meine Forschungsfragen und mein Expose.

**Angehängte Dateien:** Prüfungsanforderungen (Folien „Datenprojekt“), CSV-Datei `04_company_financials1.csv`, Notizen zu den Phasen einer statistischen Untersuchung und FAIR, Forschungsfragen mit Programmieransätzen, Exposé.

**Reaktion der KI:** Die KI hat die CSV-Datei per Python geprüft (alle fünf Unternehmen und sechs Kennzahlen vorhanden) und auf drei methodische Punkte hingewiesen: unterschiedliche Geschäftsjahresenden (relevant für FF1), wenige Datenpunkte je Unternehmen (relevant für FF4 und FF5) und die Möglichkeit, FF3 zusätzlich über alle Unternehmen zu rechnen.

### Prompt 2: Notebook und Dokumentation erstellen

> Bitte erstelle mir das komplette Jupyter Notebook für Github, gegliedert nach den Phasen, mit allen Forcshungsfragen, Diagrammen und Interpretationen. Die Readme wurde schon erstellt. Bitte mach mir auch die Dokumentation des Vibe Codings. Bitte erfinde keine Daten dazu und halluziniere nicht.

**Vorgehen der KI:**
1. Erkundung der Daten (Struktur, fehlende Werte, Duplikate, Wertebereiche).
2. Berechnung aller fünf Forschungsfragen in einem Entwurfsskript, um die Ergebnisse vor dem Schreiben der Texte zu kennen.
3. Aufbau des Notebooks nach den fünf Phasen; Ausführung aller Zellen, Sichtprüfung der Diagramme, Korrektur von Layoutfehlern (überlappende Beschriftungen, doppelte Achsenwerte, verdeckte Punkte).
4. Formulierung der Interpretationen ausschließlich auf Basis der im Notebook ausgegebenen Werte.
5. Abgleich aller Zahlen in den Interpretationstexten mit den Notebook-Ausgaben.

## 4. Wichtige Erkenntnisse und Entscheidungen

Diese Punkte sind während des Vibe-Coding-Prozesses in den Daten aufgefallen. Sie sind im Notebook mit Code und Ausgabe belegt.

| Problem | Wie entdeckt | Entscheidung | Begründung |
|---|---|---|---|
| Einzelne Jahre bestehen nur aus Nullen (z. B. AAPL 2021, TSLA 2021; im Gesamtdatensatz 375 Unternehmensjahre) | Sichtung der Kennzahlen im Wide-Format | Unternehmensjahre mit `Total Revenue <= 0` werden entfernt | Ein Umsatz von 0 USD ist für S&P-500-Unternehmen nicht plausibel; die Nullen stehen für fehlende Daten und würden Mittelwerte und Wachstumsraten verfälschen |
| Unterschiedliche Geschäftsjahresenden (AAPL September, MSFT Juni, Rest Dezember) | Auswertung der Periodenenden je Unternehmen | Gruppierung nach Geschäftsjahr (Kalenderjahr des Periodenendes) statt nach exaktem Datum | Sonst stünde pro Datum oft nur ein Unternehmen |
| Nicht in jedem Geschäftsjahr sind alle fünf Unternehmen enthalten | Verfügbarkeitstabelle | Durchschnittsvergleich nur im balancierten Zeitraum 2023–2025 | Sonst entstehen scheinbare Rückgänge durch die wechselnde Zusammensetzung |
| „Aktuellste Periode“ ist nicht eindeutig | Neuestes Datum (30.06.2026) betrifft nur MSFT | Zwei Sichtweisen: letzter Abschluss je Unternehmen und gemeinsames Geschäftsjahr 2025 | Transparenter als eine einzige, willkürliche Definition |
| Doppellistungen (GOOG/GOOGL, FOX/FOXA, NWS/NWSA) | identischer Umsatz und Gewinn in derselben Periode | Für Vergleiche über den Gesamtdatensatz nur ein Symbol je Konzern | Sonst würden diese Konzerne doppelt gezählt |
| `Tax Rate For Calcs` ist nicht immer Steueraufwand / Vorsteuergewinn | eigene Nachberechnung | Prüfung im Notebook dokumentiert, Einschränkung bei FF3 genannt | z. B. TSLA 2023: berechnet −50,1 %, im Datensatz 21,0 % |
| Extreme Ausreißer bei der Nettomarge (bis −1.285,9 %) | Häufigkeitsverteilung | Zusätzlich Spearman-Korrelation und Pearson ohne 1-%-Ränder | Pearson ist empfindlich gegenüber Ausreißern |
| Unterschiedliche EPS-Niveaus | Vergleich der Mittelwerte | Neben der Standardabweichung auch Variationskoeffizient | Absolute Schwankung allein bevorzugt Unternehmen mit hohem EPS |
| Steuereffekt der Sondereffekte allein ist sehr klein | Anteil am Nettogewinn | Zusätzlich bereinigtes EPS aus `Normalized Income` | Der Zusammenhang `Normalized Income = Net Income − Total Unusual Items + Tax Effect Of Unusual Items` wurde im Notebook geprüft (Abweichung 0 USD) |
| Z-Score bei nur 3 Wachstumsraten je Unternehmen | mathematische Prüfung | Schwellenwert \|z\| > 1 statt 2; zusätzlich robuster Z-Score im Vergleich mit allen Unternehmen | Bei n = 3 ist \|z\| höchstens 1,155; der übliche Schwellenwert 2 wäre nie erreichbar |

## 5. Abweichungen vom Exposé

- **Datenqualität:** Im Exposé steht „keine fehlenden Werte in den relevanten Kennzahlen“. Formal gibt es keine NaN-Werte, inhaltlich fehlen aber Jahre, die als Nullen codiert sind (siehe oben). Dadurch hat jedes Unternehmen 4 statt 4 bis 5 auswertbare Geschäftsjahre.
- **FF2:** zwei Sichtweisen statt einer, zusätzlich Top 10 im Gesamtdatensatz (ursprüngliche Fragestellung).
- **FF3:** zusätzlich Auswertung über alle Unternehmen des Datensatzes sowie Spearman-Korrelation.
- **FF4:** zusätzlich Variationskoeffizient und bereinigtes EPS.
- **FF5:** zusätzlich robuster Z-Score im Marktvergleich.

## 6. Qualitätssicherung und Grenzen der KI-Unterstützung

**Durchgeführte Prüfschritte:**
- Alle Code-Zellen wurden von oben nach unten ausgeführt; alle Ergebnisse und Diagramme im Notebook stammen aus dieser Ausführung.
- Jedes Diagramm wurde nach dem Rendern angesehen und bei Layoutfehlern korrigiert.
- Alle Zahlen in den Interpretationstexten wurden mit den Ausgaben des Notebooks abgeglichen.
- Plausibilitätsprüfungen im Code: Duplikate, fehlende Werte, Identität von Operating Revenue und Total Revenue, Nachberechnung der Steuerquote, Prüfung von Normalized Income.

**Hinweise zur Transparenz:**
- Die Hypothesen H1 bis H5 wurden von der KI nach einer ersten Sichtung der Daten formuliert.
- In der Arbeitsumgebung der KI war Jupyter nicht installierbar. Das Notebook wurde dort mit einem eigenen Skript ausgeführt, das die Zellen nacheinander mit Python laufen lässt und die Ausgaben speichert. Vor der Abgabe sollte das Notebook einmal lokal mit „Restart Kernel and Run All“ ausgeführt werden.
- Die Originalquelle der CSV-Datei (Kaggle-Link) wurde von uns angegeben und im Notebook (Abschnitt 2.1) sowie in der README eingetragen.
- Die Verantwortung für den Inhalt liegt bei uns: Wir müssen jeden Schritt des Codes und jede Interpretation erklären können.

## 7. Weitere eigene Prompts

*(Hier tragen wir weitere Prompts ein, falls wir das Notebook nach dem 21.10.2026 mit KI-Unterstützung weiter verändern.)*

| Datum | Prompt (wörtlich) | Ergebnis / Änderung | Selbst geprüft? |
|---|---|---|---|
| | | | |
| | | | |

## 8. Leitfragen für unsere Reflexion

*(Von uns selbst zu beantworten, z. B. für die Präsentation am 30. Oktober.)*

- Welche Teile hätten wir ohne KI nicht oder nur deutlich langsamer umsetzen können?
- Wo hat die KI auf Probleme hingewiesen, die wir selbst übersehen hätten?
- Welche Ergebnisse der KI haben wir selbst nachgerechnet oder überprüft, und wie?
- Wo liegen die Risiken von Vibe Coding (z. B. Code, den man nicht versteht; unbemerkte Fehler)?
