# :fire: _openv_
Im [OpenV Wiki](https://github.com/openv/openv/wiki) finden sich Baupläne, Beschreibungen, Software, Informationen und Projekte rund um Viessmann Heizungssteuerungen.

Die [Issues](https://github.com/openv/openv/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc) können ähnlich einem [Diskussionsforum](https://github.com/openv/openv/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc) genutzt werden.

### en

The [OpenV Wiki](https://github.com/openv/openv/wiki) is about DIY projects, software, and information concerning Viessmann® heating controllers.

The [Issues](https://github.com/openv/openv/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc) are to be used like a [bulletin board / forum](https://github.com/openv/openv/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc) in this Github repo.


# :fire: Viessdata 2.1, 2.2 und 2.3
  
[Kontakt / Contact the author](https://github.com/philippoo66/ViessData21/discussions/1)
  
Die neuen Versionen des schon älteren Tools für Viessmann Heizungen mit OptoLink und KW oder 300 Protokoll. [Hier mehr lesen]( https://github.com/philippoo66/ViessData21/wiki/ViessData-2.1)

- Viessdata 2.1: voll kompatibel zu V2.06, mit der Möglichkeit, Listenwerte einzeln zu lesen und auch zu schreiben(!!) und etwas überarbeitet.

  Update: bei der 2.1.0.7 AppOnly ist jetzt auch das fehlende Icon File mit drin - sie läuft jetzt auch ;-)

- Viessdata 2.2: die hart-programmierten Werte-Konvertierungen sind (abgesehen von Zeit/Datum und Heiz/etc/zeiten) raus => die vito_DP.xml ist jetzt besser zu utilisieren, die alte ist aber diesbezüglich bei einigen wenigen DPs nicht mehr kompatibel. 

  Der Umrechnungsfaktor wird jetzt durchgehend als Multiplikator angewandt. Hat dieser ein vorangestelltes Minus-Zeichen, so werden die hex Werte signed interpretiert.

- Viessdata 2.3: Zeiten-Geschichte überarbeitet. Einzelne Tage schreiben und Werte auf andere Tage übertragen eingebaut. Knopf zur WW Einmalladung eingebaut. Schreiben großer Werte (bis zu 8 Bytes, auch unsigned), Block-segmented Lesen auch mit Offset. Anzeige Strings in Liste. Fehler in xml gehandled. Mehr siehe Version.txt. 

  Einige DPs in vito_DP.xml ergänzt (auch welche, die nicht in der Vitosoft DB stehen). DPs ein wenig in Gruppen angeordnet. 

  Achtung: Heiz/etc/zeiten jetzt als ein 56-Byte Wert ODER 7 sub-sequent Tage je 8 Bytes in der Liste erwartet. Am besten die vito_DP.xml übernehmen. Aber vor Starten des neuen Programms die bestehende aktuelle Wochen-csv umbenennen, damit eine neue erstellt wird! Sonst gibt es Chaos wegen der tw. umgeordneten Reihenfolge der gespeicherten DPs.
  
  Seit Version 2.3.2.0 sollte auch das KW Protokoll 'arbeiten' (danke @traori für sein Mitwirken!).
  
# :new: Viessdata 2.4
Die Version 2.4 kann jetzt TCP/IP, d.h. ihr könnt einen kleinen Raspi im Keller an die Heizung oder WP hängen und das Ding macht still und stromsparend vor sich hin. Dann könnt ihr Viessdata bei Bedarf auf einem Rechner im W/LAN starten und die aktuellen Werte über's Netz lesen und schreiben. Die Log csv's für die Grafik bei Bedarf über FTP vom Raspi holen und in Viessdata öffnen.

Grundlage dafür ist der [Optolink-Switch](https://github.com/philippoo66/optolink-splitter), der noch viel mehr kann...

![grafik](https://github.com/philippoo66/ViessData21/assets/122479122/94129601-6916-4446-9a24-a45cd7a4e7a5)


## DP_Listen_2.zip
weiter DP Listen ergänzt. Die, bei denen das Python Skript offensichtlich nicht richtig funktioniert hat, habe ich als csv Kopie der SQL Abfrage beigefügt. Nicht ganz so schön wie die txt Files, aber zumindest sind die Address-Infos drin. 

![grafik](https://user-images.githubusercontent.com/122479122/235306088-cc4b642f-67df-4142-94f1-6e22368e9fac.png)

Die Listen, die aus der Vitosoft SQL DB / xml stammen, sind übrigens nicht unbedingt vollständig. Bei meiner 'VScotHO1_200_01' tauchen die Wandlerwerte an 0800h ff nicht auf, aber sie existieren. Wenn ich die DPs mit denen aus einer KW3 kombiniere, sind die ADC DPs dabei. Aber es fehlen bsw. noch eine Menge Einstellungen an 0x77yz (Betriebsweise/Regelung der internen Umwälzpumpe, LON Parameter, Anlagentyp, Haustyp, allgem. Einstellungen, ...), wobei yz die Parameternummer aus der Serviceanleitung sind. Es scheint Sinn zu machen, anhand der Parameternummern im Serv.HB und der DP Adressen/Adressbereiche mal weiter zu schauen, wo man noch was findet. 

Wer zusätzliche Infos braucht (z.B. Enums der Enum-Typ Parameter), und nicht das Vitosoft Monster installieren will, kann sich gerne melden.
  
## DataPoints_ReadMe

<b>Identifikation der zum Gerät gehörenden Datenpunktliste</b>

Zuerst wird die Gerätekennung an der Adresse 0xF8 / 0x00F8 ausgelesen. Die 8 Bytes haben die folgende Struktur:

![grafik](https://user-images.githubusercontent.com/122479122/235326784-79c9e46b-fda9-4a53-b95e-04c68af3c47e.png)

Gegebenefalls wird noch das ecnsysDeviceIdentF0, 1 Byte an Adresse 0xF0 / 0x00F0 benötigt.

Damit schaut man dann in die [DataPoints Liste](https://github.com/philippoo66/ViessData21/blob/master/DataPoints.txt). Bei einigen Geräten reichen die ersten beiden Bytes an F8, beispielsweise 

![grafik](https://user-images.githubusercontent.com/122479122/235326869-1710f9ce-dddb-42ec-ad36-c7da25bc8152.png)

Bei anderen Geräten werden noch zwei weitere Bytes benötigt:

![grafik](https://user-images.githubusercontent.com/122479122/235326887-1ef0d12a-aeca-4fea-9ba3-07a54d06d455.png)

Bei einer dritten Gruppe wird auch noch das Byte an F0 benötigt:

![grafik](https://user-images.githubusercontent.com/122479122/235326911-a20628f6-0313-4b93-80f5-0d81aca00369.png)

Aber ACHTUNG! Manchmal ist der sysHardwareIndexIdent '01' nur ein "Platzhalter" und kann als "einer für alle" aufgefasst werden. 

Beispiel: Bei meiner Vitodens B3HB steht an F8: 20 CB 1F C9 00 00 01 14, an F0: 01

sysHardware/SoftwareIndexIdent 1F C9 ist aber nirgends zu finden. Tatsächlich ist der HardwareIndex hier irrelevant. Es handelt sich um eine VScotHO1_200_01, Klartext "ab Softwareindex 200, Projekt Vitodens 300 mit HO2B, ab 08/2016 mit Lüftungsbedienung". Das 'ab Softwareindex 200' findet sich mutmasslich im SoftwareIndexIdent 0xC9 = 201.

Relevant für die Identifikation der zugehörigen Datenpunktliste im [DP_Listen_2.zip](https://github.com/philippoo66/ViessData21/blob/master/DP_Listen_2.zip) ist die Kennung hinter dem rechten Doppelpunkt, im Beispiel also das 'VScotHO1_200_01'. Die zugehörige Datenpunktliste ist DP_VScotHO1_200_01.txt

