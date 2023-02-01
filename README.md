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

  Der Umrechnungsfaktor wird jetzt durchgehend als Multiplikator angewandt, hat dieser ein vorangestelltes Minus-Zeichen, so werden die hex Werte signed interpretiert.

- Viessdata 2.3: Zeiten-Geschichte überarbeitet. Einzelne Tage schreiben und Werte auf andere Tage übertragen eingebaut. Knopf zur WW Einmalladung eingebaut. Schreiben großer Werte (bis zu 8 Bytes, auch unsigned), Block-segmented Lesen auch mit Offset. Anzeige Strings in Liste. Fehler in xml gehandled. Mehr siehe Verstion.txt. 

  Einige DPs in vito_DP.xml ergänzt (auch welche, die nicht in der Vitosoft DB stehen). DPs ein wenig in Gruppen angeordnet. 

  Achtung: Heiz/etc/zeiten jetzt als ein 56-Byte Wert ODER 7 sub-sequent Tage je 8 Bytes in der Liste erwartet. Am besten die vito_DP.xml übernehmen. Aber vor Starten des neuen Programms die bestehende aktuelle Wochen-csv umbenennen, damit eine neue erstellt wird! Sonst gibt es Chaos wegen der tw. umgeordneten Reihenfolge der gespeicherten DPs.
  
## DP_Listen_2.zip
weiter DP Listen ergänzt. Die, bei denen das Python Skript offensichtlich nicht richtig funktioniert hat, habe ich als csv Kopie der SQL Abfrage beigefügt. Nicht ganz so schön wie die txt Files, aber zumindest sind die Address-Infos drin. 

Die Listen, die aus der Vitosoft SQL DB / xml stammen, sind übrigens nicht unbedingt vollständig. Bei meiner 'VScotHO1_200_01' tauchen die Wandlerwerte an 0800h ff nicht auf, aber sie existieren. Wenn ich die DPs mit denen aus einer KW3 kombiniere, sind die ADC DPs dabei. Und es fehlen bsw. eine Menge Einstellungen an 0x77yz (Betriebsweise/Regelung der internen Umwälzpumpe, LON Parameter, Anlagentyp, Haustyp, allgem. Einstellungen, ...), wobei yz die Parameternummer aus der Serviceanleitung sind. Es scheint Sinn zu machen, anhand der Parameternummern im Serv.HB und der DP Adressen/Adressbereiche mal weiter zu schauen, wo man noch was findet. 

Wer zusätzliche Infos braucht (z.B. Enums der Enum-Typ Parameter), und nicht das Vitosoft Monster installieren will, kann sich gerne melden.
  
