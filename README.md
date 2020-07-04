# GERMAN translation fork from PIDtoolbox
--------------------------------------------------------------------

## BAUSTELLE'
Diese deutsche Übersetzung von PIDToolbox befindet sich im Aufbau und ist noch nicht vollständig übersetzt und erweitert. Daher bitte etwas Geduld


--------------------------------------------------------------------
Diese Deutsche Anleitung von PIDToolbox ist entstanden um Interessierten - nicht native-English-Speaker Menschen - auf relativ einfacher weise, die teileweise komplexen Zusammenhänge der unterschiedlichen Filter und Auswertungsmöglichkeiten Deiner Blackbox-Logdatei mit diesem Programm zu ermöglichen.

Die Übersetzung der englischsprachigen WIKI-Seite ist nicht 1:1 und beschreibt an einigen Stellen zusätzliche Dinge, die hoffentlich das Verständnis für die Zusammenhänge innerhalb der großen Datenmengen besser zu verstehen.

Wenn Ihr Fragen/Verbesserungsvorschläge oder anderes habt, dann schreibt einen Kommentar.

Dieses Wiki ist in Absprache mit dem Owner von PIDToolBox Brain White entstanden.

Wir wünschen Euch viel Spass mit Eurem Copter, den hunderten von Möglichkeiten das Flugverhalten zu studieren, zu verbessern und die Zusammenhänge zu verstehen.

Cheers
Bernd (alias LunaX) und Brain

# PIDToolbox - Intro
PIDtoolbox ist ein Tool zur graphischen Analyse  von Blackbox-Logdaten für FPV-Copter. 
Entwickelt wurde dieses eigentständige Programm zur Auswertung von Betaflight und INAV-Logdateien und ist  lauffähig unter MAC OS und Windows. 

PIDToolBox ist für FPV-Hobby Piloten die gerne herumbasteln und die bestmögliche Leistung aus seinem Copter herausholen möchten. Das Programm sollte aber auch für diejenigen, die neu in diesem Hobby sind, relativ einfach zu bedienen sein und es gibt ein detailliertes **<a href="https://github.com/bw1129/PIDtoolbox/wiki/PIDtoolbox-user-guide" target="blank">Wiki-Seite</a>**, was Dir dabei hilft die Auswertungen besser zu verstehen.

![](images/PIDtoolbox_v0.32.png)

# Motivation
Die Motivation für die Entwicklung dieses Werkzeugs war die Schaffung einer benutzerfreundlichen GUI zur Analyse von Blackbox-Daten unter Verwendung einer Hochsprache mit einfachen Plot- und Visualisierungswerkzeugen, die für einen größeren Teil der FPV-Gemeinschaft leichter zugänglich sind. MATLab bietet diesbezüglich hervorragende Möglichkeit komplexe Strukturen mit einem überschaubaren Aufwand zu analysieren und in graphischen Darstellungen darzustellen.

 Ein zweites Ziel war die Entwicklung einer objektiven Methode für den Vergleich zwischen Flügen, hierzu wurde die Möglichkeit implementiert zwei Flüge (Logdaten) miteinander direkt zu vergleichen. Insbesondere können So zum Beispiel Vibrationen, Throttle-Oszillationen, Propwash usw. einfach verglichen werden, ohne das Du immer merken musst, wie die vorherigen Werte waren. 
 
 Wenn du Deinen Copter optimieren musst, ändere nicht gleichzeitig mehre Einstellungen, eine anschließende Analyse wird dadurh deutlich erschwert. Durch die Möglichkeit das Du in PIDToolbox zwei Dateien miteinander vergleichen kannst ist es sehr einfach kurze hintereinander erstellte Logdateien schnell und einfach zu betrachten und du siehst schnell die Unterschiede und kannst entscheiden ob die Anpassungen erfolgreich waren.
 
 Vibrationen an Deinem Copter können Softwaretechnische oder Hardwaretechnische Gründe haben. Das Problem ist, dass subjektive Voreingenommenheit zu einem echten Problem werden kann, wenn die Unterschiede zwischen den Tests subtil sind. PIDtoolbox wurde unter diesem Gesichtspunkt entwickelt, Dir diese feinen Unterschiede zu visualisieren. 
 
 Im Folgenden findest Du alles, was Du benötigen, um mit PIDToolbox zu starten und Deine Logdateien zu analysieren.

