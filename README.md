# Finanzkennzahlen der Big-Tech-Unternehmen im Vergleich

**Autoren:** [Vorname Nachname]

Datenprojekt im Modul *Business Analytics* (DHBW Bad Mergentheim, Digital Business Management, Dozent: Thomas Burghardt), umgesetzt mit der Methode **Vibe Coding**.

## Kurze Beschreibung

Das Projekt analysiert die Finanzkennzahlen von fünf börsennotierten Technologieunternehmen (**AAPL, MSFT, AMZN, TSLA, GOOGL**) auf Basis der Datei `04_company_financials.csv` (S&P-500-Unternehmen, Long-Format mit den Spalten `Symbol`, `Item`, `Period`, `Value`). Aus dem Gesamtdatensatz (114.528 Zeilen, 509 Unternehmen, 84 Kennzahlen) werden die 986 Zeilen der fünf Unternehmen ausgewertet. Die Ergebnisse werden in einem Jupyter Notebook visualisiert.

**Forschungsfragen:**

1. Wie hat sich der durchschnittliche Total Revenue über die Perioden entwickelt?
2. Welches Unternehmen hat in der aktuellsten Periode den höchsten Net Income?
3. Gibt es eine Korrelation zwischen Tax Rate For Calcs und der Nettogewinnmarge?
4. Welches Unternehmen hat die höchste Volatilität beim Diluted EPS, und erklären Sondereffekte (Tax Effect Of Unusual Items) diese?
5. Lassen sich Anomalien im Operating Revenue mit Z-Score oder rollierendem Durchschnitt erkennen?

> **Hinweis:** Pro Unternehmen liegen nur 4 bis 5 Jahreswerte vor. Die Ergebnisse sind daher explorative Tendenzen, kein statistisch belastbarer Nachweis.

## Quick Start

Voraussetzung: Python 3.10 oder neuer.

```bash
# 1. Repository klonen
git clone https://github.com/<Benutzername>/mgh-dbm25-gruppexx-<name-projekt>.git
cd mgh-dbm25-gruppexx-<name-projekt>

# 2. (Optional) virtuelle Umgebung anlegen
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Abhängigkeiten installieren
pip install -r requirements.txt

# 4. Notebook starten
jupyter notebook
```

Anschließend `analyse.ipynb` öffnen und über *Run All* alle Zellen ausführen. Die Datei `04_company_financials.csv` muss im Ordner `data/` liegen.

## Inhalt

```
mgh-dbm25-gruppexx-<name-projekt>/
├── README.md                      # diese Datei
├── requirements.txt               # benötigte Python-Pakete
├── analyse.ipynb                  # Jupyter Notebook mit Analyse und Visualisierung
├── data/
│   └── 04_company_financials.csv  # Rohdaten (S&P-500-Finanzkennzahlen)
└── docs/
    └── mgh-dbm25-gruppexx-expose.pdf   # Exposé
```

| Datei / Ordner | Beschreibung |
|---|---|
| `analyse.ipynb` | Datenaufbereitung, Beantwortung der 5 Forschungsfragen, Diagramme |
| `data/` | Datengrundlage im CSV-Format |
| `docs/` | Exposé (und optional Präsentationsfolien) |
| `requirements.txt` | pandas, numpy, matplotlib, seaborn, scipy, jupyter |

## Daten und Lizenz

Quelle und Nutzungsbedingungen der Daten: [Quelle/Link eintragen]. Die Daten werden ausschließlich zu Lehrzwecken verwendet.
