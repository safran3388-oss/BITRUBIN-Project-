# BITRUBIN — Whitepaper v2.4
**Burn Bitcoin. Create BITRUBIN.**  
*Ein vorgeschlagenes digitales Geldprotokoll auf Bitcoin-Basis*  
Autor: Faycal Hammouti · 9. November 2026

> **Forschungs- und Entwicklungsstand:** BITRUBIN ist ein Konzept- und Prototypprojekt, nicht produktionsreif. Die technische Annahme und Weiterleitung positiver OP_RETURN-Ausgabewerte wurde auf Signet noch nicht nachgewiesen. Dieses Dokument beschreibt Regeln und offene Fragen, keine bereits funktionierende Ausgabe.

## 1. Ziel und Grundprinzip

BITRUBIN (BRBN) soll ein digitales Geldprotokoll sein, das Bitcoin als einzige Blockchain und einzige Konsensgrundlage verwendet. Es soll Bitcoin ergänzen und keine zweite Blockchain, eigene Blockproduktion oder ein eigenes Mining-/Validatorennetzwerk einführen.

Die zentrale Idee lautet: **Bitcoin verbrennen – BITRUBIN erzeugen.** Der aktuelle Entwurf wertet positive BTC-Werte in qualifizierenden, nicht ausgebbaren OP_RETURN-Ausgaben aus. Ein spezieller BRBN-Marker ist nicht erforderlich. Gezählt werden dürfen nur Ereignisse ab einem künftig festgelegten offiziellen Startblock; eine rückwirkende Ausgabe ist nicht vorgesehen.

## 2. Bitcoin-Burn- und OP_RETURN-Mechanismus

1. Eine Bitcoin-Transaktion enthält eine OP_RETURN-Ausgabe mit positivem BTC-Wert.
2. BITRUBIN CORE liest die bestätigte Transaktion aus der Bitcoin-Kette über Bitcoin Core.
3. CORE prüft anhand festgelegter Regeln, ob der Output qualifiziert, eindeutig und noch nicht verarbeitet ist.
4. Der qualifizierende BTC-Wert wird nach der Regel **1 BTC = 1 BRBN** verbucht; die kleinste benannte Einheit folgt der Regel **1 Satoshi = 1 Rubini**.
5. BPRL (Pearls) wird proportional zur gültigen BRBN-Ausgabe berechnet.

Eine OP_RETURN-Ausgabe ist nicht ausgebbar. Davon getrennt zu prüfen ist, ob Bitcoin Core positive OP_RETURN-Werte als standardmäßig akzeptiert, in den Mempool aufnimmt und an Peers weiterleitet. Konsensgültigkeit, Standardness-Policy, lokale Mempool-Annahme und Peer-Relay sind unterschiedliche Fragen. Der Mechanismus ist noch nicht auf Signet nachgewiesen und darf nicht als funktionsfähig beworben werden.

Ein OP_RETURN-Output benennt keinen Empfänger. Die verbindliche Zuordnung zu einer Wallet bzw. Adresse ist noch offen und muss vor der Aktivierung eindeutig beschlossen werden. Eine Zuordnung darf nicht stillschweigend aus einer beliebigen Transaktionsausgabe abgeleitet werden.

## 3. Architektur und Verifikation

Bitcoin ist die einzige Blockchain und Konsensbasis. BITRUBIN CORE ist eine deterministische Prüf- und Auswertungsschicht über der Bitcoin-Historie; es erzeugt keine eigenen Blöcke und keinen eigenen Konsens.

Das Zielmodell sieht vor, dass jeder Teilnehmer einen eigenen Bitcoin-Core-Vollknoten betreibt und Bitcoin-Daten selbst validiert. Ein zweiter, unabhängig betriebener Bitcoin-Core-Knoten dient als zusätzliche Gegenprüfung. Beide Knoten sollen bei identischer gültiger Kettenhistorie zum gleichen BITRUBIN-Ergebnis gelangen.

Vor der Aktivierung müssen mindestens Startblock, Bestätigungstiefe, eindeutige Ereigniskennung (vorgesehen: TXID plus VOUT), Duplikatvermeidung, ungültige oder mehrdeutige Transaktionen sowie Rollback und Neuberechnung bei Chain-Reorganisationen verbindlich spezifiziert werden.

## 4. Einheiten und Genauigkeit

