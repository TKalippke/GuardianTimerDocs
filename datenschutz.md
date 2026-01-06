---
layout: default
nav_order: 2
parent: Einführung
title: Datenschutz
permalink: /datenschutz/
---

# Datenschutz bei GuardianTimer

**GuardianTimer** legt großen Wert auf den Schutz Ihrer persönlichen Daten. Die App wurde so konzipiert, dass sie Ihre Privatsphäre respektiert und nur die absolut notwendigen Daten verarbeitet.

## Gesammelte Daten

Die App **speichert keine Daten dauerhaft** auf einem Server. Alle Informationen werden ausschließlich **peer-to-peer** zwischen den beteiligten Geräten über **iCloud (CloudKit)** ausgetauscht:

* **Standort**: Wird **nur** beim manuellen Drücken des „Ich bin OK“-Knopfes abgefragt und für die Laufzeit des Timers gespeichert. Danach wird er automatisch gelöscht.
* **Zeitstempel**: Markiert, wann der letzte Check-in erfolgt ist.
* **Abonnement-Informationen**: Welcher Sender welchen Empfänger abonniert hat (keine persönlichen Namen oder Kontaktdaten).

![App-Rechte](/assets/images/GuardianTimer-0-AppRights.png)

## Verwendete Technologien

### CloudKit (iCloud)

* **End-to-End-Verschlüsselung**: Alle Daten sind bereits auf dem Gerät verschlüsselt, bevor sie iCloud verlassen.
* **Keine Server-Zugriffe**: Apple kann Ihre Daten nicht einsehen.
* **Private Database**: Jeder Nutzer hat seine eigene isolierte Datenbank.

### Lokaler Speicher

Alle sensiblen Daten (z. B. Abonnements, Timer-Status) werden nur **lokal** auf dem Gerät gespeichert und nie mit Dritten geteilt.

## Berechtigungen

GuardianTimer fordert nur die minimal notwendigen iOS-Berechtigungen an:

| Berechtigung | Zweck | Häufigkeit |
|--------------|--------|------------|
| **Standort (When In Use)** | Bestimmung des Standorts beim Check-in | Nur bei Knopfdruck |
| **Benachrichtigungen** | Alarm beim Timer-Ablauf | Nur bei Empfänger |
| **iCloud** | Synchronisation der Check-ins | Hintergrund |

![Systemfunktionen](/assets/images/GuardianTimer-1-Systemfunctions.png)

## Keine Tracking, keine Werbung

* **Keine Analytics** oder Nutzungsdaten werden gesammelt.
* **Keine Werbung** oder Drittanbieter-SDKs.

## Löschung von Daten

* Alle Daten werden automatisch gelöscht.
* Abonnements können jederzeit manuell gelöscht werden.
* Bei Deinstallation der App werden alle lokalen Daten unwiderruflich gelöscht.


**GuardianTimer schützt Sie – ohne Ihre Privatsphäre zu gefährden.**
