# :fire: _openv_
Im [OpenV Wiki](https://github.com/openv/openv/wiki) finden sich Baupläne, Beschreibungen, Software, Informationen und Projekte rund um Viessmann Heizungssteuerungen.

Die [Issues](https://github.com/openv/openv/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc) können ähnlich einem [Diskussionsforum](https://github.com/openv/openv/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc) genutzt werden.

### en

The [OpenV Wiki](https://github.com/openv/openv/wiki) is about DIY projects, software, and information concerning Viessmann® heating controllers.

The [Issues](https://github.com/openv/openv/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc) are to be used like a [bulletin board / forum](https://github.com/openv/openv/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc) in this Github repo.


# :fire: Viessdata 2.1 und 2.2

Die neuen Versionen des schon älteren Tools für Viessmann Heizungen mit OptoLink und KW oder 300 Protokoll. [Check it out!]( https://github.com/philippoo66/ViessData21/wiki/ViessData-2.1)

- Viessdata 2.1: voll kompatibel zu V2.06, mit der Möglichkeit, Listenwerte einzeln zu lesen und auch zu schreiben(!!) und etwas überarbeitet.

  Update: bei der 2.1.0.7 AppOnly ist jetzt auch das fehlende Icon File mit drin - sie läuft jetzt auch ;-)

- Viessdata 2.2: die hart-programmierten Werte-Konvertierungen sind (abgesehen von Zeit/Datum und Heiz/etc/zeiten) raus => die vito_DP.xml ist jetzt besser zu utilisieren, die alte ist aber diesbezüglich bei einigen wenigen DPs nicht mehr kompatibel. 

  Der Umrechnungsfaktor wird jetzt durchgehend als Multiplikator angewandt, hat dieser ein vorangestelltes Minus-Zeichen, so werden die hex Werte signed interpretiert.
