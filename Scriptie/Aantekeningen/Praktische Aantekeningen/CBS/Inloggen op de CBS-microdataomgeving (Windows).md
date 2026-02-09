---
MOC:
  - "[[$Scriptie]]"
tags:
  - clippings
  - note
source: https://www.cbs.nl/nl-nl/onze-diensten/maatwerk-en-microdata/microdata-zelf-onderzoek-doen/inloggen-op-cbs-microdata-omgeving/inloggen-op-de-cbs-microdataomgeving--windows--
published:
created: 2025-10-01
description: Toelichting Inloggen op de beveiligde Microdata-omgeving Windows
about:
  - stappenplan om in te loggen in CBS omgeving
---
Deze instructie biedt uitleg voor het opzetten van een veilige verbinding naar de CBS-microdataomgeving op een Windows-systeem, met behulp van een VPN en RSA-tokens voor authenticatie. Er is een aparte instructie “ [Inloggen op de CBS-microdataomgeving (macOS](https://www.cbs.nl/nl-nl/onze-diensten/maatwerk-en-microdata/microdata-zelf-onderzoek-doen/inloggen-op-cbs-microdata-omgeving/inloggen-op-de-cbs-microdataomgeving--macos--))”.

## Voorbereiding en Systeemeisen

Zorg ervoor dat jouw werkplek voldoet aan de volgende eisen voordat je begint met het opzetten van een sessie in de CBS-microdataomgeving:

1\. VPN Client:  
De door CBS verstrekte VPN-client moet op jouw werkplek zijn geïnstalleerd. Mocht dit niet het geval zijn, installeer de [VPN-client](https://www.cbs.nl/nl-nl/onze-diensten/maatwerk-en-microdata/microdata-zelf-onderzoek-doen/inloggen-op-cbs-microdata-omgeving/installatie-van-fortivpn-client--windows--).

2\. Omnissa Horizon Client:  
[Installeer de meest recente versie van de Omnissa Horizon-client](https://customerconnect.omnissa.com/downloads/info/slug/desktop_end_user_computing/omnissa_horizon_clients/8)  
Selecteer bij "Select Version" de laatste beschikbare versie en volg de instructies om de client te downloaden en te installeren.

3\. Systeemeisen:

- Het systeem dat wordt gebruikt voor toegang tot de CBS-microdataomgeving moet voldoen aan de T-1 richtlijnen van CBS.
- We hanteren bij het CBS een T-1 beleid, wat inhoud dat de Horizon Client en het OS moet voldoen aan specifieke eisen. Meer informatie hierover vind je op de informatiepagina.

4\. Benodigde Internetconnectiviteit:

- PSEC en IKE (UDP op poort 500)
- FW1\_scv\_keep\_alive (UDP poort 18233)
- HTTPS (TCP 443

## Opzetten VPN verbinding in FortiVPN client

Voordat je toegang kunt krijgen tot de CBS-microdataomgeving, moet je eerst een VPN-verbinding met CBS opzetten. Volg de onderstaande stappen:

1\. Open de FortiVPN-client op jouw laptop of desktop.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-mac-os/afbeelding01.jpg?h=362&w=400&hash=33562EC4F11CFDEF51F1FB0DEEC98F34)

2\. Indien je in het bezit bent van een RSA hardware token, vul het volgende in:

- Username: (pmse)  jouw 4-letterige gebruikersnaam (zonder @remoteaccess.cbs.nl)
- Password: (1611 in Authenticator app)   jouw PIN code + RSA tokencode (zonder het plusteken).

3\. Indien je in het bezit bent van een RSA software token:

1\. Start de RSA-applicatie op jouw mobiele apparaat.  
2\. In de FortiVPN-client, vul bij Username jouw 4-letterige gebruikersnaam in.  
3\. Vul jouw persoonlijke PIN in de RSA-app in en druk op Submit.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-mac-os/afbeelding02.png?h=252&w=529&hash=1458717DEBBEDFA3361C6B319B3A0EE1)

4\. Vul de gegenereerde 8-cijferige tokencode in bij Password in FortiVPN client en klik op Connect.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-mac-os/afbeelding03.png?h=133&w=353&hash=9E012E4C00CF2CEBA41B99066713ADE0)

### Belangrijk om te weten als je een software token gebruikt:

4\. Het volgende scherm verschijnt wanneer de VPN-verbinding met het CBS succesvol is opgezet.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-mac-os/afbeelding04.png)

Zodra de verbinding tot stand is gebracht, worden alle internet- en netwerkverbindingen geblokkeerd, behalve de toegang tot de CBS-microdataomgeving. Andere netwerklocaties zijn dan niet meer benaderbaar.

Alleen de CBS-microdataomgevingen zijn toegankelijk. Alle andere internet- en netwerkadressen blijven onbereikbaar totdat de VPN-verbinding wordt beëindigd.

## Configuratie van de Omnissa Horizon Client en verbinding met de CBS-microdataomgeving

De initiële configuratie van de Omnissa-client is een essentiële stap bij het voor de eerste keer gebruiken ervan. Volg onderstaande stappen om dit te voltooien:  
  
1\. Zet de VPN-verbinding op. Zorg ervoor dat de VPN-verbinding met de FortiVPN-client is opgezet voordat je verder gaat.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-mac-os/afbeelding05.png)

