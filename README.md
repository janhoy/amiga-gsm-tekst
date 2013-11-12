# GSM-tekst
Jeg legger for moro skyld ut et program jeg skrev i min [Amiga](http://en.wikipedia.org/wiki/Amiga)-periode. Dette er et [Arexx
script](http://en.wikipedia.org/wiki/ARexx) som kan kjøre i [NComm kommunikasjonsprogram](http://en.wikipedia.org/wiki/NComm). Have fun :)

Programmet var shareware på 90-tallet. Legger det ut under Apache-lisensen her!

------------------------------------------------------------------------

     ####    ####  ##   ##           ##             ##               ##
    ##  ##  ##  ## ### ###           ##             ##               ##
    ##      ###    #######          #####    ####   ##  ##   ####   #####
    ## ###   ####  ## # ##  ######   ##     ##  ##  ## ##   ##       ##
    ##  ##     ### ##   ##           ##     ######  ####     ####    ##
    ##  ##  ##  ## ##   ##           ##     ##      ## ##       ##   ##
     #####   ####  ##   ##            ###    ####   ##  ##  #####     ###

                                  v2.3
                               1997-07-01

                             av Jan Høydahl

------------------------------------------------------------------------

#INNLEDNING

GSM-tekst er et ARexx-script som bruker NComm (av Torkel Lodberg) for å
sende GSM-tekst-meldinger til personer med Telenor mobil GSM-abonnement.

Det er svært enkelt i bruk, og bør være enkelt å endre på selv etter
eget ønske også. Dette er en liten oppgradering fra v2.2. Nytt denne gang er:

* Ny forenklet modus. Slipper å svare på alle spørsmålene hvis man ikke
  vil. Dersom telefonnummer er definert i "Username" i NComm, brukes det
  automatisk som avsender og kvitteringsadresse.
* Lagt inn støtte for Telenors begrensning på at ikke mer enn to meldinger kan 
  sendes samtidig. Også advarsel om at tekst vil bli kuttet.
* Lagt inn på min hjemmeside http://members.tripod.com/~inventor/
* Nytt telefonnummer til Telenors modem. Dokumentasjon endret.

Testet og funker bra på min Amiga 500!


#BAKGRUNN

Da jeg nettopp selv har kjøpt meg GSM-telefon ville jeg benytte meg av
muligheten for å sende tekst-meldinger til denne. De meldingene som
tilbys av Telenor mobil på telefonnummer 9000 2100 er begrenset til å
legge inn et telefonnummer eller en av få standardmeldinger, så vi med
datamaskin og modem tilbys litt bedre support.


#INSTALLERING

Ingenting gjøres automatisk for deg her :-) Du må selv finne et sted å
legge  scriptet  samt et sted å putte telefonlista (en samling filer som
har samme navn som mottaker og som inneholder dennes GSM-nummer) og
meldingene. Hvor disse katalogene befinner seg må du sette opp ved å
redigere selve scriptet.

##Default er disse områdene satt opp:

Scriptet:       NComm:GSM-tekst/
Dokumentasjon:  NComm:GSM-tekst/
Meldinger:      NComm:GSM-tekst/Meldinger/
Mottakere:      NComm:GSM-tekst/Mottakere/

Det vil si at hvis du bruker samme struktur så trenger du ikke å endre
noe i scriptet. Jeg forutsetter i resten av dokumentasjonen at dene
strukturen brukes.

Lag så et entry i telefonboken til NComm hvor du skriver inn nummeret
9000 2199, og velg NO7 som tegnsett. **Nytt** i denne versjonen er at du i
tillegg kan fylle ut feltet "Username" med ditt eget GSM telefonnummer.
Dette vil da sendes som "Avsenderadresse" og vises først i meldingen som
sendes, slik at mottaker automatisk kan ringe deg ved et tastetrykk.
Det navnet du gir entryet i telefonboka må også defineres helt i starten
av GSM-tekst scriptet.  Default her er "GSM-tekst".  Dette entryet
brukes for å ringe opp.  På den måten vil du også dette telefonforbruket
komme skikkelig frem i NComm.log loggfilen.  Pr.  dags dato er det
vanlig telefontakst å ringe denne tjenesten.  Dette kan endres siden.

En annen variabel som kan endres i starten av scriptet er hvilken editor
du bruker. Default er "ed -sticky" som er CED sin activator. Jeg
oppdaget et problem med CED, nemlig at -sticky (-s) funksjonen ikke
fungerer hvis CED ikke allerede er i minnet. For å rette på dette har
jeg laget en ny variabel i starten av scriptet som heter "Starteditor".
Den fyrer opp CED resident først. Hvis du ikke bruker CED, settes denne
variabelen til "".

Selvsagt må du også sørge for at RexxMast er aktiv. Dette programmet
følger med AmigaDOS og skal ligge i SYS:System/ skuffen.


#OPPSTART

