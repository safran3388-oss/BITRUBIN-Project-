> **HISTORISCHER ENTWURF — ÜBERHOLT.** Diese Version v2.2 bleibt nur zur Dokumentation früherer Entwicklungsstände erhalten. Sie ist nicht die aktuelle BITRUBIN-Spezifikation. Maßgeblich ist [Whitepaper v2.4 (Deutsch)](WHITEPAPER_DE_v2.4.md) bzw. [Whitepaper v2.4 (English)](WHITEPAPER_EN_v2.4.md). Empfängerzuordnung und technische Ausgaberegeln sind in v2.4 ausdrücklich als noch festzulegende Punkte gekennzeichnet.

---

# BITRUBIN – Whitepaper v2.2 (Prototyp / Forschungsstand)

**Burn Bitcoin. Create BITRUBIN.**  
*Ein digitales Geldsystem auf Bitcoin-Basis*  
Autor: Faycal Hammouti · 4. November 2026

> **Wichtiger Hinweis:** Dieses Dokument beschreibt einen Entwurf und ein Forschungsprojekt. BITRUBIN ist kein fertiges oder produktionsreifes System. Insbesondere ist die technische Zulässigkeit und Weiterleitung positiver OP_RETURN-Ausgabewerte noch nicht auf Bitcoin Signet nachgewiesen.

## 1. Ziel und Grundidee

BITRUBIN (BRBN) ist als eigenständiges digitales Geld- und Ausgabeprotokoll konzipiert, das Bitcoin als einzige Blockchain und einzige Konsensgrundlage verwendet. Ziel ist eine nachvollziehbare, knappe digitale Einheit mit bis zu 38 Dezimalstellen. BITRUBIN soll Bitcoin ergänzen und nicht durch eine zweite Blockchain ersetzen.

Die Ausgabe soll durch nachprüfbare Bitcoin-Transaktionen ausgelöst werden, in denen ein positiver BTC-Betrag in einer qualifizierenden, nicht ausgebbaren OP_RETURN-Ausgabe festgehalten wird. BITRUBIN CORE liest und prüft die Bitcoin-Historie und leitet daraus den Protokollzustand deterministisch ab.

## 2. Architektur: Bitcoin als einzige Grundlage

Es gibt keine eigene BITRUBIN-Blockchain, keine eigenen Blöcke, keine eigenen Miner oder Validatoren und keinen separaten Konsens. Bitcoin entscheidet, welche Transaktionen und Blöcke zur gültigen Bitcoin-Kette gehören. BITRUBIN CORE ist eine zusätzliche Prüf- und Auswertungsschicht, kein Ersatz für Bitcoin-Konsens.

Das Zielmodell sieht vor, dass jeder Teilnehmer einen eigenen Bitcoin-Core-Vollknoten betreibt und Bitcoin-Daten selbst validiert. Ein zweiter, unabhängig betriebener Bitcoin-Knoten dient als zusätzliche Kontrolle und zum Vergleich der Kettendaten. Die genaue Betriebs- und Synchronisationsarchitektur muss noch implementiert und getestet werden.

## 3. Ausgabeidee und OP_RETURN-Regel

Der aktuelle Vorschlag zählt jeden positiven BTC-Wert in einer qualifizierenden, nicht ausgebbaren OP_RETURN-Ausgabe ab einem festgelegten offiziellen BITRUBIN-Startblock. Transaktionen vor diesem Startblock werden nicht rückwirkend berücksichtigt. Ein spezieller BRBN-Marker oder ein zusätzlicher BRBN-Hash ist nach dem aktuellen Entwurf nicht vorgesehen.

Die OP_RETURN-Ausgabe ist nicht ausgebbar. Der darin zugeordnete Wert gilt daher im normalen Bitcoin-Ausgabemodell als dauerhaft nicht mehr ausgebbar. Ob Bitcoin-Knoten solche Ausgaben mit positivem Wert akzeptieren, als standardmäßig behandeln und weiterleiten, ist jedoch eine offene technische Frage. Die Regel ist noch nicht auf Signet nachgewiesen und darf nicht als funktionierend dargestellt werden.

Ein OP_RETURN-Ausgabeskript identifiziert keinen Empfänger. Als mögliche, noch nicht beschlossene Lösung wird untersucht, ob die erste normale, ausgebbare Ausgabe derselben Transaktion den Empfänger bestimmt. Diese Regel ist ausdrücklich ein Vorschlag und muss vor der Protokollfreigabe festgelegt werden.

## 4. Einheiten und Dezimalstellen

