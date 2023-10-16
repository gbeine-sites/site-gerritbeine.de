+++
title = 'macOS Developer Tools'
date = '2020-10-09'
categories = [ 'it' ]
tags = [ 'unix', 'macos', 'linux', 'programming' ]
+++

Ich darf mich aktuell mal wieder mit Linux umtun.
So richtig ehrliches Hacken, Coden und mit dem Compiler die CPU-Lüfter zum heulen bringen.

Daher sammele ich jetzt mal ein paar Tipps, wie sich diese Arbeit mit macOS erledigen lässt.
<!--more-->

## Verschiedene Versionen der Command Line Tools

Von Haus aus gibt es auf macOS immer nur eine Version der Command Line Tools.
Welche das ist, erfährt man via:

{{< highlight shell >}}
xcode-select -p
{{< /highlight >}}

Manchmal ist das aber nicht die, die man benötigt.
Dann braucht es etwas Magie.
Oder gezieltes Suchen bei Stackoverflow.

Um weitere Versionen der Command Line Tools parallel zu installieren, lädt man sich zunächst die entsprechende Version bei [Apple herunter](https://developer.apple.com/download/more/).
Das DMG klickt man dann ganz normal an und es erscheint der Pfad `/Volumes/Command Line Developer Tools`.

Als nächstes benötigt man einen lokalen Pfad für die Installation.
Ich mache das unter `~/Developer/<Version>/CommandLineTools`.
Also für den Fall der Command Line Tools 11.5:

{{< highlight shell >}}
mkdir -p ~/Developer/11.5/CommandLineTools
{{< /highlight >}}

Als nächstes muss das Package ausgepackt werden.
Dafür gibt es eine nicht-dokumentierte Option für `pkgutils`: `--expand-full <pkg> <dir>`.
Das Verzeichnis, in das ausgepackt werden soll, darf es noch nicht geben.

Der Befehl dazu lautet dann:
{{< highlight shell >}}
pkgutil --expand-full /Volumes/Command\ Line\ Developer\ Tools/Command\ Line\ Tools.pkg ~/Developer/tmp
{{< /highlight >}}

Als nächstes müssen die Dateien aus dem Package in das Installationsverzeichnis kopiert werden:

{{< highlight shell >}}
cp -a Developer/tmp/CLTools_Executables.pkg/Payload/Library/Developer/CommandLineTools/* Developer/11.5/CommandLineTools
cp -a Developer/tmp/CLTools_macOS1014_SDK.pkg/Payload/Library/Developer/CommandLineTools/* Developer/11.5/CommandLineTools
cp -a Developer/tmp/CLTools_macOS1015_SDK.pkg/Payload/Library/Developer/CommandLineTools/* Developer/11.5/CommandLineTools
cp -a  Developer/tmp/CLTools_macOS_SDK.pkg/Payload/Library/Developer/CommandLineTools/* Developer/11.5/CommandLineTools
rm -rf Developer/tmp
{{< /highlight >}}

Wenn das erledigt ist, kann die Auswahl der Command Line Tools angepasst werden:

{{< highlight bash-session >}}
gbeine@mbpgb ~ % clang --version
Apple clang version 12.0.0 (clang-1200.0.32.2)
Target: x86_64-apple-darwin19.6.0
Thread model: posix
InstalledDir: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin
gbeine@mbpgb ~ % sudo xcode-select -s ~/Developer/11.5/CommandLineTools/
gbeine@mbpgb ~ % xcode-select -p
/Users/gbeine/Developer/11.5/CommandLineTools
gbeine@mbpgb ~ % clang --version
Apple clang version 11.0.3 (clang-1103.0.32.62)
Target: x86_64-apple-darwin19.6.0
Thread model: posix
InstalledDir: /Users/gbeine/Developer/11.5/CommandLineTools/usr/bin
gbeine@mbpgb ~ %
{{< /highlight >}}

Geholfen haben mir dabei zwei Threads auf Stackoverflow:

* [How to switch between multiple Command Line Tools installations in Mac OS X (without installing XCode)](https://stackoverflow.com/questions/47455245/how-to-switch-between-multiple-command-line-tools-installations-in-mac-os-x-wit)
* [How to extract contents from 'Payload' file in a apple macOS update package?](https://stackoverflow.com/questions/41166805/how-to-extract-contents-from-payload-file-in-a-apple-macos-update-package)

## OpenWRT bauen

* [Setup MacOSX as an OpenWrt build environment](https://openwrt.org/docs/guide-developer/easy.build.macosx)
* [OpenWrt Buildroot – Installation on macOS](https://openwrt.org/docs/guide-developer/buildroot.exigence.macosx)
