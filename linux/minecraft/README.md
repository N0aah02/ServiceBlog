In diesem Blog Artikel möchte ich Dir zeigen, wie du Minecraft auf Debian 9/10/11 ändern kannst.

Zuerst verbinden wir uns per SSH auf unseren Server mit z.B. Putty.

Nun führen wir folgenden Befehl aus:

Server Updaten:
root@testserver ~ # apt update & apt upgrade -y
Nun prüfen wir ob Java installiert ist:
root@testserver ~ # java -version
java version "1.8.*_***"
Java(TM) SE Runtime Environment (build 1.8.*_**-***)
Java HotSpot(TM) 64-Bit Server VM (build **.**-**, mixed mode)
Minecraft Benutzer anlegen:
root@testserver ~ # adduser --disabled-login minecraft
Die Angaben wie Name, Telefonnummer, E-Mail.. können überprungen werden.
Anmeldung in den neuen Benutzer:
root@testserver ~ # su - minecraft
Das Homeverzeichnis des Benutzers ist im /home/minecraft zu finden.
Gewünschte Version herunterladen:
Spigot 1.8.8:
root@testserver ~ # wget https://cdn.getbukkit.org/spigot/spigot-1.8.8-R0.1-SNAPSHOT-latest.jar
Spigot 1.16.4:
root@testserver ~ # wget https://cdn.getbukkit.org/spigot/spigot-1.16.4.jar
Craftbukkit 1.8.8:
root@testserver ~ # wget https://cdn.getbukkit.org/craftbukkit/craftbukkit-1.8.8-R0.1-SNAPSHOT-latest.jar
Craftbukkit 1.16.4:
root@testserver ~ # wget https://cdn.getbukkit.org/craftbukkit/craftbukkit-1.16.4.jar
Weitere Versionen:
https://getbukkit.org/download/spigot
https://getbukkit.org/download/craftbukkit
Startdatei anlegen:
root@testserver ~ # nano start.sh
Nun geben wir folgendes in das Fenster ein:
screen -AmdS minecraft java -Xms1024M -Xmx1024M -jar spigot-1.8.8-R0.1-SNAPSHOT-latest.jar
Mit -Xms und -Xmx kannst du die gewünschte Arbeitsspeichermenge angeben.
Zudem muss der Name der Datei(spigot-1.8.8-R0.1-SNAPSHOT-latest.jar) korrekt angegeben werden.
Anschließend müssen wir mit STRG + X und anschließend mit der Y-Taste speichern.
Rechte vergeben:
root@testserver ~ # chmod +x start.sh
Lizenzbedingungen(EULA) akzeptieren:
root@testserver ~ # echo "eula = true" > eula.txt
Startdatei starten:
root@testserver ~ # ./start.sh
Konsole öffnen:
root@testserver ~ # screen -r minecraft
