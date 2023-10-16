+++
title = 'Scaling Agile simulieren mit dem getKanban Board Game'
date = '2020-03-05'
categories = [ 'training' ]
tags = [ 'agile', 'kanban' ]
+++

Seit vielen Jahren benutzen ich das [**getKanban Board Game**](https://getkanban.com/ "The getKanban Board Game") wann immer ich Teams an Kanban, Costs of Delay oder andere agile Ideen heranführen möchte.

Das **getKanban** ist brilliant: durchdachter Ablauf, klare Regeln und die Szenen im Spielverlauf passen hervorragend zur Arbeitswirklichkeit fast aller Teams, denen ich begegne.
<!--more-->

Vor einer ganzen Weile habe ich mir einige zusätzliche Regeln ausgedacht, mit denen auch skaliertes Arbeiten simuliert werden kann. Bis zu fünf Teams spielen **getKanban** nicht gegeneinander, sondern arbeiten gemeinsam an einem Produkt. Die Teams gewinnen damit in kurzer Zeit sehr viele wertvolle Erkenntnisse hinsichtlich der Skalierung agiler Methoden.

## Regeln für getKanban - Scaled
Regeln müssen maximal einfach sein, daher beschränke ich mich für das Scaling auch auf eine einzige:

**Geradzahlige S-Tickets können nur von allen Teams gemeinsam deployed werden.**

Mit anderen Worten: wenn alle Teams am Ende des ersten Tages die Tickets S2 und S4 auf _Ready for Deployment_ gezogen haben, können beide Tickets deployed werden. Hat ein Team das nicht geschafft (am ersten Tag ;-), kann das Deployment dieses Tickets nicht stattfinden.

## Wirkung der Regel
So einfach die Regel ist, so stark ist ihre Wirkung auf das, was in den Teams passiert. Das Deployment der geradzahligen Features wird viel schwieriger, wenn man es nur gemeinsam durchführen kann.

Die Regel lässt folgende Aspekte der teamübergreifenden Zusammenarbeit sichtbar werden:
- Das Deployment kann nicht mehr autark erfolgen
- Das Replenishment kann nicht mehr autark erfolgen
- Würfeleien bei einem Team haben plötzlich Auswirkungen auf die anderen Teams
- Intangibles sind viel weniger nützlich, wenn sie nicht in allen Teams umgesetzt werden
- Die Product Owner müssen sich abstimmen, was sie als nächste Optionen auswählen wollen
- Die Teams müssen sich über die Reihenfolge und Priorisierung während der Bearbeitung der Tickets abstimmen

Um diese Dinge tatsächlich sichtbar werden zu lassen, mache ich mit den Teams nach jedem Billing Cycle eine kurze übergreifende Retrospektive. Das zwingt zu einem gemeinsamen Takt und verlängert das Spiel. Es ist aber notwendig, um die Teilnehmer nicht zu frustrieren.

## Verhalten und Erkenntnisse der Teilnehmer
Die Erkenntnisse der Teilnehmer treten nicht zwangsläufig in einer bestimmten Reihenfolge auf. Erfahrene Moderatoren haben aber durchaus die Möglichkeit, sie über verschiedene Wege herbeizuführen. Je nach Kontext des Teams kann es natürlich sinnvoll sein, einen anderen Weg zu gehen. Deshalb beschreibe ich hier keinen Ablauf, sondern nur ein paar Bausteine zum Verhalten und den Erkenntnissen der Teilnehmer.

### Abhängigkeiten im Deployment
Die Abhängigkeiten im Deployment werden sehr schnell sichtbar, spätestens am Tag 12. Manchmal erkennen Teams schon vorher, dass sie etwas tun müssen, um deployment-fähig zu werden. Dabei werden die Effekte von Pete und Carlos durch die Scaling-Regel noch verstärkt.

Im Idealfall erkennen die Teams früh, dass sie sich synchronisieren müssen und dass das Deployment dafür eigentlich zu spät ist. Ein sichtbares Board auf einem Flipchart ist eine gute Lösung. So ein Board bereite ich auch immer schon vor.

### Planen und Replenishment
Damit die Teams an den gleichen Dingen arbeiten, müssen sie sich hinsichtlich ihrer Replenishments abstimmen. Das passiert idealerweise durch die Product Owner vor dem Replenishment - also zum Beispiel für den Tag 14, während sich das Team durch den Tag 13 würfelt.

Auch dafür ist ein Board sehr nützlich, auf dem die Themen sichtbar werden, die gemeinsam angegangen werden sollen. Eine wichtige Erkenntnis dabei ist, dass diese Diskussion tatsächlich täglich stattfinden muss und nicht nur einmal für den Billing Cycle.

Spannend wird es, wenn sich die Teilnehmer entscheiden, dass es keine explizite Abstimmung geben soll, sondern stattdessen eine Regel eingeführt wird, nach der die einzelnen Teams selektieren.
Diese Regel kann z.B. Weighted Shortest Job First sein, basierend auf dem Business Value und den zu würfelnden Punkten. Diese Regel hat in einigen Simulationen tatsächlich gut funktioniert, auch wenn es einige Unschärfen gibt, weil es dann eben doch passieren kann, dass Teams nicht an exakt dem gleichen Thema arbeiten.
  
Eine gute Frage für das Debriefing ist, ob diese Unschärfen oder die Zeit für das gemeinsame Planen teurer sind.

### Intangibles
Die Wirkung von Intangibles bleibt lokal gesehen natürlich gleich. Allerdings nützt es deutlich weniger, wenn nur ein Team automatisch deployen kann. Das Team kann dann ungerade S-Tickets fertigstellen, aber die geraden S-Tickets müssen trotzdem auf die anderen Teams warten.

Auch der Effekt der Testautomatisierung verändert sich. Sofern nicht alle Teams Testautomatisierung beherrschen, kann es sein, dass Tickets dann einfach länger in _Ready for Deployment_ liegen bleiben.

Das Datenbank-Upgrade, dass die wertvollsten Tickets liefert, kann natürlich unabhängig angegangen werden. Da aber für die geradzahligen Tickets aus dem Set 3 das gleiche gilt wie für alle Standard-Tickets, bleibt die Hälfte davon liegen, wenn nicht alle Teams das Upgrade durchgeführt haben.

### Teampriorisierung
In der skalierten Version lernen Teams eine wichtige Lektion: Sie können nicht mehr alles selbst bestimmen. Das ist für viele ein Bruch mit Selbstorganisation, insbesondere weil die Priorisierung im normalen **getKanban** von vielen Teams ausgehandelt wird.

In der skalierten Version müssen die Teams lernen, ihren Product Ownern zu vertrauen, dass diese sich auf sinnvolle Tickets einigen, die dann gemeinsam entwickelt werden. Umgekehrt muss sich ein Product Owner natürlich auch auf das Team verlassen können.

In einigen Simulationen hat das Team sich nicht an die Absprachen des eigenen Product Owners gehalten. Das hat dann natürlich vor allem bei den anderen Teams für schlechte Stimmung gesorgt. Wie im echten Leben halt ;-)

