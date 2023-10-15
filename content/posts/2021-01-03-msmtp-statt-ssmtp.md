+++
title = 'msmtp statt ssmtp'
date = '2021-01-03'
categories = [ 'linux' ]
tags = [ 'linux', 'home-automation' ]
+++

Ich hatte auf vielen meiner Raspberry Pis lange Jahre [ssmtp](https://wiki.debian.org/sSMTP) laufen, um E-Mails ohne großen Mailserver versenden zu können.
Die E-Mails habe ich über ein mailbox.org-Postfach verschickt.

Leider wird ssmtp nicht mehr gepflegt und mailbox.org hat den Versand auch verriegelt, so dass das nicht mehr so einfach geht.

Als Alternative bin ich jetzt bei [msmtp](https://wiki.debian.org/msmtp) und [mailgun](https://www.mailgun.com/) angekommen.
msmtp ein guter Ersatz für ssmtp und kann wie ein lokal installiertes sendmail benutzt werden.

Die Installation ist denkbar einfach:

```apt install msmtp msmtp-mta```

Danach muss die Konfigurationsdatei ```/etc/msmtprc``` erstellt werden:

```
defaults

account default
host smtp.eu.mailgun.org
port 587
tls on
tls_starttls on
auth on
user mailgun-user
password mailgun-password

auto_from on
maildomain beine-computer.de

# Syslog logging with facility LOG_MAIL instead of the default LOG_USER
syslog LOG_MAIL
```

Wie oben geschrieben, nutze ich mailgun für den Versand.
Dort kann man mehrere Domains registrieren und entsprechende SMTP-Accounts anlegen, um E-Mails zu versenden.
Der Service läuft recht zuverlässig, auch bei größeren Mengen.

https://arnaudr.io/2020/08/24/send-emails-from-your-terminal-with-msmtp/
https://stackoverflow.com/questions/42403155/msmtp-cannot-send-emails-with-php-when-setting-the-from
