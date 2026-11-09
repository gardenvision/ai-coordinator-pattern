# KI-Koordinator-Muster – Goldene Regel

Stand 2026-11-09 · gehört zu [KI-Koordinator-Muster.md](KI-Koordinator-Muster.md) (Fassung 4.9)

> **Jeder Rechner mit eigener Werkbank ist ein eigener Bauplatz, nicht nur ein Prüfplatz.
> Verteile die Einbauten auf alle Bauplätze – und gib mit jedem „fertig“ den nächsten Block frei.**

Eine **Werkbank** ist alles, was ein Rechner zum Einbauen braucht: ein eigener Editor bzw. eine eigene Laufzeit- und
Testumgebung und eigene Agenten, die dort arbeiten.

**Warum:** Wer einen zweiten Rechner nur für Gegentests nutzt, macht den einen Editor auf dem Hauptrechner zum Engpass für
alles. Dann stehen fertige Offline-Ergebnisse Schlange, obwohl eine zweite Werkbank frei ist. Der zweite Rechner wurde aber
gerade dafür eingerichtet: mit eigenem Editor und eigenen Agenten.

---

## Die acht Punkte

1. **Begrenzt wird nur die echte exklusive Ressource.** Je Rechner arbeitet genau ein Agent zur Zeit im Editor
   (Fenster-Protokoll, Muster 5.1). Offline-Arbeit – lesen, planen, Patches schreiben, offline kompilieren,
   Hintergrund-Werkzeuge – läuft parallel, solange keine zwei Agenten dieselbe Datei ändern. Wie viele Helfer gleichzeitig
   arbeiten, begrenzt das Budget (Muster 5.10), keine künstliche Obergrenze.
2. **Keine künstliche Grenze, die einen Koordinationsfehler verdeckt.** Eine Obergrenze für die Zahl der Baustellen ist oft
   ein Pflaster für eine andere Ursache: fehlender Takt des Koordinators, schlafende Helfer, Aufträge ohne „Fertig heißt“.
   Erst die Ursache beheben, dann nur das Exklusive begrenzen. Aus der Praxis: Eine Grenze von „höchstens zwei Baustellen“
   stammte aus einer Phase, in der der Takt des Koordinators versehentlich aus war. Danach lief es deutlich besser, und die
   Grenze bremste nur noch.
3. **Was auf einem Bauplatz bleibt und was wandert.** Auf einem Rechner bleibt, was dessen noch nicht eingespielten Stand
   braucht oder dieselben nicht mischbaren Dateien berührt wie ein laufender Einbau dort (z. B. Binärdateien, große Dateien
   in LFS, gemeinsame Konfigurations- oder Schemadateien). Alles andere geht auf eigenen Zweigen an die anderen Bauplätze. Der
   Koordinator führt zusammen und vergibt die gemeinsamen Nummern (Muster 5.2 und 9).
4. **Alle Bauplätze auf derselben Hauptlinie.** Nach jedem Einspielen versorgt der Koordinator alle Bauplätze mit demselben
   Stand (z. B. Push in alle Remotes, danach Pull auf jedem Rechner). Vor jeder Vergabe gleicht er ab, was schon offline
   erledigt ist oder woanders läuft, damit nichts doppelt gebaut wird.
5. **Freie Werkbank und wartender Block sind ein Alarm.** Steht eine Werkbank frei und wartet ein vereinbarter Block, geht er
   sofort los. Hängt der Block nur an einem Ja des Menschen und der Mensch ist da, fragt der Koordinator sofort, mit
   Empfehlung, statt ihn als „liegt beim Menschen“ stehen zu lassen. **Keine Arbeit erfinden:** Eine freie Werkbank ohne
   wartenden Block darf ruhen. Aus der Praxis: Solange jede freie Werkbank als Alarm galt, entstanden in einer Nacht
   37 Gegenlesungen und viele Pläne, die niemand brauchte, und das Kontingent schmolz. Ein Stillstand-Wächter meldet eine
   freie Werkbank mit wartendem Block nach einer einstellbaren Leerlaufzeit (Muster 5.12).
6. **„Fertig“ heißt: im selben Zug den nächsten Block freigeben.** Ein ausstehender Test des Menschen blockiert keine Arbeit
   am Zweig; nur das Einspielen und die Abnahme warten darauf. Bekannte Fehler für den nächsten Build werden nicht „bis nach
   dem Test“ geparkt. Aus der Praxis: Der Mensch fragte „wird daran schon gearbeitet?“, und beide Werkbänke standen frei.
7. **Vorrang und Pausen haben ein Ende.** „Thema X hat Vorrang“ heißt: X bekommt zuerst die Werkbank. Die anderen Aufgaben
   behalten einen Besitzer und einen nächsten Schritt und laufen offline oder auf dem anderen Bauplatz weiter. Jede Pause
   nennt ihren Grund; fällt er weg (der Morgen kommt, der Test ist vorbei, das Kontingent ist zurück), endet sie. Aus der
   Praxis: Eine Nachtregel wurde morgens nicht aufgehoben, und eine Werkbank stand fast sieben Stunden frei.
8. **Der Block geht an die zuständige Leitung.** Vor jedem Block fragt oder beauftragt der Koordinator die fachlich
   zuständige Leitungs-Session, nicht irgendeinen freien Helfer. Ist sie nicht erreichbar, bittet er den Menschen, sie zu
   öffnen, oder sagt offen, wer den Block stattdessen übernimmt.

---

## Kurz prüfen vor jeder Vergabe

- Steht eine Werkbank frei, und wartet ein vereinbarter Block? Dann sofort vergeben – aber keinen Block erfinden.
- Hängt der Block nur an einem Ja des Menschen? Dann jetzt fragen, mit Empfehlung.
- Ist die zuständige Leitung gefragt oder beauftragt?
- Welche Bauplätze sind frei, und ist der Editor dort frei?
- Braucht das Paket einen noch nicht eingespielten Stand, oder berührt es nicht mischbare Dateien eines laufenden Einbaus?
  Dann bleibt es auf diesem Bauplatz.
- Ist es schon erledigt, gebaut oder läuft es woanders? Erst in Historie und Tafel nachsehen – auch bevor der Mensch
  gefragt wird.
- Steht jeder Bauplatz auf der aktuellen Hauptlinie?

## Verwandte Abschnitte im Muster

5.1 Fenster-Protokoll · 5.2 Geteilte Dateien und Nummern · 5.5 Reviews · 5.11 Delegieren statt selbst umsetzen ·
5.12 Keine Aufgabe liegen lassen · 7 Tag- und Nachtmodus · 9 Mehrere Rechner · 11 Bewährte Lehren (eigener Takt,
„Fertig“ vorher festlegen)
