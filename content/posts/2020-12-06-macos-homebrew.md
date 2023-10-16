+++
title = 'macOS & homebrew'
date = '2020-12-06'
categories = [ 'it' ]
tags = [ 'unix', 'macos' ]
+++

Seit ich 2012 vom Thinkpad W520 auf das MacBook Pro Retina umgestiegen bin, nutze ich homebrew.

Ich konnte auch schon ein paar Packages und Patches beisteuern.
<!--more-->

Abweichend vom Standard habe ich homebrew seit jeher unter `/opt/homebrew`  installiert.
Das empfohlene `/usr/local` nutze ich bewusst nicht, aber darüber schreibe ich ein anderes Mal.

Blöderweise ist dieser Pfad aber seit kurzem reserviert für die ARM-Architektur:
Auf Intel-MacBooks kann man kein homewbrew mehr unter `/opt/homebrew` installieren.

Also habe ich mich mal schlau gemacht, was die Alternativen sind und das Upgrade auf Big Sur direkt genutzt, um homewbrew umzuziehen.
Es liegt jetzt unter `/homebrew` auf einem eigenen Volume.

Hier nun eine Anleitung, wie das funktioniert.

Zunächst muss der Pfad `/homebrew` erstellt werden.
Das geht unter Big Sur nicht einfach mit `mkdir` - auch nicht als root.
Stattdessen benötigt es einen Eintrag in `/etc/synthetic.conf`, den man wie folgt erstellen kann:

{{< highlight shell >}}
echo 'homebrew' | sudo tee -a /etc/synthetic.conf
{{< /highlight >}}

Anschließen muss das MacBook neu gestartet werden.

Jetzt kann das Volume erstellt werden.
Das geht am einfachsten an einem Terminal mit diesen Kommandos:

{{< highlight shell >}}
sudo diskutil apfs addVolume disk1 APFS homebrew -mountpoint /homebrew
sudo diskutil enableOwnership /homebrew
sudo chflags hidden /homebrew
echo "LABEL=homebrew /homebrew apfs rw" | sudo tee -a /etc/fstab
{{< /highlight >}}

Damit wir ein neues Volume mit dem Name homebrew erzeugt und in dem gerade erstellten Pfad `/homebrew` gemountet.
Das `chflags` ist nicht nötigt, wenn das Icon auf dem Desktop nicht stört.

Anschließen kann homebrew installiert werden.
Hier muss `gbeine` natürlich durch den eigenen Benutzernamen ersetzt werden.

{{< highlight shell >}}
sudo chown gbeine:staff /homebrew
cd /
curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew
{{< /highlight >}}

Zum Schluss noch ein 

{{< highlight shell >}}
export PATH=/homebrew/bin:$PATH
{{< /highlight >}}

an geeigneter Stelle in der `.zshrc` hinzufügen und alles läuft wie geschmiert.

Quellen:

* [How to make root volume writeable again in Catalina](https://apple.stackexchange.com/questions/371908/how-to-make-root-volume-writeable-again-in-catalina)
* [Handle macOS Homebrew on ARM](https://github.com/Homebrew/brew/commit/5afff3f3aa1d806855d460e5f39bfbef28ef6262)
