---
layout: default
title: GuardianTimer Dokumentation
---

# GuardianTimer – Funktionsweise und Hintergründe

Die **GuardianTimer** ist eine Sicherheits-App für iOS, die nach dem Prinzip eines **Totmannschalters** funktioniert. Sie dient dazu, automatisch Hilfe zu rufen oder einen Alarm auszulösen, wenn der Nutzer *nicht* mehr reagiert.

![App-Rechte und Systemfunktionen](/assets/images/GuardianTimer-0-AppRights.png)

## Was ist der GuardianTimer?

Der GuardianTimer überwacht, ob der Nutzer regelmäßig aktiv bestätigt, dass alles in Ordnung ist.

### Die Funktionsweise

1. **Der Sender (z. B. eine gefährdete Person):** Startet die App und aktiviert einen Timer (z. B. 30 Minuten). Solange alles in Ordnung ist, muss der Sender regelmäßig einen Knopf drücken („Ich bin OK“). Bei jedem Drücken wird der Timer zurückgesetzt, und der aktuelle Standort sowie der Zeitpunkt werden aktualisiert.

![Start-Button des Senders](/assets/images/GuardianTimer-2-StartButton.png)

![Laufender Timer beim Sender](/assets/images/GuardianTimer-3-RunningTimer.png)

2. **Der Empfänger (z. B. ein Angehöriger):** Installiert ebenfalls die App und abonniert die Daten des Senders. Er sieht, wann zuletzt das „Alles OK“-Signal kam.

3. **Der Alarm:** Vergisst oder schafft es der Sender nicht, den Knopf vor Ablauf der Zeit zu drücken, wird der Empfänger automatisch alarmiert.

![Timer abgelaufen beim Empfänger](/assets/images/GuardianTimer-4-Watcher-TimerOverdue.png)

![Letzter Standort auf der Karte](/assets/images/GuardienTimer-5-Watcher-Map.png)

Die App überwacht also nicht primär, *wo* jemand ist, sondern *ob* jemand noch handlungsfähig ist.

## Unterschied zu Apple "Wo ist?" und "Wegbegleitung"

Apple bietet mit den Funktionen "Wo ist?" (Find My) und "Wegbegleitung" (Check In) bereits Möglichkeiten zur Standortbestimmung. Der GuardianTimer unterscheidet sich jedoch in einem entscheidenden Punkt:

* **Apple "Wo ist?":** Zeigt jederzeit den Standort des *Gerätes* an. Es sagt aber nichts darüber aus, wie es der Person geht. Ein Handy kann sich an einem Ort befinden, während dem Besitzer etwas zugestoßen ist, ohne dass es jemand bemerkt.
* **Apple "Wegbegleitung":** Überwacht, ob eine Person ein bestimmtes Ziel erreicht. Wenn man sich nicht bewegt oder das Ziel nicht erreicht, wird ein Alarm ausgelöst.
* **GuardianTimer (Der Unterschied):** Erfordert eine **aktive Bestätigung**. Auch wenn man zu Hause auf dem Sofa sitzt (und sich der Standort nicht ändert), muss man regelmäßig bestätigen, dass man wohlauf ist. Tut man das nicht (z. B. wegen Ohnmacht oder Sturz), wird Alarm geschlagen. Es geht um die **Aktivität der Person**, nicht nur um den Ort des Gerätes.

## Herausforderungen in der Entwicklung

Die Entwicklung einer solchen Sicherheits-App bringt spezielle technische Hürden mit sich:

### 1. Zuverlässigkeit vs. Akkuverbrauch
Die App muss im Hintergrund laufen, um im Notfall zuverlässig zu alarmieren. Gleichzeitig darf sie den Akku nicht leer saugen.

**Lösung:** Die App nutzt eine "When-In-Use"-Strategie. Der Standort wird nur genau in dem Moment abgefragt, wenn der Sender den Knopf drückt. Das spart Energie und schützt die Privatsphäre.

### 2. Datenübertragung in Echtzeit (CloudKit)
Wenn der Sender den Knopf drückt, muss diese Information sofort auf dem Handy des Empfängers erscheinen.

**Lösung:** Wir nutzen Apples iCloud (CloudKit) zur Übertragung. Diese ist sicher und datenschutzfreundlich. Spezielle Mechanismen („Polling" und „Remote Change Observer“) sorgen dafür, dass der Alarm beim Empfänger auch wirklich ankommt.

### 3. Fehlalarme vermeiden
Nichts ist schlimmer als ein Fehlalarm, der Panik auslöst.

**Lösung:** Mechanismen („Deduping" und „Cooldowns“) verhindern, dass ein Alarm mehrmals ausgelöst wird.

### 4. Datenschutz und Berechtigungen
Die App benötigt Zugriff auf den Standort und muss Mitteilungen senden dürfen.

**Ansatz:** Wir fragen nur nach den nötigsten Rechten. Der Standort wird nicht permanent überwacht, sondern nur punktuell beim manuellen Check-in gesendet.