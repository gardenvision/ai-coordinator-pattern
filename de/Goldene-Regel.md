# KI-Koordinator-Muster – Goldene Regel

Stand 2026-10-28 · gehört zu [KI-Koordinator-Muster.md](KI-Koordinator-Muster.md) (Fassung 4.6)

> **Jeder Rechner mit eigener Werkbank ist ein eigener Bauplatz, nicht nur ein Prüfplatz.
> Verteile die Einbauten auf alle Bauplätze.**

Eine **Werkbank** ist alles, was ein Rechner zum Einbauen braucht: ein eigener Editor bzw. eine eigene Laufzeit- und
Testumgebung und eigene Agenten, die dort arbeiten.

**Warum:** Wer einen zweiten Rechner nur für Gegentests nutzt, macht den einen Editor auf dem Hauptrechner zum Engpass für
alles. Dann stehen fertige Offline-Ergebnisse Schlange, obwohl eine zweite Werkbank frei ist. Der zweite Rechner wurde aber
gerade dafür eingerichtet: mit eigenem Editor und eigenen Agenten.

---

## Die vier Punkte

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

---

## Kurz prüfen vor jeder Vergabe

- Welche Bauplätze sind frei, und ist der Editor dort frei?
- Braucht das Paket einen noch nicht eingespielten Stand, oder berührt es nicht mischbare Dateien eines laufenden Einbaus?
  Dann bleibt es auf diesem Bauplatz.
- Ist es schon offline erledigt oder läuft es woanders? Dann nicht noch einmal vergeben.
- Steht jeder Bauplatz auf der aktuellen Hauptlinie?

## Verwandte Abschnitte im Muster

5.1 Fenster-Protokoll · 5.2 Geteilte Dateien und Nummern · 5.11 Delegieren statt selbst umsetzen · 9 Mehrere Rechner ·
11 Bewährte Lehren (eigener Takt, „Fertig“ vorher festlegen)