2\. Open de Omnissa Horizon ClientAls je de Omnissa Horizon Client nog niet hebt geïnstalleerd, volg dan de installatie-instructies.

3\. Server toevoegenKlik op Add Server, voer microdata1.cbs.nl in en klik vervolgens op Connect.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-windows/afbeelding06.png)

4\. Voer jouw CBS-microdata account en Project PIN code in. In het volgende scherm wordt gevraagd om jouw CBS-microdata account en de 4-cijferige Project PIN code. Bijvoorbeeld, als jouw CBS-microdata account gst1234test is, dan is de Project PIN code 1234. Klik daarna op Login.

==Zie wachtwoordenkluis==

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-windows/afbeelding07.png)

5\. SMS-verificatie. Je ontvangt een SMS met een 8-cijferige verificatiecode. Voer deze code in het volgende scherm in en klik op Login.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-windows/afbeelding08.png)

6\. Voer jouw wachtwoord in. In het volgende scherm wordt gevraagd om het wachtwoord van jouw CBS-microdata account. Vul het wachtwoord in en klik op Login.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-windows/afbeelding09.png)

7\. Start een desktopsessie. Je bent nu ingelogd in de CBS-microdataomgeving. Om een desktopsessie te starten, dubbelklik op de gewenste omgeving. Voor applicaties zoals MATLAB en SAS moet een aparte applicatiesessie worden gestart.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-windows/afbeelding10.jpg?h=207&w=341&hash=CEDE7A27099BE421A49A0A7D19F264DF)

8\. Applicaties gereed voor gebruik. Na het inloggen verschijnt er een venster dat aftelt. Zodra dit venster verdwijnt, zijn de applicaties klaar voor gebruik.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-mac-os/afbeelding11.png?h=207&w=510&hash=A962A263FC5A3EB6D150EC951F750CD5)

## Nuttige informatie

### CTRL + ALT + DEL

Als de sessie is vergrendeld en er op het scherm staat dat je CTRL + ALT + DEL moet indrukken, gebruik dan niet de toetsen op jouw toetsenbord.

- Als je op een Windows-computer werkt, klik je op de CTRL + ALT + DEL knop in de grijze bovenbalk van de Omnissa Horizon Client om de sessie te ontgrendelen.
- Als je op een MacOS werkt, klik je in de bovenbalk op Connection > Send Ctrl-Alt-Del om de sessie te ontgrendelen.
![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-windows/afbeelding12.jpg?h=207&w=341&hash=59A3A1AFB38AA4A467A17DD4EA05CEF9)

### Snelkoppelingen aanmaken

Je kunt snelkoppelingen naar applicaties op jouw bureaublad maken als alternatief voor de favorietenlijst in de tegelinterface. Volg deze stappen:

1. Open het Startmenu door op de Startknop linksonder in beeld te klikken.
2. Klik vervolgens op "Alle apps" om een lijst met beschikbare applicaties te openen.
3. Sleep de gewenste applicaties vanuit deze lijst naar jouw bureaublad om een snelkoppeling aan te maken.

### Verbinding verbreken

Als je nog scripts of verwerkingen hebt die door moeten gaan, kan je de verbinding verbreken zonder de sessie af te sluiten. Klik op het kruisje in de bovenbalk van het scherm om de verbinding te verbreken.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-mac-os/afbeelding13.jpg?h=207&w=341&hash=65FD7423309BCCFB4FE34A754CD5CB05)  
  

### Verbinding verbreken

Wanneer je klaar bent met jouw werk en alles is opgeslagen, wordt aanbevolen om jouw sessie af te melden om de omgeving stabiel te houden. Je kunt dit doen via het Startmenu. Klik op het grijze rondje met het poppetje erin, klik op de drie puntjes, en kies vervolgens voor Afmelden.

![](https://www.cbs.nl/-/media/cbs/onze-diensten/maatwerk/zelf-onderzoek-doen/inloggen-ra-omgeving-windows/afbeelding14.png)