+++
title = 'Tipps zur iSAQB CPSA-A-Prüfung'
date = '2021-04-05'
categories = [ 'isaqb' ]
tags = [ 'isaqb', 'software-architecture' ]
url = '/isaqb/iSAQB-CPSA-A'
+++

Ich bin jetzt seit 2016 als Prüfer für den Advanced Level des iSAQB tätig und habe in dieser Zeit sehr viele Arbeiten angesehen.

Die Prüfungen machen mir Spaß und häufig ist das Feedback der Prüflinge auch, dass ihnen die Diskussion und die Kritik an der Erstellung der Aufgabe etwas gebracht hat.
<!--more-->

Der Ablauf sieht prinzipiell vor, dass sich ein Prüfling für einen Themenbereich entscheidet und dann vom ausgewählten Zertifizierungsinstitut eine Aufgabe zugelost bekommt.

Dann gibt es einen Bearbeitungszeitraum von einigen Wochen und nach der Einreichung haben zwei Prüfer:innen vier Wochen Zeit für eine Bewertung.

Nachdem Gernot Starke und ich bereits im [INNOQ-Blog](https://www.innoq.com/en/blog/isaqb-advanced-exam-antipatterns/) einige häufige Antipattern beschrieben haben, möchte ich hier nochmal ein paar weitere Tipps beschreiben.
## Fragen ist erlaubt

Ihr dürft den Prüfer:innen Fragen stellen. Macht das auch!
Ich höre häufig, dass die Situation unrealistisch ist.
Das stimmt, das ist bei fast allen Prüfungssituationen der Fall.
Fragen ist aber erlaubt!
Ich freue mich darüber, wenn ihr mir eure Annahmen als Fragen schickt - das zeigt, dass ihr euch bewusst mit der Aufgabe auseinandersetzt und nicht nur Abschnitte abarbeitet.

Ich darf zwar keine inhaltlichen Hinweise geben, aber zu Annahmen äußere ich mich immer gern.

## Szenarien beschreiben Handlungen

Es gehört zum fundamentalen Handwerkszeug von Software-Architekt:innen, mit Qualitätsszenarien zu beschreiben, wie die entworfenen Software-Architektur Anforderungen erfüllt.
[Szenarien](https://de.wikipedia.org/wiki/Szenario) beschreiben Folgen von Ereignissen, Handlungen beispielsweise oder Abläufe.

Nutzt Qualitätsszenarien, um euch selbst zu prüfen. Schreibt nicht einfach irgendwelche technischen Anforderungen auf.

Folgt im Idealfall dem einfachen Muster Trigger-Reaktion des Systems-Ergebnis.
Denkt über Qualitätsszenarien so nach wie über [User Stories](https://de.wikipedia.org/wiki/User_Story).
Gute Qualitätsszenarien sind guten User Stories sehr ähnlich.

## Randbedingungen sind nicht eure Entscheidung

Beim Entwurf des Software-Architektur müsst ihr häufig mit Randbedingungen oder Rahmenbedingungen umgehen, die ihr nicht beeinflussen könnt.
Meistens werden organisatorische und technologische Randbedingungen unterschieden, manchmal kommen auch noch regulatorische dazu.

Wichtig für euch ist: diese Randbedingungen sind weder Anforderungen noch Entscheidungen.
Sie begrenzen aber den Raum, der euch für Entscheidungen und Handlungen im Architekturentwurf zur Verfügung steht.
Seid genau, beim Benennen dieser Randbedingungen.
Interpretiert nicht zu viel hinein, aber lasst auch keine weg.

## Urlaub ist kein Risiko

Viele Software-Architekt:innen tun sich unglaublich schwer mit dem Benennen und Bewerten von Risiken.
Dazu kommt dann die unsägliche Boston-Consulting-Risiko-Matrix, die an Blödsinnigkeit kaum zu überbieten ist.

Dann passiert es, dass Urlaub des Product Owners als Risiko mit Eintrittswahrscheinlichkeit hoch beschrieben wird.
Oder dass Risiken benannt werden, die gar nichts mit der Software-Architektur zu tun haben, wie z.B. dass Kunden das Produkt nicht kaufen.

Wenn ihr Risiken benennen sollt, dann überlegt zunächst mal, was die negativen Konsequenzen eurer Architekturentscheidungen sein könnten.
Und zeigt mir mit einer Zahl, dass ihr euch Gedanken gemacht habt.
Nutzt eine [Fermi-Dekomposition](https://de.wikipedia.org/wiki/Fermi-Problem), um die Schadenshöhe zu bewerten.
Und schreibt bitte nicht, dass Weihnachten und Ostern Risiken sind, die das Projekt verzögern.

## to be continued...

Ich werde hier im Laufe der Zeit sicher immer wieder ein paar Tipps schreiben.
Folgt mir am besten auf [LinkedIn](https://linkedin.com/in/gerritbeine), um das direkt zu erfahren.