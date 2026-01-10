+++
date = '2026-01-09T18:22:15+01:00'
draft = false
title = 'Lass Claude kochen: Mein wöchentlicher Einkauf automatisiert'
description = 'Wie ich mit Claude Code eine Browser-Erweiterung gebaut habe, um meinen Einkauf von Cookidoo zu Knuspr zu automatisieren'
tags = ['automatisierung', 'chrome-extension', 'ki', 'produktivitaet']
categories = ['projekte']
+++

Jedes Wochenende stehe ich vor der gleichen Prozedur: die Einkäufe für die ganze Woche planen. Seit ich mir einen Thermomix zugelegt habe, kann ich meine Woche über die [Cookidoo](https://cookidoo.thermomix.com/)-App vorausplanen.

Cookidoo ist die Begleit-App zum Thermomix. Sie bietet eine große Auswahl an Rezepten, auf die man über die Web-App, die mobile App oder direkt über den Thermomix zugreifen kann. Diese Rezepte können gefiltert, als Favoriten markiert, in eigene Listen sortiert oder direkt zum Cookidoo-Kalender hinzugefügt werden. Die Idee hinter dem Kalender ist es, die kommenden Tage mit Cookidoo-Rezepten zu planen.

Außerdem kann man von jedem Rezept alle benötigten Zutaten zur Cookidoo-Einkaufsliste hinzufügen. Alle Zutaten aller Rezepte werden dann zusammengefasst.

{{< figure src="/blog/images/let-claude-cook-cookidoo-list.png" caption="Die Cookidoo-Einkaufsliste mit allen Zutaten" align="center" >}}

Mein aktueller Workflow jedes Wochenende sieht so aus:

1. Nach Rezepten für die kommende Woche suchen
2. Ein Rezept pro Wochentag hinzufügen
3. Für jedes Rezept auf „Zur Einkaufsliste hinzufügen" klicken
4. Meinen lokalen Vorrat mit der zusammengefassten Einkaufsliste abgleichen

Während Cookidoo durchaus auch die Möglichkeit bietet aus der Einkaufsliste direkt die Lebensmittel zu bestellen, ist es für mich aus zwei Gründen wenig hilfreich. Zuallererst habe ich nur vorselektierte Lieferdienste von Cookidoo zur Verfügung. Weiter wird versucht die Artikel automatisch auszuwählen. Das funktioniert in der Praxis ganz ok. Allerdings möchte ich gerne meine Artikel gerne selber auswählen anhand von Preis und Art. Gerade bei tierischen Produkten ist es mir wichtig, dass diese Bio sind.

Jedes Wochenende bleibt mir also die mühsame Aufgabe, jeden Artikel bei Knuspr zu suchen und in den Warenkorb zu legen. Das bedeutet für jeden Artikel aus Cookidoo kopieren, Tab wechseln und in die Knuspr-Suche eingeben, Artikel zum Warenkorb hinzufügen.

Als überambitionierter Softwareentwickler schien mir das ein guter Anwendungsfall zu sein, um eine stupide wiederkehrende Aufgabe zu automatisieren mit KI.

## Lass Claude kochen

Mein initialer Prompt an [Claude](https://claude.ai/) war:

> Ich brauche eine Chrome Extension, die meine Cookidoo Einkaufsliste in den Knuspr Einkaufskorb konvertiert. Also pro Artikel auf der Einkaufsliste soll in Knuspr gesucht werden. Es soll anschließend nach Preis-Leistung sortiert werden und evtl. Bio. Welche Probleme sind dafür zu lösen?

Claude hat direkt die Knuspr-Webseite durchsucht und versucht zu verstehen, wie sie funktioniert. Und hat mir eine fertige Version einer Chrome-Erweiterung geliefert. Überraschenderweise funktionierte sie direkt out of the box. Keine Fehler und eine sehr gute Nutzererfahrung.

Es wurde ein neuer Button zu meiner Cookidoo-Einkaufsliste hinzugefügt, der alle Artikel mit der Einkaufsliste der Erweiterung synchronisiert. Danach wird man direkt aufgefordert, Knuspr zu öffnen.

{{< figure src="/blog/images/let-claude-cook-sync-button.png" caption="Der Sync-Button der Erweiterung auf der Cookidoo-Seite" align="center" >}}

## Einkaufen für Fortgeschrittene

Auf der Knuspr-Webseite öffnet sich eine Seitenleiste mit der Einkaufsliste. Jeder Artikel hat einen Lookup-Button, der die Suche auf der Seite ausführt. Nachdem man den gesuchten Artikel gefunden hat, kann er abgehakt werden und man sucht den nächsten Artikel. Das geht so weiter, bis die Einkaufsliste komplett abgearbeitet ist.

{{< figure src="/blog/images/let-claude-cook-sidebar.png" caption="Knuspr mit der Einkaufslisten-Seitenleiste der Erweiterung" align="center" >}}

Am Ende hat man einen vollen Warenkorb mit selbst ausgewählten Lebensmitteln – aber ohne die nervige Aufgabe, für jeden Artikel zwischen Knuspr und der Einkaufsliste hin- und herzuwechseln.

Nach ein paar Anpassungen habe ich die Erweiterung fertiggestellt, die ich gerne mit euch teilen möchte. Während des Prozesses wurde mir klar, dass ich sie nicht auf Knuspr beschränken sollte. Zu Testzwecken habe ich auch Unterstützung für [Rewe](https://www.rewe.de/shop/) hinzugefügt.

Die Erweiterung kann im [Chrome Web Store](https://chromewebstore.google.com/detail/warenkorb+/kjgdjddfhgoeemlfgadcmipgfdojffbd) und als [Firefox Add-On](https://addons.mozilla.org/de/firefox/addon/warenkorb-plus/) installiert werden. Der Quellcode ist auf [GitHub](https://github.com/Lars147/warenkorb_plus) verfügbar.