# Download & Installation

**<a href="https://github.com/bw1129/PIDtoolbox/releases" target="blank">Download the latest version of PIDtoolbox.</a>** Unzippe die Datei in einem Verzeichnis Deiner Wahl. Bei der allerersten Installation nutze  **`MyAppInstaller_web`** Ist im Package (unter **`PIDtoolbox\runtime_installation_file\`**). **64 bit only!** Mit diesem Tools wird die notwendige Matlab Runtime installiert. Das kann einige Zeit in Anspruch nehemn, da die MATLab-Runtime sehr groß ist. Die MATLab Runtime  enthält alle  "standalone" Libraries, die notwendig sind um mit PIDToolbox Auswertungen und Analysen durchzuführen und sie anschließend in unterschiedlichen Graphen zu visualisieren. Der SourceCode von PIDToolbox ist selbst in MATLab geschrieben und wurde so auch compiliert. Daraus entstand die ausführebare PIDToolbox-Applikation.

**Nochmals der Hinweis: der Download von MATLab-Runtime wird mehrere Minuten in Anspruch nehmen.**

**Bitte beachte**
Wenn du bereits MATLab Runtime installiert hast (z.B 0.95), dann musst die nicht nochmals die Runtime installieren (aktuelle Version ist 0.97 (Stand 2020)). Du musst in dem Fall lediglich die PIDToolbox-Applikation ersetzen

**TIPS & TRICKS**
Sehr häufig werden Fehler gemeldet, dass Log-Dateien nicht richtig geladen werden können und das beim Start es zu Abbrüchen kommt. Die Meisten dieser Fehler sind damit begründet das  das**`blackbox_decode`**  Programm **nicht** im gleichen Ordner wie Deine Logdatei enthalten ist (also in dem Ordner wo Deine **`.bbl´** oder **`.bfl`** Dateien liegen)

