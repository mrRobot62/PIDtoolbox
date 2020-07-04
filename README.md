# GERMAN translation fork from PIDtoolbox
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



The motivation for the development of this tool was to create a user-friendly GUI for analyzing blackbox data, using a high-level language with simple plotting and visualization tools that are more accessible to a larger part of the FPV community. A second goal was to develop an objective method for comparing between flights. It was inspired by the way we often troubleshoot flight performance issues (e.g., vibrations, mid-throttle oscillation, propwash), where we make back to back test flights with slight changes in software/hardware/mechanical settings with each test, and then make subjective inferences about flight performance. The problem is subjective bias becomes a real issue when the differences between tests are subtle. PIDtoolbox was designed with this in mind. Below is everything you need to begin using PIDtoolbox.

# Download

**<a href="https://github.com/bw1129/PIDtoolbox/releases" target="blank">Download the latest version of PIDtoolbox.</a>** Unzip and place entire folder in a preferred location on your computer. For first time installation, use the **`MyAppInstaller_web`** file included in the package (under **`PIDtoolbox\runtime_installation_file\`**). **64 bit only!** This will install Matlab Runtime, which contains the standalone set of libraries that enables the execution of compiled MATLAB application. It's a fairly big download so hang in there :-) 

**NOTE: if you already have a running version of Ptb, you DON'T need to re-run the installer. Just grab the new PIDtoolbox program file and replace with your old version!**

The **`PIDtoolbox`** program file can be found under **`PIDtoolbox\main\`**. The contents of the **`main`** folder should not be moved. PIDtoolbox uses **`blackbox_decode`** from <a href="https://github.com/betaflight/blackbox-tools" target="blank">Betaflight/Cleanflight Blackbox Tools</a>, which is conveniently packaged within this download. The **`blackbox_decode`** program file should also remain in the main folder (or at the very least must be in the same folder as your **`.bbl`** or **`.bfl`** log files. **Disclaimer**: Personally I've had no issue with placing my log files anywhere on my computer as long as blackbox_decode is in there with them, but in the interest of having less reported issues, I'm erring on the side of caution with these recommendations, but feel free to experiment.

* PIDtoolbox has been confirmed to run on Windows7/8/10 64bit machines, and Mac 10.11 (El capitan), 10.13 (Sierra) and 10.14 (Mojave). If you have issues installing Matlab runtime, or running PIDtoolbox, please post **<a href="https://github.com/bw1129/PIDtoolbox/issues" target="blank">feedback here</a>**, or post a response in the **<a href="https://www.facebook.com/groups/291745494678694/?ref=bookmarks" target="blank">Betaflight BlackBox Log Review Facebook group</a>** for Betaflight specific issues, or **<a href="https://www.facebook.com/groups/INAVOfficial/?ref=bookmarks" target="blank">INAV official Facebook group</a>** for INAV specific issues.

* If you have Matlab and all the required toolboxes you can simply download the source code (download from the zip file on the **<a href="https://github.com/bw1129/PIDtoolbox/releases" target="blank">releases</a>** page for the most up to date and platform-specific source code), and run from the command window. 



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
