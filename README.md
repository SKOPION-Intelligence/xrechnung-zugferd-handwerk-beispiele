# XRechnung- und ZUGFeRD-Beispiele für das Handwerk

Validierte Beispieldateien für E-Rechnungen im Handwerk: **XRechnung 3.0 (UBL)**, **ZUGFeRD / Factur-X EN 16931 (CII)** und eine **Bauleistungsrechnung nach § 13b UStG**.

Alle Dateien wurden mit dem offiziellen [KoSIT-Validator](https://github.com/itplr-kosit/validator) und der Prüfkonfiguration [XRechnung 3.0.2](https://github.com/itplr-kosit/validator-configuration-xrechnung) geprüft. Ergebnis: **accept**, ohne Fehler.

Bereitgestellt von [Handwerkrechnung.de](https://handwerkrechnung.de/de), einer Software für E-Rechnungen im Handwerk.

## Dateien

| Datei | Syntax | Profil / Standard | Anwendungsfall |
| :--- | :--- | :--- | :--- |
| [`xrechnung-3.0-ubl-handwerk-beispiel.xml`](samples/xrechnung-3.0-ubl-handwerk-beispiel.xml) | UBL 2.1 | XRechnung 3.0 (EN 16931) | Elektro-Handwerksrechnung an einen öffentlichen Auftraggeber mit Leitweg-ID, Ausweis nach § 35a EStG |
| [`zugferd-en16931-cii-handwerk-beispiel.xml`](samples/zugferd-en16931-cii-handwerk-beispiel.xml) | UN/CEFACT CII D16B | ZUGFeRD / Factur-X, Profil EN 16931 | Dieselbe Rechnung als CII-XML |
| [`xrechnung-13b-bauleistung-beispiel.xml`](samples/xrechnung-13b-bauleistung-beispiel.xml) | UBL 2.1 | XRechnung 3.0 (EN 16931) | Trockenbau-Bauleistung mit Steuerschuldnerschaft des Leistungsempfängers (§ 13b UStG, Kategorie `AE`) |

## Wichtige Felder (Auszug)

| Business Term | Bedeutung | Beispielwert |
| :--- | :--- | :--- |
| BT-1 | Rechnungsnummer | `RE-2026-0104` |
| BT-2 | Rechnungsdatum | `2026-11-01` |
| BT-10 | Käuferreferenz / Leitweg-ID | `04011000-1234512345-06` |
| BT-31 | USt-IdNr. des Verkäufers | `DE123456789` |
| BT-32 | Steuernummer des Verkäufers | `121/5000/1234` |
| BT-34 / BT-49 | Elektronische Adresse Verkäufer / Käufer | `EM`-Schema (E-Mail) |
| BT-72 | Leistungsdatum | `2026-10-30` |
| BT-81 | Zahlungsart | `58` (SEPA-Überweisung) |
| BT-118 / BT-120 | Steuerkategorie / Befreiungsgrund (§ 13b) | `AE` / „Steuerschuldnerschaft des Leistungsempfängers (§ 13b UStG)“ |
| BT-121 | Befreiungscode (§ 13b) | `VATEX-EU-AE` |

## Selbst prüfen

Online und kostenlos: [E-Rechnung-Validator](https://handwerkrechnung.de/de/tools/e-rechnung-validator) und [XRechnung-Viewer](https://handwerkrechnung.de/de/tools/xrechnung-viewer).

Lokal mit dem KoSIT-Validator:

```bash
java -jar validator-standalone.jar \
  -s xrechnung-3.0.2/scenarios.xml -r xrechnung-3.0.2 \
  samples/xrechnung-3.0-ubl-handwerk-beispiel.xml
```

## Hinweise

- Alle Namen, Adressen, Steuernummern und Bankdaten sind **fiktiv**.
- Die Dateien dienen als technische Referenz und ersetzen keine steuerliche Beratung.
- Weitere Erläuterungen und Downloads: [XRechnung- und ZUGFeRD-Beispiele zum Download](https://handwerkrechnung.de/de/xrechnung-beispiel-download).

## Lizenz

Die Beispieldateien stehen unter [CC0 1.0](LICENSE) und dürfen ohne Einschränkung verwendet werden.

---

Gepflegt von [Skopion Intelligence](https://skopion.de) · Mönchengladbach