Das **`PIDtoolbox`** Findest du unter  **`PIDtoolbox\main\`**. Der Inhalt des **`main`** Ordners sollte nicht geändert/verschoben werden. PIDtoolbox nutzt **`blackbox_decode`** von <a href="https://github.com/betaflight/blackbox-tools" target="blank">Betaflight/Cleanflight Blackbox Tools</a>, und ist im Download von PIDToolbox enthalten. 

**`blackbox_decode`**  ist für die Decodierung  der binären Logdatei zuständig.

* PIDtoolbox läuft unter  Windows7/8/10 64bit machines, and Mac 10.11 (El capitan), 10.13 (Sierra) , 10.14 (Mojave) und 10.15 (Catalina) . Wenn Du Probleme hast MATLAb-Runtime oder mit PIDtoolbox, bitte Poste Dein Issue (Englisch)**<a href="https://github.com/bw1129/PIDtoolbox/issues" target="blank">feedback here</a>**, oder auf Facebook **<a href="https://www.facebook.com/groups/291745494678694/?ref=bookmarks" target="blank">Betaflight BlackBox Log Review Facebook group</a>**  für Betaflight spezifische Dinge, rund um INAV kannst Du unter **<a href="https://www.facebook.com/groups/INAVOfficial/?ref=bookmarks" target="blank">INAV official Facebook group</a>** Hilfe finden.

* Wenn Du MATLab installiert hast und alle notwendigen Tools ebenfalls verfügbar sind, dann kannst du einfach den Sourcecode als ZIP herunterladen ( **<a href="https://github.com/bw1129/PIDtoolbox/releases" target="blank">releases</a>** herunterladen. Dies beinhaltet die aktuellesten Versionsstände von PID-Toolbox und kann aus dem Terminal heraus gestartet werden. 

### Disclaimer*
Im Prinzip ist es kein Problem wenn meine Logdateien irgendwo auf meinem Computer liegen, hauptsache das blackbox_decode Programm ist im gleichen Ordner enthalten.

Im interesse davon, dass weniger **Issues** gemeldet werden, bitten wir Euch, immer daran zu denken. "An dem Platz wo Deine Logdateien liegen - muss auch blackbox_decode liegen"


# Quick Guide

For a detailed guide to PIDtoolbox, please visit the **<a href="https://github.com/bw1129/PIDtoolbox/wiki/PIDtoolbox-user-guide" target="blank">PIDtoolbox Wiki page</a>**.

For a quick guide, follow the steps below:

**(i)** **<a href="https://github.com/bw1129/PIDtoolbox/releases" target="blank">PIDtoolbox</a>** (versions 0.2 onward) reads **`.bbl`** or **`.bfl`** files directly by decoding them using **`blackbox_decode`** <a href="https://github.com/betaflight/blackbox-tools" target="blank">(Betaflight/Cleanflight Blackbox Tools)</a>, which is conveniently packaged within the PIDtoolbox download (earlier versions required users to convert **`.bbl`** or **`.bfl`** files into **`.csv`** files). Just place your **`.bbl`** or **`.bfl`** files right in the main folder where the **`PIDtoolbox`** and **`blackbox_decode`** program files are already located. As stated earlier, the contents of this folder should not be moved. Start the program, select the file(s) you wish to load by clicking the **`select file`** button, then click **`load+run`**. NOTE: the Mac version does not show a "splash screen" when you run the program (an issue with Matlab for Mac), so it may seem like nothing is happening, but please be patient while it to loads.

**(ii)** It is recommended to log at 2k (unless you're running 1k loop rate in which case log at 1k), because the spectrograms only go to 1k. It is not recommended to log higher than 4k. It'll run, but much slower.

**(iii)** It is recommended that you set debug mode to **`GYRO_SCALED`** for PIDtoolbox. This is because the program expects the debug variables to contain the unfiltered gyro data, which is used to plot the filtered vs unfiltered gyro spectrograms, and compute gyro phase latency online. If you are using RPM filter in BF4.0, PIDtoolbox v0.2+ will recognize if you have debug mode set to **`DSHOT_RPM_TELEMETRY`**, and will plot RPM data along with motor signals in the Log Viewer. Just be aware that the debug mode you choose will result in different data contained in the 'gyro unfiltered' variable. For a list of debug modes and the data contained in the debug variable, see the **<a href="https://github.com/betaflight/betaflight/wiki/Debug-Modes" target="blank">Betaflight debug modes wiki</a>**.

If you have issues installing Matlab runtime, or running PIDtoolbox, please post **<a href="https://github.com/bw1129/PIDtoolbox/issues" target="blank">feedback here</a>**, or post a response in the **<a href="https://www.facebook.com/groups/291745494678694/?ref=bookmarks" target="blank">Betaflight BlackBox Log Review Facebook group</a>**, or **<a href="https://www.facebook.com/groups/INAVOfficial/?ref=bookmarks" target="blank">INAV official Facebook group</a>** for INAV specific issues.

# Acknowledgments

I have to give a long overdue shoutout to several people who contributed to this project outside GitHub. 
**Mark Spatz (UAVtech)** has been a huge source of information for me in general and it was through conversations with him that motivated the development of this tool in the first place. 
**Chris Thompson (ctzsnooze)** has always supported the project and continues to contribute great ideas that are continually integrated into various revisions of the tools.
**DusKing** converted the tooltips to Simplified Chinese language, and maintained and compiled this version for Chinese users. 
Many others have contributed thoughts and ideas that worked there way into various versions of the software, some of whom I only know by their Slack or Github name: **Qopter, Qratz, Zach Young, Zak Smiley, Stephen Wright, McGiverGim, Bizmar, Martin Hapl, Ken Kammerer, Paweł Spychalski**. I will continue to update this list. Thanks for your help!

 I hope you find PIDtoolbox useful, and I welcome feedback from the FPV community.

Cheers! -Brian