- **1 BTC = 1 BRBN** (nominale Protokoll- und Buchhaltungsdefinition).
- **1 Satoshi = 1 Rubini** (nominale Definition der kleinsten benannten Einheit).
- BRBN und BPRL verwenden jeweils **38 Dezimalstellen**.
- Alle zustandsbestimmenden Berechnungen müssen deterministisch mit Ganzzahlen erfolgen; Gleitkomma-Arithmetik ist dafür ausgeschlossen.

Diese Einheitsdefinitionen versprechen weder Marktwert noch BTC-Deckung, Rückzahlung, Einlösbarkeit oder einen garantierten Wechselkurs.

## 5. Mengen und Zuteilungen

| Zuteilung | BRBN | BPRL (Pearls) |
|---|---:|---:|
| Öffentliche Zielmenge | 2.100.000 | 700.000 |
| Gründerzuteilung zusätzlich (3 %) | 63.000 | 21.000 |
| Entwicklerzuteilung zusätzlich (2 %) | 42.000 | 14.000 |
| **Geplante Höchstmenge einschließlich Zuteilungen** | **2.205.000** | **735.000** |

Die Gründer- und Entwicklerzuteilungen kommen zusätzlich zur öffentlichen Zielmenge hinzu. Die Entwicklerzuteilung ist nach dem aktuellen Projektwunsch von Beginn an vollständig vorgesehen und nicht an Meilensteine gebunden. Verwahrung, konkrete Empfänger und Übertragungsbedingungen müssen noch dokumentiert werden.

## 6. Pearls (BPRL) — proportional, ohne Halving

BPRL gehört zum BITRUBIN-System und entsteht ausschließlich in Verbindung mit gültiger BRBN-Ausgabe. Die öffentliche Zielmenge beträgt 700.000 BPRL bei einer öffentlichen BRBN-Zielmenge von 2.100.000 BRBN. Daraus ergibt sich als Zielverhältnis **1 BPRL je 3 BRBN** bei vollständiger öffentlicher Ausgabe.

**Es gibt kein Halving und keine Epochen.** Die BPRL-Ausgabe ist proportional zur gültigen BRBN-Ausgabe. Die Berechnung muss deterministisch, mit 38 Dezimalstellen und ohne Vorteil durch Aufteilung auf mehrere Transaktionen erfolgen. Rundungs- und Restbetragsregeln sowie die Durchsetzung der Gesamtobergrenze müssen vor Aktivierung exakt festgelegt und getestet werden. Die gesamte geplante BPRL-Menge einschließlich Gründer- und Entwicklerzuteilung darf 735.000 nicht überschreiten.

## 7. Offene technische Arbeiten

1. Positive OP_RETURN-Ausgabewerte auf Signet konstruieren und Annahme, Mempool-Verhalten und Relay getrennt testen.
2. Empfänger-/Wallet-Zuordnungsregel gemeinsam mit dem Projektinhaber verbindlich festlegen.
3. Offiziellen Startblock und Bestätigungspolitik bestimmen.
4. Output-Qualifikation, Ereigniskennung, Duplikat- und Reorganisationsregeln spezifizieren.
5. 38-stellige Ganzzahlberechnung, proportionale BPRL-Formel, Rundung und Caps implementieren und testen.
6. Ergebnisse zweier unabhängig betriebener Bitcoin-Core-Knoten vergleichen.
7. Reproduzierbare Tests veröffentlichen und eine unabhängige Sicherheitsprüfung durchführen.

## 8. Entwicklungsstatus und Entwicklerübernahme

BITRUBIN sucht einen erfahrenen Bitcoin-/Protocol-Entwickler oder ein Entwicklungsteam, das die technische Prüfung, Spezifikation, Implementierung, Tests und anschließend die vollständige technische Entwicklung bzw. Übernahme des Projekts übernehmen möchte. Die zentralen ersten Aufgaben sind Signet-Forschung zu positiven OP_RETURN-Werten, eine sichere Empfängerregel und ein reproduzierbarer BITRUBIN-CORE-Prototyp.

Bis diese Arbeiten abgeschlossen und unabhängig geprüft sind, bleibt BITRUBIN ein Forschungs- und Prototypprojekt. Es gibt keine produktive Ausgabe und keine Empfehlung, echtes BTC für einen vermeintlichen BRBN-Erwerb einzusetzen.

## 9. Haftungshinweis

Dieses Dokument ist keine Anlageberatung, kein Verkaufsangebot und kein Versprechen von Wert, Rendite, Deckung oder Rückzahlung. Die technische Realisierbarkeit der vorgeschlagenen OP_RETURN-Ausgabe ist offen.

© 2026 Faycal Hammouti. Technischer Entwurf; Änderungen vorbehalten.
