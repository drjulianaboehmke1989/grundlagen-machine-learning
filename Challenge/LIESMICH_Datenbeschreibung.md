# Challenge-Daten: Täglicher Absatz eines Online-Modehändlers

## Szenario
Ein Online-Modehändler plant Lager, Logistik und Personal für das Weihnachtsgeschäft. Am **31.10.2020 abends** soll eine Prognose für den **Absatz jedes einzelnen Tages vom 01.11.2020 bis 31.12.2020** (61 Tage) erstellt werden. In diesen Zeitraum fallen Black Friday, die Vorweihnachtszeit und die Feiertage.

## Prognoseaufgabe
| | |
|---|---|
| Prognosezeitpunkt | 31.10.2020, abends |
| Prognosezeitraum | 01.11.2020 bis 31.12.2020, jeder Tag einzeln (61 Prognosen) |
| Prognosehorizont | 1 bis 61 Tage |
| Zielgröße | `absatz` (Anzahl verkaufter Artikel pro Tag) |
| Bewertung | Mean Absolute Error (MAE) über die 61 Tage, kleiner gewinnt; zur Information zusätzlich Root Mean Squared Error (RMSE) |
| Abgabe | CSV mit den Spalten `datum` und `prognose`, genau 61 Zeilen |

Wichtig: Für den Prognosezeitraum ist der Absatz **nicht** bekannt.

## Dateien
| Datei | Inhalt |
|---|---|
| `Onlinehandel_Absatz_Training.csv` | 01.01.2017 bis 31.10.2020, 1.400 Tage, mit Zielgröße |
| `Onlinehandel_Absatz_Prognosezeitraum.csv` | 01.11.2020 bis 31.12.2020, 61 Tage, nur Merkmale, ohne Zielgröße |

Die Daten sind vollständig: keine fehlenden Tage, keine Missing Values.

## Spalten
| Spalte | Bedeutung | Am 31.10.2020 für den Prognosezeitraum bekannt? | Im Prognosezeitraum enthalten |
|---|---|---|---|
| `datum` | Tag | ja | ja |
| **`absatz`** | **Zielgröße: Anzahl verkaufter Artikel an diesem Tag** | nein | nein |
| `feiertag` | 1 = bundesweiter Feiertag, Heiligabend oder Silvester | ja (Kalender) | ja |
| `black_friday` | 1 = Black-Friday-Aktionstag | ja (geplant) | ja |
| `rabatt_aktion` | Durchschnittlicher Rabatt einer Flash-Sale-Aktion (0,12 = 12 %), 0 = keine Aktion | ja (geplant) | ja |
| `durchschnittspreis` | Durchschnittlicher Artikelpreis im Shop in Euro | ja (Preisplanung) | ja |
| `budget_suchmaschine` | Werbebudget Suchmaschinen (bezahlte Suche, Shopping-Anzeigen) | ja (Mediaplan) | ja |
| `budget_affiliate` | Werbebudget Partnerseiten (Affiliate) | ja (Mediaplan) | ja |
| `budget_retargeting` | Werbebudget Retargeting (erneute Ansprache früherer Besucher) | ja (Mediaplan) | ja |
| `budget_social_media` | Werbebudget Social Media (Facebook, Instagram, TikTok, Snapchat) | ja (Mediaplan) | ja |
| `budget_tv` | Werbebudget Fernsehen | ja (Mediaplan) | ja |
| `budget_display_video` | Werbebudget Bannerwerbung und Online-Video (inkl. YouTube) | ja (Mediaplan) | ja |
| `budget_radio` | Werbebudget Radio | ja (Mediaplan) | ja |
| `budget_print` | Werbebudget Printwerbung (Kataloge, Mailings) | ja (Mediaplan) | ja |
| `budget_influencer` | Werbebudget Influencer-Kooperationen | ja (Mediaplan) | ja |
| `push_nachrichten` | Anzahl versendeter App-Push-Nachrichten | ja (Versandplan) | ja |
| `email_versand` | Anzahl versendeter Newsletter-E-Mails | ja (Versandplan) | ja |
| `temperatur` | Tagesmitteltemperatur in °C (als Wetterprognose behandeln) | ja (Prognose) | ja |
| `umsatz` | Umsatz des Tages in Euro | nein, erst am Abend des Tages | nein |
| `google_suchinteresse` | Google-Trends-Index (Suchinteresse) an diesem Tag | nein, erst am Tag selbst | nein |
| `corona_neuinfektionen` | Gemeldete Corona-Neuinfektionen in Deutschland an diesem Tag | nein | nein |
| `lockdown_einzelhandel` | 1 = stationärer Einzelhandel geschlossen (bundesweit, vereinfacht) | nein, spätere Schließungen waren am 31.10. noch nicht beschlossen | nein |

Budgets sind Nettobeträge in Euro pro Tag. Die vier letzten Spalten stehen nur in den Trainingsdaten. Sie helfen beim Verstehen der Vergangenheit (z. B. des Frühjahrs 2020), für die Prognose stehen sie nicht zur Verfügung.

## Herkunft
Tagesdaten eines mittelgroßen Online-Modehändlers (2019: rund 2,4 Mio. verkaufte Artikel). Die absoluten Werte sind anonymisiert; Verläufe und Zusammenhänge entsprechen den Originaldaten. Für die Challenge wurden Marketingkanäle zu Budgetgruppen zusammengefasst, Spalten umbenannt, Feiertage und Lockdown-Phasen ergänzt sowie einzelne negative Buchungs- und Meldewerte (Korrekturbuchungen) auf 0 gesetzt.