## Sinnvolle Maßnahmen & Lektionen
Ich bereite immer zwei Flipcharts als Boards zur Synchronisation vor. Eines für die Teams, das deren Boards widerspiegelt und eines für die Product Owner, das nur die Spalten _Selected_, _In Progress_ und _Ready_ kennt.

 Das erste Board ist sehr spannend, weil man hier viel für die tägliche Synchronisation lernen kann: Haben wir Swimlanes pro Team auf dem Board? Fassen wir Tickets der Teams zu einem zusammen? Führt das Team, das am weitesten fortgeschritten ist oder das Team, das am weitesten zurückliegt? Wie oft treffen wir uns? Wann aktualisieren wir das Board und wer geht hin?

Das Board für die Product Owner bietet ebenfalls eine spannende Lernkurve. Es ist am Anfang irritierend, dass die einzelnen Schritte des Team-Prozesses hier nicht zu sehen sind. Aber die Product Owner benötigen diese gar nicht. Es reicht, wenn sie wissen, wie viel Arbeit im System ist und wie lange es im Mittel dauert, um zu entscheiden, was als nächstes _gemeinsam_ angegangen werden soll.

## Fazit
Die oben genannte Regel und die zwei zusätzlichen Boards haben mir in der Arbeit mit Teams schon oft geholfen. Die Erkenntnisse zu den Voraussetzungen und Konsequenzen von skalierter Agilität sind sehr wertvoll, um ein wirkungsvolles Coaching umsetzen zu können.

Die Regeln und die Tipps zur Moderation stelle ich unter {{< cc-by-sa-40 >}}.
