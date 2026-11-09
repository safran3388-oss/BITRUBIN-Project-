> **HISTORICAL DRAFT — SUPERSEDED.** This v2.3 document is retained for reference only. It is not the current BITRUBIN specification. The current project rules are documented in [Whitepaper v2.4 (German)](WHITEPAPER_DE_v2.4.md) and [Whitepaper v2.4 (English)](WHITEPAPER_EN_v2.4.md). The current BPRL rule is proportional issuance with **no halving and no epochs**. Do not implement the superseded epoch/halving text below.

---

# BITRUBIN — Whitepaper v2.3
**Burn Bitcoin. Create BITRUBIN.**  
*Ein vorgeschlagenes digitales Geldprotokoll auf Bitcoin-Basis*  
Autor: Faycal Hammouti · 4. November 2026

> **Forschungshinweis:** BITRUBIN ist ein Konzept- und Prototypprojekt und nicht produktionsreif. Die Annahme und Weiterleitung positiver OP_RETURN-Ausgabewerte wurde auf Signet noch nicht nachgewiesen.

## 1. Ziel

BITRUBIN (BRBN) ist als eigenständiges digitales Geldprotokoll konzipiert, das Bitcoin als einzige Blockchain und einzige Konsensgrundlage verwendet. Es soll Bitcoin ergänzen und nicht durch eine zweite Blockchain ersetzen.

## 2. Architektur

Es gibt keine eigene BITRUBIN-Blockchain, keine eigene Blockproduktion, kein eigenes Mining- oder Validatorennetzwerk und keinen unabhängigen Konsens. Bitcoin bestimmt die gültige Kette. BITRUBIN CORE ist eine deterministische Prüf- und Auswertungsschicht über der Bitcoin-Historie.

Das vorgesehene Betriebsmodell verlangt, dass jeder Teilnehmer einen eigenen Bitcoin-Core-Vollknoten betreibt und Bitcoin-Daten selbstständig validiert. Ein zweiter, unabhängig betriebener Bitcoin-Core-Knoten dient als zusätzliche Gegenprüfung und ersetzt nicht die eigene Prüfung.

## 3. Vorgeschlagenes Bitcoin-Ausgabeereignis

Der aktuelle Vorschlag im Repository zählt positive BTC-Werte in qualifizierenden, nicht ausgebbaren OP_RETURN-Ausgaben ab einem offiziell festgelegten BITRUBIN-Startblock. Frühere Transaktionen werden ausgeschlossen. Ein spezieller BRBN-Marker oder Hash-Marker ist im aktuellen Vorschlag nicht vorgesehen.

Eine OP_RETURN-Ausgabe ist nicht ausgebbar. Ob Bitcoin Core positive OP_RETURN-Ausgabewerte als standardmäßig akzeptiert und das Netzwerk sie weiterleitet, ist jedoch eine offene technische Frage. Dies wurde auf Signet noch nicht nachgewiesen. Konsensgültigkeit, Standardness-Policy, lokale Mempool-Annahme und Weiterleitung durch Peers müssen getrennt getestet werden.

Eine OP_RETURN-Ausgabe bestimmt keinen Empfänger. Eine deterministische Empfängerregel, der Startblock, die Bestätigungsregeln, der Schutz vor doppelter Verarbeitung, der Umgang mit fehlerhaften Transaktionen und das Verhalten bei Reorganisationen müssen vor Aktivierung der Ausgabe-Logik verbindlich festgelegt werden.

## 4. Einheiten und Genauigkeit

BRBN und BPRL verwenden **38 Dezimalstellen**. Alle Protokollberechnungen müssen deterministisch mit Ganzzahlen erfolgen; Gleitkomma-Berechnungen dürfen den Token-Zustand nicht bestimmen.

Die nominalen Rechendefinitionen lauten **1 BTC = 1 BRBN** und **1 Satoshi = 1 Rubini**. Dies sind ausschließlich Einheitsdefinitionen und versprechen weder Marktwert noch Deckung, Rückzahlung oder Einlösbarkeit.

