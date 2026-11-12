# XRechnung- und ZUGFeRD-Beispiele für das Handwerk

Validierte Beispieldateien für E-Rechnungen im deutschen Handwerk: **XRechnung 3.0.2 (UBL 2.1)**, **ZUGFeRD 2.4 / Factur-X EN 16931 (CII)**, **Bauleistungsrechnung nach § 13b UStG** sowie **Schlussrechnung nach Abschlagsrechnungen gemäß § 14 Abs. 5 UStG**.

Alle vier XML-Dateien wurden mit dem offiziellen [KoSIT-Validator 1.6.3](https://github.com/itplr-kosit/validator) und der Prüfkonfiguration [XRechnung 3.0.2](https://github.com/itplr-kosit/validator-configuration-xrechnung) geprüft. Ergebnis: **accept (`valid="true"`)**, 0 Fehler, 0 Warnungen.

Bereitgestellt von [Handwerkrechnung.de](https://handwerkrechnung.de/de), einer spezialisierten E-Rechnungssoftware für Handwerksbetriebe.

## Dateien

| Datei | Syntax | Profil / Standard | Anwendungsfall |
| :--- | :--- | :--- | :--- |
| [`xrechnung-3.0-ubl-handwerk-beispiel.xml`](samples/xrechnung-3.0-ubl-handwerk-beispiel.xml) | UBL 2.1 | XRechnung 3.0.2 (EN 16931) | Elektro-Handwerksrechnung an einen öffentlichen Auftraggeber mit Leitweg-ID und Ausweis nach § 35a EStG |
| [`zugferd-en16931-cii-handwerk-beispiel.xml`](samples/zugferd-en16931-cii-handwerk-beispiel.xml) | UN/CEFACT CII D16B | ZUGFeRD 2.4 / Factur-X, Profil EN 16931 | Dieselbe Handwerksrechnung als UN/CEFACT-CII-Kerndatensatz |
| [`xrechnung-13b-bauleistung-beispiel.xml`](samples/xrechnung-13b-bauleistung-beispiel.xml) | UBL 2.1 | XRechnung 3.0.2 (EN 16931) | Trockenbau-Bauleistung mit Steuerschuldnerschaft des Leistungsempfängers (§ 13b UStG, Kategorie `AE`) |
| [`xrechnung-schlussrechnung-abschlag-beispiel.xml`](samples/xrechnung-schlussrechnung-abschlag-beispiel.xml) | UBL 2.1 | XRechnung 3.0.2 (EN 16931) | Dachdecker-Schlussrechnung (10.000 € netto) nach 2 Abschlagsrechnungen gemäß § 14 Abs. 5 UStG (`BG-3`, `BT-113`, `BT-115`) |

## Wichtige EN-16931-Felder (Auszug)

| Business Term | Bedeutung | Beispielwert |
| :--- | :--- | :--- |
| BT-1 / BT-2 | Rechnungsnummer & Rechnungsdatum | `RE-2026-0218-SR` / `2026-11-10` |
| BT-10 | Käuferreferenz / Leitweg-ID | `04011000-1234512345-06` bzw. `BAU-2026-DACH-44` |
| BG-3 (BT-25 / BT-26) | Referenz auf vorausgegangene Abschlagsrechnungen | `RE-2026-0140` (`2026-09-15`), `RE-2026-0182` (`2026-10-15`) |
| BT-31 / BT-32 | USt-IdNr. / Steuernummer des Verkäufers | `DE123456789` / `121/5000/1234` |
| BT-34 / BT-49 | Elektronische Adresse Verkäufer / Käufer | `EM`-Schema (E-Mail) |
| BT-72 | Leistungs- bzw. Abnahmedatum | `2026-11-08` |
| BT-81 | Zahlungsart | `58` (SEPA-Überweisung) |
| BT-109 / BT-112 | Gesamtleistung netto / brutto | `10000.00` / `11900.00` |
| BT-113 / BT-115 | Bereits abgerechnete Abschläge (`PrepaidAmount`) / Restzahlung (`PayableAmount`) | `8330.00` / `3570.00` |
| BT-118 / BT-120 | Steuerkategorie / Befreiungsgrund (§ 13b) | `AE` / „Steuerschuldnerschaft des Leistungsempfängers (§ 13b UStG)“ |
| BT-130 | UN/ECE-Maßeinheitencodes im Handwerk | `HUR` (Stunde), `MTK` (m²), `MTR` (lfm), `C62` (Stück/Pauschal) |

## Online prüfen & berechnen (ohne Anmeldung)

- [E-Rechnung-Validator (KoSIT)](https://handwerkrechnung.de/de/tools/e-rechnung-validator) – XRechnung & ZUGFeRD online validieren
- [XRechnung- & ZUGFeRD-Viewer](https://handwerkrechnung.de/de/tools/xrechnung-viewer) – XML/PDF direkt lokal im Browser anzeigen
- [Abschlags- & Schlussrechnungs-Rechner](https://handwerkrechnung.de/de/tools/abschlagsrechnung-rechner) – Netto-Restforderung, § 14 Abs. 5 UStG-Abzug & Sicherheitseinbehalt berechnen
- [Leitfaden: Abschlagsrechnung & Schlussrechnung im Handwerk](https://handwerkrechnung.de/de/abschlagsrechnung-handwerk) – § 632a BGB, § 16 VOB/B & EN-16931-Feldzuordnung

Lokal mit dem KoSIT-Validator:

```bash
java -jar validator-standalone.jar \
  -s xrechnung-3.0.2/scenarios.xml -r xrechnung-3.0.2 \
  samples/xrechnung-schlussrechnung-abschlag-beispiel.xml
```

## Hinweise

- Alle Namen, Adressen, Steuernummern und Bankdaten sind **fiktiv**.
- Die Dateien dienen als technische Referenz und ersetzen keine steuerliche Beratung.
- Weitere Erläuterungen und Downloads: [XRechnung- und ZUGFeRD-Beispiele zum Download](https://handwerkrechnung.de/de/xrechnung-beispiel-download).

## Lizenz

Die Beispieldateien stehen unter [CC0 1.0](LICENSE) und dürfen ohne Einschränkung verwendet werden.

---

Gepflegt von [Skopion Intelligence](https://skopion.de) · Mönchengladbach
