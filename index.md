---
layout: default
title: GuardianTimer Dokumentation
---

# GuardianTimer – Funktionsweise und Hintergründe

Die **GuardianTimer** ist eine Sicherheits-App für iOS, die nach dem Prinzip eines **Totmannschalters** funktioniert. Sie dient dazu, einer anderen Person einen Hinweis (iOS-Benachrichtigung) zu geben, wenn der Nutzer *nicht* mehr reagiert.

![App-Rechte und Systemfunktionen](/assets/images/GuardianTimer-0-AppRights.png)

## Was ist der GuardianTimer?

Der GuardianTimer überwacht, ob der Nutzer regelmäßig aktiv bestätigt, dass alles in Ordnung ist.

### Die Funktionsweise

1. **Der Sender (z. B. eine Person):** Startet die App und aktiviert einen Timer (z. B. 30 Minuten). Solange alles in Ordnung ist, muss der Sender regelmäßig einen Knopf drücken („Ich bin OK“). Bei jedem Drücken wird der Timer zurückgesetzt, und der aktuelle Standort sowie der Zeitpunkt werden aktualisiert.

![Start-Button des Senders](/assets/images/GuardianTimer-2-StartButton.png)

![Laufender Timer beim Sender](/assets/images/GuardianTimer-3-RunningTimer.png)

2. **Der Empfänger (z. B. ein Angehöriger):** Installiert ebenfalls die App und abonniert die Daten des Senders. Er sieht, wann zuletzt das „Alles OK“-Signal kam.

3. **Der Alarm:** Vergisst oder schafft es der Sender nicht, den Knopf vor Ablauf der Zeit zu drücken, wird der Empfänger automatisch benachrichtigt.

![Timer abgelaufen beim Empfänger](/assets/images/GuardianTimer-4-Watcher-TimerOverdue.png)

![Letzter Standort auf der Karte](/assets/images/GuardienTimer-5-Watcher-Map.png)

Die App überwacht also nicht primär, *wo* jemand ist, sondern *ob* jemand noch handlungsfähig ist.

## Unterschied zu Apple "Wo ist?" und "Wegbegleitung"

Apple bietet mit den Funktionen "Wo ist?" (Find My) und "Wegbegleitung" (Check In) bereits Möglichkeiten zur Standortbestimmung. Der GuardianTimer unterscheidet sich jedoch in einem entscheidenden Punkt:

* **Apple "Wo ist?":** Zeigt jederzeit den Standort des *Gerätes* an. Es sagt aber nichts darüber aus, wie es der Person geht. Ein Handy kann sich an einem Ort befinden, während dem Besitzer etwas zugestoßen ist, ohne dass es jemand bemerkt.
* **Apple "Wegbegleitung":** Überwacht, ob eine Person ein bestimmtes Ziel erreicht. Wenn man sich nicht bewegt oder das Ziel nicht erreicht, wird ein Alarm ausgelöst.
* **GuardianTimer (Der Unterschied):** Erfordert eine **aktive Bestätigung**. Auch wenn man zu Hause auf dem Sofa sitzt (und sich der Standort nicht ändert), muss man regelmäßig bestätigen, dass man wohlauf ist. Tut man das nicht (z. B. wegen Ohnmacht oder Sturz), wird Alarm geschlagen. Es geht um die **Aktivität der Person**, nicht nur um den Ort des Gerätes.
