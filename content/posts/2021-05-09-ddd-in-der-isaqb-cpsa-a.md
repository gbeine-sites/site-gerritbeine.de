+++
title = 'Domain Driven Design in der iSAQB CPSA-A-Prüfung'
date = '2021-05-09'
categories = [ 'isaqb' ]
tags = [ 'isaqb', 'software-architecture', 'ddd' ]
+++

Vor einer kleinen Weile habe ich ein paar [erste Tipps für die CPSA-A-Prüfung](https://gerritbeine.de/isaqb/iSAQB-CPSA-A/) hier auf meinem Blog geteilt, nun ist es Zeit für eine Fortsetzung.

Diesmal möchte ich mich zu Domain Driven Design in der Ausarbeitung zur Prüfung äußern.

Ich bin Fan von DDD seit ungefähr 2005. Ich bin sogar Besitzer eines Exemplars der Erstauflage des Blauen Buches. Es hat mir in meiner Diplomarbeit 2006 unglaublich geholfen.

Seitdem hat sich viel getan, handwerklich wie methodisch und DDD hat viele Fans gewonnen - auch unter den CPSA-A-Kandiat:innen. Daher diesmal ein paar Tipps aus meiner Prüferperspektive zum Einsatz von DDD in der CPSA-A-Prüfung.

## Domain Driven Fiction

In einigen CPSA-A-Aufgaben kann es sinnvoll sein, sich der Fachlichkeit mit den Mitteln von DDD zu nähern. Manchmal ist das sogar mehr als nur sinnvoll, aber das merkt ihr dann schon.

Seit einiger Zeit kommen immer wieder Prüfungen, in denen Workshop-Methoden aus dem DDD-Kontext adaptiert werden. Das macht praktisch wenig Sinn und führt auf Seiten von uns Prüfer:innen nur zu der Frage: hat dieser Mensch verstanden, worum es dabei eigentlich geht?

Wenn jemand ein Viertel seiner Arbeit mit der Beschreibung eines fiktiven Event Storming Workshops füllt, dann komme ich ganz schnell zu dem Schluss: Nein, vermutlich nicht.

Denn das ist dann DD-Fiction, nicht DDD. Es ist völlig in Ordnung, zu erwähnen, dass ihr in der Praxis mit den Stakeholder und Nutzer:innen einen Event Storming-Workshop machen würdet. Das kann ich anerkennen, und ich denke die meisten anderen Prüfer:innen ebenfalls.

Aber sich einen solchen Workshop auszudenken, mit Ergebnissen, die nur eurer Fantasie entspringen, sagt über eure Fähigkeiten als Architekt:in rein gar nichts.

## Es lebe die Ubiquitous Language!

DDD lebt von den kontextspezifischen allgegenwärtigen Sprachen. Und Software-Architektur ebenfalls. Es ist äußerst lobenswert, wenn ihr für den Kontext eurer Aufgabenstellung eine UL entwickelt, die ihr im Architekturentwurf benutzt.

Aber wenn ihr dann für eben diesen Entwurf all die wunderbaren formalen Sprachen ignoriert, die das Software Engineering uns geschenkt hat und nur informelle Kästen und Striche zeichnet, dann macht ihr das sofort wieder kaputt.

Ja, UML mag kompliziert sein. Und sperrig. Aber UML ist eine UL für Software-Architekturentwürfe. Auf diesem Gebiet ist sie umgemein praktisch, weil sie stark standardisiert ist und in Situationen, in denen man nicht über die Bedeutung des informellen sprechen kann, eine ausreichende Klarheit herstellt.

Ihr dürft euch natürlich trotzdem gegen UML entscheiden, das kreidet euch niemand an. Aber dann müsst ihr die Notation, die ihr verwendet, so weit formalisieren und dokumentieren, dass sie in der Prüfungssituation Bestand haben kann.

Wer schon mal formale Sprachen designed hat weiß: es ist leichter, einfach UML zu lernen.

## Auch DDD kennt formale Konstrukte

Der dritte Aspekt, der mir häufig bei der Anwendung von DDD in den Prüfungen begegnet, ist eine Anhäufung von Missverständnissen, was die DDD-Termini bedeuten.
Wann ist etwas ein Value Object? Wann eine Entity? Warum ist es potentiell ein Problem, wenn ich zehn Root Aggregates in meiner Subdomain habe? Und warum gibt es Services, wo doch Entities selbst schon Verhalten haben.

Ich werde jetzt nicht alles erklären, was klügere Menschen schon anderswo getan haben, aber ich möchte euch bitten:
Bevor ihr in eurer CPSA-A-Prüfung mit DDD anfangt, lest [dieses kleine Büchlein](https://leanpub.com/ddd-referenz), dass tolle Kollegys von mir übersetzt haben.

Ihr tut euch und euren Prüfer:innen damit einen großen Gefallen.

## to be continued...

Ich werde hier im Laufe der Zeit sicher immer wieder ein paar Tipps schreiben.
Folgt mir am besten auf [LinkedIn](https://linkedin.com/in/gerritbeine), um das direkt zu erfahren.