Ein Rubini entspricht 0,00000001 BRBN (10^-8 BRBN). Bei 38 Dezimalstellen entspricht ein Rubini genau 10^30 kleinsten BRBN-Recheneinheiten.

## 5. Öffentliche Mengen und Zuteilungen

| Zuteilung | BRBN | BPRL (Pearls) |
|---|---:|---:|
| Öffentliche Zielmenge | 2.100.000 | 700.000 |
| Gründerzuteilung (zusätzlich 3 %) | 63.000 | 21.000 |
| Entwicklerzuteilung (zusätzlich 2 %) | 42.000 | 14.000 |
| **Geplante Höchstmenge** | **2.205.000** | **735.000** |

Die vollständige Entwicklerzuteilung soll von Beginn an zugeteilt sein und nicht schrittweise durch Meilensteine verdient werden. Verwahrung, konkrete Empfänger und Übertragungsbedingungen müssen vor Aktivierung dokumentiert werden.

## 6. Ausgabe der Pearls (BPRL)

BPRL gehört zum BITRUBIN-System und setzt eine gültige BRBN-Ausgabe voraus. BPRL kann nicht unabhängig von einem gültigen BRBN-Ereignis entstehen. Die öffentliche BPRL-Zielmenge beträgt 700.000.

Die öffentliche BRBN-Zielmenge wird in vier Epochen zu jeweils 525.000 BRBN aufgeteilt. Die BPRL-Zuteilungsrate halbiert sich mit jeder folgenden Epoche. Die genaue Darstellung der Raten mit Ganzzahlen, die Berechnung pro Ereignis, Rundungs- und Restbetragsregeln sowie die Durchsetzung der Höchstmenge müssen vor Aktivierung in den Protokollregeln festgelegt und durch reproduzierbare Tests abgesichert werden. Eine Aufteilung auf mehrere Transaktionen darf keinen Zuteilungsvorteil erzeugen. Die gesamte BPRL-Menge einschließlich Gründer- und Entwicklerzuteilung darf 735.000 niemals überschreiten.

## 7. Verifikation und Sicherheitsanforderungen

BITRUBIN CORE muss qualifizierende Bitcoin-Transaktionen und Outputs, die Aufnahme in die Kette, die Bestätigungstiefe, eine eindeutige Ereigniskennung (TXID plus VOUT ist als Kennung vorgesehen), doppelte Verarbeitung und Reorganisationsfolgen deterministisch prüfen. Zwei unabhängig betriebene Bitcoin-Core-Knoten sollen aus derselben akzeptierten Kettenhistorie dasselbe Ergebnis ableiten.

BITRUBIN stützt sich auf den Bitcoin-Konsens und kann keine stärkere Konsenssicherheit als Bitcoin selbst bieten. Wird der Bitcoin-Konsens kompromittiert, kann BITRUBIN seine Grundlage nicht vollständig schützen.

## 8. Offene Entwicklungsarbeiten

1. Standardness und Weiterleitung positiver OP_RETURN-Werte auf Signet testen.
2. Empfängerregel und offiziellen Startblock verbindlich festlegen.
3. Bestätigungs-, Duplikat-, Fehler- und Reorganisationsregeln spezifizieren.
4. Exakte 38-stellige Ganzzahlberechnung sowie BPRL-Epochen- und Rundungsregeln festlegen.
5. BITRUBIN CORE implementieren und Ergebnisse unabhängiger Knoten vergleichen.
6. Reproduzierbare Tests veröffentlichen und eine unabhängige Sicherheitsprüfung durchführen.

## 9. Status und Haftungshinweis

BITRUBIN befindet sich weiterhin im Forschungs- und Prototypstadium. Die Ausgabe-Mechanik ist nicht nachgewiesen oder aktiviert; eine produktive Veröffentlichung ist nicht angekündigt. Keine echten Mittel einsetzen und sich im Produktivbetrieb nicht auf Ausgabeversprechen verlassen. Dieses Dokument ist keine Anlageberatung, kein Verkaufsangebot und kein Versprechen eines Werts, einer Rendite, Deckung oder Rückzahlung.

© 2026 Faycal Hammouti. Technischer Entwurf; Änderungen vorbehalten.