Die nominale Rechendefinition lautet: **1 BTC = 1 BRBN** und **1 Satoshi = 1 Rubini**. Dies sind ausschließlich Einheiten- und Buchhaltungsdefinitionen. Sie versprechen weder einen Marktwert noch eine Deckung, Rückzahlung oder Einlösbarkeit.

BRBN und Pearls verwenden jeweils **38 Dezimalstellen**. 1 Rubini entspricht 0,00000001 BRBN (10⁻⁸ BRBN) und damit 10³⁰ kleinsten BRBN-Recheneinheiten bei 38 Dezimalstellen. Alle Berechnungen müssen deterministisch mit Ganzzahlen erfolgen; Gleitkomma-Arithmetik ist für Konsensregeln ungeeignet.

## 5. Mengen und Zuteilungen

- Öffentliche Zielmenge: **2.100.000 BRBN** und **700.000 Pearls**.
- Gründerzuteilung zusätzlich: **63.000 BRBN** und **21.000 Pearls** (jeweils 3 % der öffentlichen Zielmenge).
- Entwicklerzuteilung zusätzlich: **42.000 BRBN** und **14.000 Pearls** (jeweils 2 % der öffentlichen Zielmenge).
- Maximale Gesamtmengen einschließlich Zuteilungen: **2.205.000 BRBN** und **735.000 Pearls**.

Die vollständige Entwicklerzuteilung soll von Beginn an bereitstehen; Verwahrung, Empfänger und Übertragbarkeit müssen noch eindeutig dokumentiert werden.

Pearls werden proportional zur gültigen öffentlichen BRBN-Ausgabe berechnet. Das Zielverhältnis bei vollständiger öffentlicher Ausgabe beträgt 1 Pearl je 3 BRBN. Die Berechnung muss deterministisch, mit 38 Dezimalstellen und ohne Aufteilungsvorteile erfolgen. Die Höchstmenge darf niemals überschritten werden. Ein Halving ist nicht vorgesehen.

## 6. Verifikation und Schutzmaßnahmen

BITRUBIN CORE muss mindestens die Bitcoin-Transaktion, den betreffenden Output-Index, das Ausgabeskript, den positiven BTC-Wert, die Zugehörigkeit zur gültigen Bitcoin-Kette und die erforderliche Bestätigungstiefe prüfen. Jedes Ausgabeereignis muss eindeutig identifiziert werden; als technische Ereigniskennung bietet sich TXID plus VOUT an.

Das System muss doppelte Verarbeitung verhindern, fehlerhafte oder mehrdeutige Transaktionen ablehnen und Bitcoin-Reorganisationen korrekt behandeln. Bei einer Reorganisation müssen betroffene Ereignisse zurückgenommen und der abgeleitete Zustand reproduzierbar neu berechnet werden. Die konkrete Bestätigungstiefe und Fehlerregeln sind noch festzulegen.

Unabhängige Knotenprüfung reduziert Abhängigkeiten von einem einzelnen Datenlieferanten, ersetzt aber nicht die Bitcoin-Konsenssicherheit. Wenn Bitcoin-Konsens selbst kompromittiert wird, kann BITRUBIN diese Grundlage nicht vollständig schützen.

## 7. Offene Punkte und Entwicklungsplan

Vor einer öffentlichen Prototypfreigabe müssen insbesondere folgende Punkte geklärt werden:

1. Akzeptanz und Weiterleitung positiver OP_RETURN-Werte auf Signet und im Bitcoin-Netzwerk.
2. Verbindliche Empfängerregel.
3. Offizieller Startblock.
4. Transaktions- und Bestätigungsregeln.
5. Reorganisations- und Duplikatbehandlung.
6. Exakte Ganzzahl- und Rundungsregeln.
7. Reproduzierbare Tests und unabhängige Sicherheitsprüfung.

Der nächste Schritt ist ein isolierter Signet-Test zur Untersuchung der OP_RETURN-Standardness und Relay-Policy. Erst danach sollte die konkrete Ausgabe- und Empfängerregel finalisiert und in BITRUBIN CORE implementiert werden.

## 8. Status und Haftungshinweis

BITRUBIN befindet sich im Konzept-, Forschungs- und Prototypstadium. Es gibt keine Zusicherung, dass die vorgeschlagene Ausgabeform im Bitcoin-Netzwerk akzeptiert oder weitergeleitet wird. Dieses Whitepaper ist keine Anlageberatung, kein Verkaufsangebot und kein Versprechen eines Tokenwerts, einer Rendite, einer Deckung oder Rückzahlung. Eine Nutzung mit echtem BTC sollte erst nach Implementierung, Tests und unabhängiger Prüfung erwogen werden.

© 2026 Faycal Hammouti. Prototyp-Dokument; technische Änderungen vorbehalten.