Du starter først opp NComm. Så startes scriptet ved å skrive følgende i
et Shell-vindu:

rx NComm:GSM-tekst/GSM-tekst

Du kan også skrive følgende i en makrotast-definisjon i NComm (Velg
System/Macrokeys i menyen):

{arexx}NComm:GSM-tekst/GSM-tekst

Du vil da kunne trykke på denne tasten for å starte GSM-tekst.

Siste opsjon er å bruke medfølgende script med ikon for IconX. Du må
selv redigere scriptet (GSM-tekst.bat) slik at det peker til rett sted
for ARexx-scriptet. Jeg har brukt "leave out" for å få ikonet (som er et
bilde av en mobiltelefon) ut på WB. Scriptet starter NComm!


#BRUK

Følg bare instruksene som gis i dialogboksene på skjermen. Velg først
forenklet/avansert modus. Ved forenklet modus får du nesten ingen
spørsmål, men alle default-verdiene brukes. I avansert modus er det som
før at du blir spurt om det meste.

For å definere nye personer i telefonlista bare skriver du dennes navn i
filrequesteren. Deretter blir du spurt om telefonnummer. Neste gang du
bruker GSM-tekst vil du finne navnet oppført i listen.

De andre alternativene er som følger:

Kvitteringstype: Ved sending av tekstmelding kan man få en kvittering på
                 om meldingen kom frem eller hva som har skjedd. På
                 dette valget kan du velge hva som skal meldes fra om.
                 Default 7=Alle typer.

Kvitteringsadr:  Jeg har ikke prøvd å få kvittering til annet sted enn
                 min egen GSM-telefon. Her skriver du altså ditt eget
                 GSM-nummer hvis du har det selv.

Type mottaker:   Foreløpig virker det som om kun GSM-tekst mottakere
                 støttes. Andre alternativer kunne jo være PS-tekst
                 eller vanlig dataterminal. Denne trenger derfor strengt
                 tatt ikke å fylles ut. Default: 1=GSM.

Gyldighetstid:   Vanligvis lagres en melding hos Telenor mobil i 72
                 timer før den slettes. Hvis ikke mottakerens telefon
                 står på er dette kjekt. Maks kan du be om 168 timers
                 lagring. Det kan jo også være aktuelt med kortere enn
                 72 timer dersom saken gjelder noe som er uaktuelt hvis
                 det leses for sent. Trenger som regel ikke fylles ut.

Senere levering: Hvis meldingen først ønskes levert om noen timer, dager
                 eller kanskje måneder, kan dette stilles inn her.
                 Telenor mobil vil da passe på å sende meldingen til
                 korrekt tid. Dette kan jo f.eks. brukes for å minne seg
                 selv på ting som er langt frem i tid. Formatet er slik:
                 Eks: 17. mai kl 12:30 blir "05:17:12:30".

Etter at ønsket informasjon er fylt inn blir du sendt til editoren.
Skriv meldingen rett frem. Norske tegn og de fleste spesialtegn går helt
bra. En GSM-tekst-melding er max 160 tegn, men dette scriptet støtter
å sende budskapet over to meldinger, så bare føl deg fri. Dersom du
definerer ditt telefonnummer i phonebook-oppføringen til GSM-tekst i NComm
under User name, vil dette bli brukt som avsenderadresse (kommer frem
host mottaker).

Så lagrer du og avslutter editoren. Da blir du ført tilbake til NComm.
Dersom du skriver mer enn 160 tegn, vil GSM-tekst nå spørre deg om du
ønsker å sende meldingen i "flere omganger", dvs at mottaker får to
GSM-tekst-meldinger rett etter hverandre slik at det ser ut som de
henger sammen.. (Funker helt fint og er veldig praktisk!). Tar ikke noe
særlig lenger tid heller. GSM-tekst passer da på at hver del-melding
slutter MELLOM to ord, og ikke midt i :-) Begrensning: 2 meldinger av
gangen.

Så spørres det om du vil sende meldingen. Svar ja og len deg tilbake.


BUGS

Skyldes i såfall et teit interface som Telenor har valgt for sin "BBS"
:-)


#COPYRIGHT ETC

GSM-tekst er FREEWARE - helt gratis, gjør som du vil med det! Eneste
betingelse for å bruke programmet er at du sender *en* GSM-tekst-melding
til meg på 901 25 809 hvor du forteller kort hva du synes om prg. :)

Forfatteren av dette programmet tar intet ansvar for noe som helst som
måtte inntreffe under bruken av programmet. Blir ikke forbindelsen
koblet ned og du får en stor telefonregning så er ikke det min feil. Du
bruker programmet på eget ansvar. Det samme gjelder om meldinger blir
sendt med feil innhold eller til feil mottaker eller til feil tid osv.

Du skjønner sikkert hva jeg vil frem til.. :-)


TILBAKEMELDING

http://members.tripod.com/~inventor/
jan@engineer.com

Lykke til.