# Prüfnachweis zu Abschnitt 16 (Vergleich mit Cloud-Angeboten)

Stand 2026-10-21, 17:40 · gehört zu [KI-Koordinator-Muster.md](KI-Koordinator-Muster.md) Fassung 4.1, Abschnitt 16

**Vorgehen:** Ein Zuarbeiter (anderes Modell) hatte die Recherche gemacht; mehrere seiner Links waren falsch. Am
21.10. abends wurde jede Aussage an offiziellen Seiten nachgeprüft: zuerst von einem Prüf-Helfer (nur lesen), danach die
wichtigsten Stellen noch einmal selbst geöffnet (Spalte „selbst“). Wiedergabe sinngemäß, nicht wörtlich.

**Bewertung:** belegt = Aussage auf der Seite gefunden · teilweise = im Kern richtig, Einschränkung beachten ·
nicht gefunden = Seite geöffnet, Aussage steht nicht dort.

## Quellen (Abruf jeweils 2026-10-21)

| Kürzel | Seite | Datum auf der Seite |
|---|---|---|
| D1 | `https://code.claude.com/docs/en/claude-projects` (Projects in Claude Code) | keines |
| D2 | `https://code.claude.com/docs/en/data-usage` (Datennutzung Claude Code) | keines |
| D3 | `https://code.claude.com/docs/en/routines` (Scheduled tasks) | keines |
| B1 | `https://claude.com/blog/projects-redesigned` („Projects redesigned: from folder to conversation“) | 17.09.2026 |
| H1 | `https://support.claude.com/en/articles/11145838-use-claude-code-with-your-pro-or-max-plan` | „diese Woche aktualisiert“ |
| H2 | `https://support.claude.com/en/articles/11049741-what-is-the-max-plan` | „vor über einer Woche aktualisiert“ |
| P1 | `https://claude.com/pricing` (Preise) | keines |
| P2 | `https://privacy.claude.com/en/articles/10023548-how-long-do-you-store-my-data` | 01.07.2026 |
| X1 | `https://learn.chatgpt.com/docs/cloud` (OpenAI Codex Cloud, Weiterleitung von developers.openai.com) | keines |
| X2 | `https://jules.google/docs` (Google Jules) | keines |

## Ergebnis je Aussage

