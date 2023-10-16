+++
title = 'SNMP Syslog-Meldungen unter Debian'
date = '2020-12-14'
categories = [ 'it' ]
tags = [ 'unix', 'linux', 'snmp', 'monitoring' ]
+++

Ich benutze ganz gerne SNMP um Daten über meine Linux-Rechner zu sammeln und sie zu überwachen.

Leider hat net-snmpd unter Debian die Eigenart, `/var/log/syslog` mit Meldungen zuzumüllen.
<!--more-->

Das schaut dann in etwa so aus:

```
Dec 14 00:00:31 host19 snmpd[17617]: error on subcontainer 'ia_addr' insert (-1)
Dec 14 00:01:01 host19 snmpd[17617]: error on subcontainer 'ia_addr' insert (-1)
Dec 14 00:01:31 host19 snmpd[17617]: error on subcontainer 'ia_addr' insert (-1)
Dec 14 00:02:01 host19 snmpd[17617]: error on subcontainer 'ia_addr' insert (-1)
Dec 14 00:02:31 host19 snmpd[17617]: error on subcontainer 'ia_addr' insert (-1)
Dec 14 00:03:01 host19 snmpd[17617]: error on subcontainer 'ia_addr' insert (-1)
Dec 14 00:03:31 host19 snmpd[17617]: error on subcontainer 'ia_addr' insert (-1)
Dec 14 00:04:01 host19 snmpd[17617]: error on subcontainer 'ia_addr' insert (-1)
Dec 14 00:04:31 host19 snmpd[17617]: error on subcontainer 'ia_addr' insert (-1)
Dec 14 00:05:01 host19 snmpd[17617]: error on subcontainer 'ia_addr' insert (-1)
```

Um das zu lösen, musste ich schon mal auf Seite Zwei der Google-Ergebnisse blättern, denn auch wenn ich wohl nicht der einzige mit dem Problem bin, hat kaum jemand eine echte Lösung beschrieben.

## Wie man es nicht machen kann

Die erste Lösung - die nicht unter Debian 10 funktioniert - ist, in `/etc/default/snmpd` die folgende Zeile zu ändern:

```
#SNMPDOPTS='-Lsd -Lf /dev/null -u Debian-snmp -g Debian-snmp -I -smux,mteTrigger,mteTriggerConf -p /run/snmpd.pid'
```

in

```
SNMPDOPTS='-LS6d -Lf /dev/null -u Debian-snmp -g Debian-snmp -I -smux,mteTrigger,mteTriggerConf -p /run/snmpd.pid'
```

Leider funktioniert das, wie gesagt nicht unter Debian 10.
Es ist aber witzigerweise die am häufigsten auffindbare "Lösung".

## Wie man es nicht machen sollte

Debian 10 benutzt die `/etc/default/snmpd` einfach nicht mehr.
Ich denke jetzt nicht darüber nach, warum die dann noch da ist, sondern suche direkt nach der nächsten "Lösung" und siehe da:

Der Vorschlag ist `/lib/systemd/system/snmpd.service` zu editieren oder zu kopieren und dann zu editieren.

Das ist natürlich beides sehr ungünstig, weil das entweder durch das nächste Update verloren gehen könnte oder das Update nicht funktioniert, weil eine Datei geändert wurde oder niemand damit rechnet, dass jemand so eine Service Description für **systemd** kopiert.

## Wie man es machen sollte, so dass es funktioniert

Schlußendlich habe eine Lösung entdeckt, die tatsächlich funktioniert.

**systemd** kennt ein `edit` Kommando, dass die originalen Service Descriptions unangetastet lässt und die Änderungen an einem Standardort ablegt.
Das Kommando lautet: `systemctl edit snmpd.service`
Dieses Kommando öffnet nicht, wie man vermuten könnte, die originale Datei mit der Service Description, sondern eine andere Datei, in der man Teile der Service Description überschreiben kann. 

Es öffnet sich der Editor des Vertrauens und man schreibt einfach in die (beim ersten Öffnen leere) Datei:

```
[Service]
ExecStart=
ExecStart=/usr/sbin/snmpd -LS6d -Lf /dev/null -u Debian-snmp -g Debian-snmp -I -smux,mteTrigger,mteTriggerConf -f
```

Wichtig ist, dass man beide `ExecStart` Einträge schreibt.
Der erste Eintrag löscht die Konfiguration aus der originalen Service Description (lässt man die weg, bekommt man die schöne Meldung `snmpd.service: Service has more than one ExecStart= setting, which is only allowed for Type=oneshot services. Refusing.` und der Service kann nicht gestartet werden), der zweite Eintrag ist der neue Befehl für den Start des **snmpd**.

Die neue Datei liegt unter `/etc/systemd/system/snmpd.service.d/override.conf` - ein logischer Platz und ein logischer Name.
Man kann die Datei auch von Hand anlegen, dann muss man allerdings `systemctl daemon-reload` selbst ausführen - `systemctl edit` nimmt einem das ab.

Die lästigen Meldungen von **snmpd** bin ich jetzt los und habe wieder ein Detail zu **systemd** gelernt.

Quellen:

* [How can I disable snmpd ia_addr insert messages?](https://linux-tips.com/t/how-can-i-disable-snmpd-ia-addr-insert-messages/281)
* ["snmpd: error on subcontainer 'ia_addr' insert (-1)" fixen](https://wiki.magenbrot.net/linux/linux_distributionen/debian/snmpd_error_on_subcontainer_ia_addr_insert_-1_fixen)
