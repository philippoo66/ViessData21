
Identifikation der zum Gerät gehörenden Datenpunktliste
=======================================================

Zuerst wird die Gerätekennung an der Adresse 0xF8 / 0x00F8 ausgelesen. Die 8 Bytes haben die folgende Struktur:

GRUPPENIDENTIFIKATION   0xF8    sysDeviceGroupIdent
REGLERIDENTIFIKATION    0xF9    sysDeviceIdent
HARDWAREINDEX           0xFA    sysHardwareIndexIdent
SOFTWAREINDEX           0xFB    sysSoftwareIndexIdent
VERSION_LDA             0xFC    sysProtokollversionLDAIdent
VERSION_RDA             0xFD    sysProtokollversionRDAIdent
VERSION_SW1             0xFE    sysHighByteDeveloperVersionIdent
VERSION_SW2             0xFF    sysLowByteDeveloperVersionIdent

Gegebenefalls wird noch das ecnsysDeviceIdentF0, 1 Byte an Adresse 0xF0 / 0x00F0 benötigt.

Damit schaut man dann in die Datapoints Liste. Bei einigen Geräten reichen die ersten beiden Bytes an F8, beispielsweise 

  ecnsysDeviceIdent:2048 : V200WO1A

Bei anderen Geräten werden noch zwei weitere Bytes benötigt:

  ecnsysDeviceIdent:2098 sysHardware/SoftwareIndexIdent:0100-0103 : V200KW2
  ecnsysDeviceIdent:2098 sysHardware/SoftwareIndexIdent:0104-0104 : V200KW2_4
  ecnsysDeviceIdent:2098 sysHardware/SoftwareIndexIdent:0105-0105 : V200KW2_5
  ecnsysDeviceIdent:2098 sysHardware/SoftwareIndexIdent:0106-010F : V200KW2_6

Bei einer dritten Gruppe wird auch noch das Byte an F0 benötigt:

  ecnsysDeviceIdent:20CB sysHardware/SoftwareIndexIdent:01C8-01FF ecnsysDeviceIdentF0:0-0 : VScotHO1_200
  ecnsysDeviceIdent:20CB sysHardware/SoftwareIndexIdent:01C8-01FF ecnsysDeviceIdentF0:1-9 : VScotHO1_200_01
  ecnsysDeviceIdent:20CB sysHardware/SoftwareIndexIdent:01C8-01FF ecnsysDeviceIdentF0:10-10 : VScotHO1_200_10
  ecnsysDeviceIdent:20CB sysHardware/SoftwareIndexIdent:01C8-01FF ecnsysDeviceIdentF0:11-19 : VScotHO1_200_11

Aber ACHTUNG! Manchmal ist der sysHardwareIndexIdent '01' nur ein "Platzhalter" und kann als "einer für alle" aufgefasst werden. 

Beispiel: Bei meiner Vitodens B3HB steht an F8: 20 CB 1F C9 00 00 01 14, an F0: 01

sysHardware/SoftwareIndexIdent 1F C9 ist aber nirgends zu finden. Tatsächlich ist der HardwareIndex hier irrelevant. Es handelt sich um eine VScotHO1_200_01, Klartext "ab Softwareindex 200, Projekt Vitodens 300 mit HO2B, ab 08/2016 mit Lüftungsbedienung". Das 'ab Softwareindex 200' findet sich mutmasslich im SoftwareIndexIdent 0xC9 = 201.

Relevant für die Identifikation der zugehörigen Datenpunktliste im DP_Listen.zip ist die Kennung hinter dem rechten Doppelpunkt, im Beispiel also das 'VScotHO1_200_01'. Die zugehörige Datenpunktliste ist DP_VScotHO1_200_01.txt
