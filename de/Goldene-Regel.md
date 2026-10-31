# KI-Koordinator-Muster – Goldene Regel

Stand 2026-10-31 · gehört zu [KI-Koordinator-Muster.md](KI-Koordinator-Muster.md) (Fassung 4.7)

> **Jeder Rechner mit eigener Werkbank ist ein eigener Bauplatz, nicht nur ein Prüfplatz.
> Verteile die Einbauten auf alle Bauplätze.**

Eine **Werkbank** ist alles, was ein Rechner zum Einbauen braucht: ein eigener Editor bzw. eine eigene Laufzeit- und
Testumgebung und eigene Agenten, die dort arbeiten.

**Warum:** Wer einen zweiten Rechner nur für Gegentests nutzt, macht den einen Editor auf dem Hauptrechner zum Engpass für
alles. Dann stehen fertige Offline-Ergebnisse Schlange, obwohl eine zweite Werkbank frei ist. Der zweite Rechner wurde aber
gerade dafür eingerichtet: mit eigenem Editor und eigenen Agenten.

---

## Die sechs Punkte

1. **Begrenzt wird nur die echte exklusive Ressource.** Je Rechner arbeitet genau ein Agent zur Zeit im Editor
   (Fenster-Protokoll, Muster 5.1). Offline-Arbeit – lesen, planen, Patches schreiben, offline kompilieren,
   Hintergrund-Werkzeuge – läuft parallel und ohne Obergrenze, solange keine zwei Agenten dieselbe Datei ändern.
2. **Keine künstliche Grenze, die einen Koordinationsfehler verdeckt.** Eine Obergrenze für die Zahl der Baustellen ist oft
   ein Pflaster für eine andere Ursache: fehlender Takt des Koordinators, schlafende Helfer, Aufträge ohne „Fertig heißt“.
   Erst die Ursache beheben, dann nur das Exklusive begrenzen. Aus der Praxis: Eine Grenze von „höchstens zwei Baustellen“
   stammte aus einer Phase, in der der Takt des Koordinators versehentlich aus war. Danach lief es deutlich besser, und die
   Grenze bremste nur noch.
3. **Was auf einem Bauplatz bleibt und was wandert.** Auf einem Rechner bleibt, was dessen noch nicht eingespielten Stand
   braucht oder dieselben nicht mischbaren Dateien berührt wie ein laufender Einbau dort (z. B. Binärdateien, große Dateien
   in LFS, gemeinsame Speicher- oder Netzwerkdateien). Alles andere geht auf eigenen Zweigen an die anderen Bauplätze. Der
   Koordinator führt zusammen und vergibt die gemeinsamen Nummern (Muster 5.2 und 9).
4. **Alle Bauplätze auf derselben Hauptlinie.** Nach jedem Einspielen versorgt der Koordinator alle Bauplätze mit demselben
   Stand (z. B. Push in alle Remotes, danach Pull auf jedem Rechner). Vor jeder Vergabe gleicht er ab, was schon offline
   erledigt ist oder woanders läuft, damit nichts doppelt gebaut wird.
5. **Eine freie Werkbank ist ein Alarm.** Auch wenn der Mensch einem Thema Vorrang gibt, laufen dessen Teilschritte nicht
   nacheinander durch eine einzige Werkbank, während die zweite leer steht. Teilschritte und andere Aufgaben werden auf alle
   Bauplätze verteilt. Ein Stillstand-Wächter meldet eine Werkbank, die länger als eine einstellbare Leerlaufzeit frei ist (Muster 5.12).
6. **Vorrang ist keine Pause für alles andere.** „Thema X hat Vorrang“ heißt: X bekommt zuerst die Werkbank. Die anderen
   Aufgaben behalten einen Besitzer und einen nächsten Schritt und laufen offline oder auf dem anderen Bauplatz weiter.

---

## Kurz prüfen vor jeder Vergabe

- Steht eine Werkbank leer? Dann sofort die nächste Aufgabe von der Aufgaben-Tafel vergeben.
- Welche Bauplätze sind frei, und ist der Editor dort frei?
- Braucht das Paket einen noch nicht eingespielten Stand, oder berührt es nicht mischbare Dateien eines laufenden Einbaus?
  Dann bleibt es auf diesem Bauplatz.
- Ist es schon offline erledigt oder läuft es woanders? Dann nicht noch einmal vergeben.
- Steht jeder Bauplatz auf der aktuellen Hauptlinie?

## Verwandte Abschnitte im Muster

5.1 Fenster-Protokoll · 5.2 Geteilte Dateien und Nummern · 5.11 Delegieren statt selbst umsetzen ·
5.12 Keine Aufgabe liegen lassen · 9 Mehrere Rechner · 11 Bewährte Lehren (eigener Takt, „Fertig“ vorher festlegen)
