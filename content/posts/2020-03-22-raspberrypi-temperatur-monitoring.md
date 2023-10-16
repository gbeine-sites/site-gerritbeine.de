+++
title = 'RaspberryPi Temperatur-Monitoring'
date = '2020-03-22'
categories = [ 'it' ]
tags = [ 'unix', 'linux', 'monitoring', 'github' ]
+++

Ich habe sehr viele kleine Raspberry Pi im Einsatz.
Einige davon dienen mir zur Haussteuerung, andere als Medien-Center und einer werkelt im Schuppen und sammelt Wetterdaten.

Vor einer Weile habe ich mich mal hingesetzt und ein kleines Plugin für Nagios und Icinga geschrieben, das die Temperaturen dieser Raspberry Pi überwacht.
Das Plugin ist auf [GitHub][1] zu finden. 
<!--more-->

Die Verwendung ist denkbar einfach:
```
root@monitor:~# /usr/local/lib/nagios/plugins/check_rpi_temperature
OK; 41.2'C
root@monitor:~# 
```

Standardwerte sind 50°C für *warning* und 60°C für *critical*.
Es kann auch ein Parameter angegeben werden, der dann als Schwellenwert für *warning* benutzt wird.
Der Schwellenwert für *critical* ist immer 10° höher:
```
root@monitor:~# /usr/local/lib/nagios/plugins/check_rpi_temperature 40
WARNING; 40.1'C
root@monitor:~# /usr/local/lib/nagios/plugins/check_rpi_temperature 30
CRITICAL; 40.1'C
root@monitor:~# 
```

Das Plugin benutzt die `utils.sh` aus dem Paket `monitoring-plugins-common` unter Debian (andere Distributionen bieten das Paket unter anderem Namen an) und `vcgencmd` aus dem Paket `libraspberrypi-bin`.

Happy hacking!

[1]:	https://github.com/check-plugins/check_rpi_temperature "Raspberry Pi temperature plugin for Nagios/Icinga"
