# Solace Health · Evidenz-Review (Statistik & A/B-Testing)

**Statistik-Projekt (Masterschool, Data Analytics) · pandas · SciPy · matplotlib · Jupyter**

*English summary below.*

**Dokumente:** [Zusammenfassung (3 Seiten)](docs/Solace_Zusammenfassung.pdf) · [Präsentation](docs/Solace_Praesentation.pdf) · [Abgabedokument](docs/Solace_Abgabedokument.pdf)

## Frage

Eine Klinikkette mit vier Standorten wollte wissen:

1. Warten Patienten in Downtown wie versprochen im Mittel weniger als 15 Minuten?
2. Unterscheidet sich Riverside von Downtown?
3. Kann ein geplanter SMS-Test belegen, dass Erinnerungen nicht wahrgenommene Termine (No-Shows) senken?

Datenbasis: Besuchslog vom 5. Januar bis 5. April 2026 (1.200 Besuche nach Bereinigung) und 90 Tage Betriebsdaten.

## Vorgehen

- **Daten-Audit vor jeder Auswertung:** 9 Dubletten entfernt, 123 fehlende Zufriedenheitswerte nicht aufgefüllt (bei Urgent fast jeder dritte, also nicht zufällig), 129 No-Shows mit logisch unmöglichen Wartezeiten und Kosten markiert statt stillschweigend gelöscht.
- **Regeln vor den Tests festgelegt:** Ausreißerregel, Irrtumsrisiko, Testrichtung.
- **Tests:** einseitiger t-Test gegen 15 Minuten, Welch-Test Riverside gegen Downtown, Konfidenzintervalle, Cohens d, Power-Analyse.
- **Robustheit:** jedes Ergebnis auf Roh- und bereinigten Daten, ohne No-Show-Zeilen und ohne extreme Wartezeiten geprüft.
- **Weiterführend:** lineare und logistische Regression, Modelldiagnose, Kapazitätsplanung, Fallzahlplanung für einen gültigen Test.

## Ergebnisse

- **Downtown hält das Versprechen im Mittel ein:** 12,2 Minuten, 95-%-Konfidenzintervall [11,4; 12,9]. Trotzdem warten 27,9 % der Besuche (120 von 430) länger als 15 Minuten.
- **Riverside wartet 8,6 Minuten länger** [7,3; 9,8], in jeder geprüften Teilgruppe. Der Effekt ist groß (Cohens d = 1,04). Terminart, Versicherung und Wochentag erklären ihn nicht.
- **Wartezeit kostet Zufriedenheit:** von 4,60 Punkten bei bis zu 5 Minuten auf 3,52 bei über 30 Minuten.
- **Urteil zum SMS-Test: so nicht durchführen.** Riverside wurde nach Freiwilligkeit gewählt, Downtown ist die einzige Vergleichsgruppe, die Monate unterscheiden sich, und beide Standorte haben während des Tests eigenmächtig erinnert. Standort und Monat allein erklären schon −5,5 Punkte, mehr als der gezeigte Rückgang.
- **Gültige Version:** zufällige Zuteilung je Termin an allen Standorten gleichzeitig, eine Hauptkennzahl vorab, etwa 470 Termine pro Gruppe für einen Rückgang um 5 Prozentpunkte.

## Learning

Ein kleines p beweist keinen Effekt, und ein sauberer Test hilft nichts, wenn die Zuteilung nicht zufällig ist. Erst Daten und Versuchsaufbau prüfen, dann rechnen.

## Ausführen

Das Notebook wurde in Google Colab erstellt und enthält alle Ausgaben, man kann es also direkt auf GitHub lesen. Die CSV-Dateien (`solace_visits.csv`, `solace_daily_ops.csv`) stammen aus dem Kursmaterial und liegen nicht im Repo. Wer sie hat, legt sie neben das Notebook (in Colab fragt die Upload-Zelle danach) und führt alle Zellen aus.

## English summary

Statistics project of my data analytics programme. A clinic chain asked whether its Downtown site keeps the promise of under 15 minutes' wait, whether Riverside differs, and whether a planned SMS test could show fewer no-shows. I audited the visit log first (duplicates, non-random missing ratings, impossible values for no-shows flagged rather than deleted), then ran a one-sided t-test, a Welch test, confidence intervals, effect sizes and a power analysis, and rechecked every result on several data variants.

**Key findings:** Downtown keeps the promise on average (12.2 min [11.4; 12.9]), yet 27.9% of visits wait longer. Riverside waits 8.6 minutes longer [7.3; 9.8], a large effect (Cohen's d = 1.04). The SMS test should not run as planned: site, month and staff improvising would be inseparable from the SMS. A valid design randomises per appointment across all sites, about 470 appointments per group.

The documents are in German.

Author: [Denise Tirrel](https://www.linkedin.com/in/denise-tirrel)
