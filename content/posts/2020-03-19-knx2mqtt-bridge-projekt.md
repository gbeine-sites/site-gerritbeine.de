+++
title = 'KNX2MQTT Bridge-Projekt'
date = '2020-03-09'
categories = [ 'it' ]
tags = [ 'smart-home', 'home-automation', 'github', 'mqtt' ]
+++

In meinem Haus benutze ich den [Home Assistent](https://www.home-assistant.io/ "Home Assistant") zur Steuerung von Heizung, Sonnenschutz und anderen technischen Anlagen.
Der funktioniert ziemlich gut, hat aber natürlich auch ein paar Schwächen.
Eine davon ist, dass die Verbindung zu meinem KNX-Bus regelmäßig abbricht und nicht wieder aufgebaut wird.
<!--more-->

Der einzige Weg, dem mit Home Assistent zu begegnen, ist ein Neustart.
Der dauert nur ziemlich lange, setzt diverse Anlagen zurück und ist nicht planbar, weil der Ausfall der KNX-Verbindung erratisch stattfindet.

Die Ursachensuche hat mit immerhin die Erkenntnis gebracht, dass es nicht an der KNX-Bibliothek [xknx](https://xknx.io/ "xknx") liegt, sondern irgendwas mit dem Scheduling im Home Assistent zu tun hat.

Also habe ich mich mal drangesetzt und eine KNX-MQTT-Bridge geschrieben.
Das ging recht flott, weil zum einen fast alle KNX-relevanten Funktionen von xknx bereitgestellt werden und zum anderen MQTT recht einfach zu verwenden ist.

Das Ergebnis habe ich als [GitHub-Projekt](https://github.com/gbeine/knx2mqtt "knx2mqtt") unter der MIT Lizenz veröffentlicht.
Eine kurze [Anleitung und Einführung](https://github.com/gbeine/knx2mqtt/blob/master/README.md "Anleitung") ist dort zu finden, genauso wie Beispiele zur Konfiguration.