| Nr. | Aussage aus der Recherche | Ergebnis | Was die Quelle sagt | Quelle | selbst |
|---|---|---|---|---|---|
| 1 | Projects ist Public Beta für Pro und Max, schrittweise, noch nicht Team/Enterprise | belegt | genau so; Freischaltung zuerst für Konten mit Cloud-Sessions und ohne alte Projekte in claude.ai | D1, B1 | ja |
| 2 | Ein Koordinator-Gespräch startet Aufgaben als parallele Cloud-Threads; einzelne Threads per Remote Control auf dem eigenen Rechner | belegt | je Aufgabe ein Thread; lokal ab Claude Code v2.1.280, nur solange der Rechner wach ist, nicht bei „Require trusted devices“ | D1 | ja |
| 3 | Eigener Klon und Zweig je Thread, am Ende Pull Request, der Mensch führt zusammen | teilweise | eigener Zweig und eigene Sandbox stimmen; Pull Request nur, wenn die Arbeit es verlangt; Zusammenführen per Knopf („Merge it“), eine Pflicht für den Menschen steht dort nicht | D1 | ja |
| 4 | Gemeinsames Projekt-Gedächtnis und Bibliothek | teilweise | Gedächtnis als Dateien mit Index `MEMORY.md`, jeder Cloud-Thread liest ihn beim Start; Bibliothek = hinzugefügte Dateien und von Threads erzeugte Dateien | D1 | ja |
| 5 | Parallele Threads zehren am selben 5-Stunden- und Wochenkontingent | belegt | Projekte nutzen dieselben Plan-Limits wie andere Claude-Code-Sessions und verbrauchen sie schneller; Limits gelten gemeinsam für Claude und Claude Code | D1, H1 | ja |
| 6 | Zahl der Threads und Modell in den Projekteinstellungen begrenzbar | teilweise | Modell und Denkstufe der Threads: ja (Project settings > General). Zahl der Threads: nur als Wunsch im Gespräch, ausdrücklich keine Obergrenze; harte Grenze 200 neue Threads pro Tag | D1 | ja |
| 7 | Nur Claude-Modelle | belegt (sinngemäß) | Anthropic ist in beiden Fällen (Cloud, Remote Control) der Modellanbieter | D1 | ja |
| 8 | Preise Pro 20 $, Max 100/200 $, Team je Platz | belegt | Pro 20 $/Monat (17 $ bei Jahreszahlung, 200 $ im Voraus); Max 5x 100 $, Max 20x 200 $; Team Standard 25 $ (20 $ jährlich), Premium 125 $ (100 $ jährlich); Preise können sich ändern | P1, H2 | ja (P1) |
| 9 | Datenschutz: Privatkonten 5 Jahre mit Training, sonst 30 Tage; Geschäftskonten kein Training; /feedback 5 Jahre | belegt | genau so; Geschäftskonten Standard 30 Tage; `/feedback`, `/bug`, `/share` 5 Jahre; Cloud-Session: Repository in isolierter VM, GitHub-Zugang bleibt auf Anthropic-Servern | D2, P2 | ja (D2) |
| 10 | Vorstellung am 17.09.2026 | belegt | Blogbeitrag vom 17.09.2026 | B1 | ja |
| 11 | Geplante Aufgaben („formerly routines“) sind Research Preview und laufen in der Cloud | belegt | ja; auch in selbst gehosteter Umgebung möglich; Pro, Max, Team, Enterprise | D3 | nein |
| 12 | Ähnliche Angebote anderer Anbieter | Stichprobe | Codex Cloud: eigene Arbeitsumgebung je Aufgabe, Commit/PR durch den Nutzer, kein Koordinator beschrieben. Jules: klont das Repository in eine VM; Koordinator oder parallele Läufe nicht gefunden. Je nur eine Seite geprüft | X1, X2 | nein |

## Zusatzfunde (für die Einordnung wichtig)

- **Kosten-Voreinstellung:** Ein neues Projekt lässt alle Threads mit dem größten Modell und hoher Denkstufe laufen; laut
  D1 verbraucht das den Plan am schnellsten. Auf Pro erreicht man das Limit an solchen Tagen früher. (D1)
- **Blog und Doku weichen ab:** Am 17.09. hieß es, lokale Threads kämen „bald“; die Doku beschreibt sie heute als
  verfügbar. Maßgeblich ist die Doku. (B1, D1)
- **Namensgleichheit:** Die Zeile „Projects“ auf der Preisseite meint die älteren Projekte in claude.ai (Chats und
  Projektwissen), nicht die Projects in Claude Code. (P1, D1)
- **Grenzen der Beta:** nicht im Terminal-CLI, in VS Code oder JetBrains; ein Projekt gehört genau einem Nutzer und lässt
  sich nicht teilen; keine Steuerung auf Organisationsebene; selbst gestartete lokale Sessions lassen sich nicht hinzufügen;
  eine Cloud-Sandbox kann neu starten, nicht committete Änderungen gehen dann verloren. (D1)
- **Max-Pläne** haben zusätzlich ein eigenes Wochenlimit für ein bestimmtes Modell. (H1)

## Nicht geprüft

- Starttermine der übrigen Angebote (Cloud-Sessions, Remote Control, Agent Teams, Managed Agents) aus der Recherche:
  für Abschnitt 16 nicht nötig, darum nicht nachgeprüft.
- Die älteren Projekte in claude.ai (seit 25.06.2024) wurden schon vorher an `https://www.anthropic.com/news/projects`
  geprüft und hier nicht erneut geöffnet.
