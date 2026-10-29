# Finanzkennzahlen der Big-Tech-Unternehmen im Vergleich

**Autoren:** Kris Lämmermann, Vincent Eckart

Datenprojekt im Modul *Business Analytics* (DHBW Bad Mergentheim, Digital Business Management, Dozent: Thomas Burghardt), umgesetzt mit der Methode **Vibe Coding**.

## Kurze Beschreibung

Das Projekt analysiert die Finanzkennzahlen von fünf börsennotierten Technologieunternehmen (AAPL, MSFT, AMZN, TSLA, GOOGL) auf Basis der Datei `04_company_financials[1].csv` (S&P-500-Unternehmen, Long-Format mit den Spalten `Symbol`, `Item`, `Period`, `Value`). Aus dem Gesamtdatensatz (114.528 Zeilen, 509 Unternehmen, 84 Kennzahlen) werden die 986 Zeilen der fünf Unternehmen ausgewertet; bei zwei Forschungsfragen dient der Gesamtdatensatz zusätzlich als Vergleich. Die Ergebnisse werden in einem Jupyter Notebook visualisiert. Das Notebook ist nach den fünf Phasen einer statistischen Untersuchung gegliedert (Vorbereitung, Datenerhebung, Aufbereitung und Darstellung, Analyse, Ergebnispräsentation).

**Forschungsfragen:**

1. Wie hat sich der durchschnittliche Total Revenue über die Perioden entwickelt?
2. Welches Unternehmen hat in der aktuellsten Periode den höchsten Net Income?
3. Gibt es eine Korrelation zwischen Tax Rate For Calcs und der Nettogewinnmarge?
4. Welches Unternehmen hat die höchste Volatilität beim Diluted EPS, und erklären Sondereffekte (Tax Effect Of Unusual Items) diese?
5. Lassen sich Anomalien im Operating Revenue mit Z-Score oder rollierendem Durchschnitt erkennen?

**Hinweis:** Fehlende Geschäftsjahre sind in den Rohdaten als Nullen gespeichert und werden im Notebook entfernt. Danach liegen pro Unternehmen 4 auswertbare Jahreswerte vor. Die Ergebnisse sind daher explorative Tendenzen, kein statistisch belastbarer Nachweis.

## Quick Start

Voraussetzung: Python 3.10 oder neuer.

```bash
# 1. Repository klonen
git clone https://github.com/KrisLaemmermann/mgh-dbm25-Gruppe07-Unternehmensanalyse-.git
cd mgh-dbm25-Gruppe07-Unternehmensanalyse-

# 2. (Optional) virtuelle Umgebung anlegen
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Abhängigkeiten installieren
pip install -r requirements.txt

# 4. Notebook starten
jupyter notebook
```

Anschließend `Business_Analytics_BigTech.ipynb` öffnen und über **Kernel → Restart & Run All** alle Zellen ausführen. Die CSV-Datei muss im selben Ordner wie das Notebook liegen (alternativ im Unterordner `data/`).

## Inhalt

```
mgh-dbm25-Gruppe07-Unternehmensanalyse-/
├── README.md                              # diese Datei
├── requirements.txt                       # benötigte Python-Pakete
├── Business_Analytics_BigTech.ipynb       # Jupyter Notebook mit Analyse und Visualisierung
├── VIBE_CODING.md                         # Dokumentation der KI-Nutzung (Prompts, Entscheidungen, Prüfschritte)
├── 04_company_financials[1].csv           # Rohdaten (S&P-500-Finanzkennzahlen)
└── mgh-dbm25-gruppe07-Exposé...pdf        # Exposé
```

| Datei | Beschreibung |
|---|---|
| `Business_Analytics_BigTech.ipynb` | Datenaufbereitung, Beantwortung der 5 Forschungsfragen, Diagramme, Interpretationen |
| `VIBE_CODING.md` | Dokumentation des Vibe Codings: Prompts, wichtige Entscheidungen, Qualitätssicherung |
| `04_company_financials[1].csv` | Datengrundlage im CSV-Format |
| Exposé (PDF) | Projektskizze mit Forschungsfragen |
| `requirements.txt` | pandas, numpy, matplotlib, scipy, jupyter |

## Daten und Lizenz

Quelle: Kaggle-Datensatz „S&P 500“ (Nutzer *sadiqguru*): https://www.kaggle.com/datasets/sadiqguru/s-and-p-500-stock-data-along-with-financials-and-news/data

Lizenz laut Kaggle: # Released under MIT License

Copyright (c) 2013 Mark Otto.

Copyright (c) 2017 Andrew Fong.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
