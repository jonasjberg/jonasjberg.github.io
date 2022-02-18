---
layout: post
title:  "autonameow Post-Mortem"
date:   2017-06-18 21:54:48
tags:   [autonameow, projects, development, workflow, python, pim]
disqus: true
image: "" 
---

This post follows up on the previous `autonameow` project introduction.
A "Post-Mortem" was required as part of the final project delivery.
This post contains the final post-mortem for `autonameow` version `v0.4.0`,
which marked the end of of the course work.

__Note that this post describes `autonameow` version `v0.4.0` and does
not reflect the current state of the project.__

*(Also note that the Post-Mortem is written in Swedish ..)*


--------------------------------------------------------------------------------


Post-Mortem
===========
Slutrapport för det individuella mjukvaruutvecklingsprojektet i kursen `1dv430`.


##### Datum
2017-06-06   

##### Författare
Jonas Sjöberg (`js224eh@student.lnu.se`)



Abstrakt
--------
> Den här rapporten beskriver projektarbetets arbetsprocess, utmärkande
> problem, lösningar och generella reflektioner kring projektet.
>
> Efter en längre tid av planering och efterforskningar lyckades jag till slut
> nå de uppsatta målen för projektet. Den här rapporten innehåller övergripande
> reflektioner och en utvärdering av projektet.


Inledning och Bakgrund
----------------------
Projektet började som ett privat hobbyprojekt i februari 2016.

Tanken var att jag skulle samla funktionalitet för filhantering i ett verktyg.
Jag har sedan länge använt mig av egna program och script för att sköta diverse
sysslor, bland dessa automatisk namngivning och sortering av filer. Jag tänkte
att `autonameow` skulle utgöra en flexibel minsta gemensam nämnare för den här
typen av verktyg. Beteendet skulle kunna utökas och konfigureras efter behov
och reducera duplicerad kod genom att samla gemensam kod i ett större program.

Jag insåg från början att automatisk namngivning av filer och analys av
metadata är ett mycket komplext problem. Detta såg jag som en fördel, jag
behövde något utmanande att jobba på för att utvecklas som programmerare.

Jag tänkte också göra projektet tillgängligt för allmänheten på t.ex. GitHub
som del av en slags portfolio och demonstration för potentiella arbetsgivare.

Efter några månader stannade utvecklingen upp till följd av både tidsbrist men
också på grund av att jag fastnade och lyckades inte ta mig vidare. När
programmet hade växt till en viss storlek och komplexitet så krävdes helt
plötsligt mycket mer och jag lyckades inte komma vidare med den befintliga
arkitekturen. Samtidigt hade jag store problem med att komma på något bättre
alternativ. Detta på grund av bristande erfarenhet i mjukvarudesign.

Nu när jag fick tillfälle att välja fritt vad jag ville arbete med så valde jag
att gå tillbaka till `autonameow` och försöka komma vidare.

Problemformulering
------------------
Det övergripande målet för `autonameow` är att förenkla namngivning av filer.

En kan göra ett giltigt argument för att allmänt vedertagna hierarkiska
filsystem i sin natur är illa lämpade för att arkivera information på ett sätt
som möjliggör snabb och enkel åtkomst av människor.  Konventionella filsystem
bygger på en allt finare uppdelning av innehåll, ordnat i en trädstruktur.
Kanske har man en katalog för allmän media, som i sin tur innehåller
underkataloger för olika typer av media; *musik*, *film*, etc.  

Uppdelningen blir många gånger godtycklig. Dessutom är det många gånger inte
uppenbart vart ett föremål ska hamna. Föremålet kan passa lika väl i något
eller båda av parallella trädstrukturer.

En möjlig lösning är att hantera filer genom sökning i metadata, filnamn och
innehåll, likt t.ex. MacOS *Spotlight search* eller motsvarande; `kupfer`,
`launchy`, `synapse`, `recoll`, etc.

Med den här typen av åtkomst blir hierarkisk ordning och filnamn inte lika
avgörande. Men trots detta finns många fördelar med en väl ordnad hierarkisk
ordning och namngivningskonvention.
I kombination med sökverktyg ger det goda möjligheter att filtrera och begränsa
sökresultat. För t.ex. backup-kopiering är det fortfarande viktigt att ordna
data efter filnamn.

Ett annat problem med att förlita sig på metadata för att ordna sina filer är
att metadata-format är dåligt standardiserade och dessutom inte
plattformsagnostiska. Olika verktyg kan påverka metadata på oönskade sätt.

Genom att lagra information i filnamnen garanteras överföring mellan
operativsystem och kompatibilitet med kommande programvaror.

Problemet är att det krävs alltför mycket manuellt arbete eller
specialkunskaper för att göra den typen av namngivning praktisk.

För att lagra information på ett sätt som tillåter snabb och tillförlitlig
åtkomst behöver användaren upprätta något slags system och sedan kontinuerligt
upprätthålla ordningen.

De flesta användare har inte någon särskild struktur eller plan. Många av de
som ändå försökt hålla sig till någon viss strategi saknar tålamod och
disciplin som krävs för att upprätthålla den.
De användare som faktiskt försöker upprätthålla en viss strategi spenderar
mycket tid åt repetitivt arbete som krävs för att namnge och sortera filer.


Kort sagt; __användare behöver ett hjälpmedel för att göra det så pass enkelt
att hålla sig till en viss namngivningskonvention, så att det inte finns någon
anledning att inte göra det.__


Målet med `autonameow` är att reducera den kognitiva och tidsmässiga
investering som förutsätts för att upprätthålla en strikt
namngivningskonvention.

I bästa fall ska det inte krävas mer än en knapptryckning för att automatiskt
namnge filer till ett önskat format.
Tanken är att `autonameow` ska vara "hands-off" och bara göra "rätt sak".


Arbetsprincip för `autonameow`
------------------------------
Användaren startar `autonameow` och specificerar en eller flera filer.

Filerna matchas enskilt mot en uppsättning regler som konfigureras av
användaren.

Varje regel innehåller tre viktiga delar; 

* __Förutsättningar/Krav__ som utvärderas mot filen i fråga.
  Dessa tester avgör hur troligt det är att regeln gäller för just den filen.
  Exempel på krav är t.ex. att ett dokument måste innehålla en viss rad text
  eller ett foto måste vara taget av en viss kameramodell.

* __Namnformat/Mall__ som gäller för filer som matchas mot regeln.
  Mallen innehåller särskilda fält som fylls i av programmet.
  Exempelvis;

	  `{date} {title} -- {author}.txt`

* __Anvisningar för vilken data__ som ska användas för att fylla i mallens
  fält.  Här kan användaren ge anvisningar om hur `autonameow` ska välja ut
  lämpligt data för att fylla i fältet `{title}`, t.ex.


Den regel som *bäst* matchar den aktuella filen används. 
Reglerna viktas och prioriteras på olika vis, detta kan också påverkas av
användaren.


Mjukvaruarkitektur
------------------
Koden är uppdelad i två övergripande delar; `core` och *"annat"* --
`analyzers`, `extractors` och `plugins`.

All kontroll finns i `core`. Härifrån anropas de andra delarna beroende på
filtyp och andra omständigheter.

Tanken är att hålla en strikt separation mellan `core` och resten för att
förenkla vidareutveckling; en begränsad kommunikationskanal mellan de olika
modulerna gör att de påverkar varandra mindre då de modifieras, vilket leder
till mindre arbete.

Olika filtyper, t.ex. dokument, video, foton, etc. hanteras av filtypspecifika
`analyzers`.
Dessa använder sig i sin tur av `extractors` för att extrahera data från olika
filtyper.  Exempelvis nyttjar flera `analyzers` samma `exiftoolextractor` för
att hämta metadata från olika filformat.

Tanken är att `analyzers` ska hantera typer av dokument, både scannade
räkningar och böcker kan vara i PDF-format men ha väldigt lite gemensamt.
Däremot gör `extractors` inte skillnad på typer av PDF-dokument.  Extractors
ska kunna utvinna data ur olika filtyper, men agera på en "lägre nivå".

En stor del av projektet har handlat om att förbättra arkitekturen.  Projektet
har nu tydliga mål men mycket mer arbete krävs för att implementera alla delar.
Vid version `v0.4.0` som redovisas här finns bara en bråkdel av de tänkbara
möjligheterna implementerade.


Arbetsprocessen
---------------
Arbetet har efter instruktioner följt en modern iterativ "agil" arbetsmetod.

Jag hade inledningsvis stora problem att integrera all dokumentation i arbetet.
Alltför mycket tid gick åt att uppdatera parallella textfiler, särskilt i
början när jag inte var van vid de föreslagna namngivningskonventionerna.

Ungefär halvvägs in i projektet så började jag få kläm på dokumentationen, men
den har ändå känts väldigt klumpig. Antagligen behövs ett bättre system. Jag
övervägde att använda GitHub "issues" för min "Product Backlog", men jag valde
ändå att hålla mig till enkla textfiler.

Den arbetsmetod jag själv föredrar är enkla att-göra-listor med nästlade
punkter av "dependencies", vilket är likt kursens föreslagna modell med en
"Product Backlog".

### Automatisering
Jag tyckte att arbetet med dokumentationen tog upp alltför mycket tid, så jag
bestämde mig för att investera tid åt att automatisera alla tester och
framställning av testrapporter.

Jag skrev en uppsättning med bash-script som sköter det jag kallar
"integrationstester", vilket i praktiken har blivit alla tester som inte lämpat
sig att skriva med Pythons `unittest`-bibliotek.

Mitt "ramverk" av bash-script möjliggör testning av precis vad som helst på
system.  Det har varit en stor hjälp under utvecklingen, inte bara för att
kringgå manuellt skrivna testrapporter.

Med ett script körs alla "integrationstester" och alla enhetstester, och
testrapporter i HTML- PDF-format länkas in i wikin.

Dessa script finns under katalogen `tests` i källkoden.

### Vikten av Testning
Då mycket av projektet har handlat om att designa om befintlig kod, så har jag
använt enhetstester flitigt för vissa delar; innan jag gjort en större
förändring har jag sett till att den kod som berörs täcks av tester. Jag har
sedan kunnat göra förändringar utan att vara lika orolig för oväntade negativa
konsekvenser.

Integrationstesterna har också varit till stor hjälp då jag kunnat simulera en
mängd möjliga användarinteraktioner med programmet och jämföra de faktiska
resultaten med förväntade resultat.


Problem och Lösningar
---------------------

### Interna Datastrukturer
Det största problemet har handlat om datastrukturer och hur de ska hanteras
internt. Till det hör också översättningar av externa verktygs representationer
av data till en egen intern representation.  Detta knyter också an till
konfigurationsfilerna och hur en användare förväntas definiera och referera
till data.

Den inledande tiden av projektet läste jag mycket böcker och källkod för
liknande projekt för att få idéer om möjliga lösningar.

Till slut kom jag på en egen lösning som visade sig förenkla eller helt lösa
problemen. Istället för att använda flera olika strukturer och konventioner för
att lagra och referera till data, används en enda referens-struktur. Det är en
tom nästlad "dictionary" som innehåller alla möjliga interna datatyper.
Utformningen av andra datastrukturer skapas sedan dynamiskt från den här
referensen vid körtid. Översättningslager mellan olika delar av programmet kan
också "anpassa" sig genom att derivera sina typer och fält från referensen.

Den här lösningen löste många problem och kom att knyta ihop projektets delar
på ett stiligt sätt.  Alla delar av projektet har ännu inte gått över till att
använda den här metoden, men det är bara en tidsfråga att anpassa den äldre
koden till den nya designen.


### Intern Kommunikation
Ett av målen har vara att hålla en strikt separation mellan projekts olika delar.
Detta för att göra vidareutveckling enklare och minimera verkan av förändringar.

Att skriva särskilda "extractors" för filtyper är mycket krävande och ger
väldigt lite tillbaka, för att tidsinvesteringen ska vara motiverad behövs
viss garanterat kompatibilitet med framtida förändringar.  Man vill alltså
inte att en förändring i programmets kärna ska kräva justeringar i tiotals
filtyps-specifika data-"extractors".

Lösningen på detta var såklart uppenbar när jag väl kom på det; __callbacks__.

Analysis av en fil sköts av en instans av `Analysis`-klassen. Denna fyller en
kö med instanser subklasser av `Analyzer`-klassen.  Dessa körs i sin tur att
får en callback som de använder för att skicka tillbaka resultat till
`Analysis`-instansen.

Den här lösningen i kombination med ovan nämnda interna datastrukturer löste
många problem kring hantering av data, internet i programmet och för hantering
av användare genom konfigurationsfilen.


Positiva Erfarenheter
---------------------
Den mest utmärkande positiva erfarenheten av projektet är ökad tilltro till mig
själv. Jag har verkligen känt att jag utvecklats och blivit en bättre
programmerare. Särskilt då vad jag gäller värdet av namngivning av design.
Jag strävar efter att hålla koden ren och läsbar, går gärna tillbaka för att
uppdatera namngivning och struktur efter att ha gjort förändringar.
Jag har blivit mycket bättre på att skriva komplexa program.

Jag är väldigt nöjd med vad jag åstadkommit under projektets gång. Även om det
inte uppfyller alla krav och jag inte följt det efterfrågade arbetssättet,
känner jag ändå att jag presterat väl och skapat något jag är stolt över.


Negativa Erfarenheter
---------------------
Inledningsvis tyckte jag att den mängd dokumentation som krävdes, i kombination
med alla kod; var orimlig för oerfarna programmerare.
Men jag inser också att jag har mig själv att skylla, då jag tenderar att göra
allt lite för noga. Jag borde kanske ha "slarvat" lite mer och fokuserat på
koden.

I vilket fall så blev dokumentationen allt mindre av ett problem under
projektets gång. Jag känner att jag kanske inte har skött t.ex. min "Product
Backlog" *rätt*, men för att göra det skulle jag inte ha haft någon tid över
till att skriva kod.

Min katt Gibson, som tidigare hjälp mig med projektet (och myntat namnet) har
varit väldigt sjuk. Jag har varit till veterinären jag vet inte hur många
gånger, och spenderat jag vet inte hur många tusen.  Det faktum att min bästa
kompis är sjuk och döende har varit en ständig distraktion och starkt
orosmoment som helt klart har påverkat mig under projekttiden.

Men i vilket fall så lyckades jag till slut ro det i land.


Sammanfattning
--------------
Sammanfattningsvis vill jag säga att jag tycker den här typen av projekt är
extremt värdefulla rent pedagogiskt, jag lär mig bäst genom att lösa roliga
problem.  

Jag hade kanske önskat mer diskussioner i gruppen, jag hade gärna haft
någon att bolla idéer med då gånger jag fastnade med svåra problem.

Jag kommer att fortsätta att jobba med `autonameow` när jag har tillfälle.
Målet är också att göra projektet offentligt och möjligtvis attrahera
hjälp från intresserade utvecklare.



Referenser
----------

* __Demonstrationsvideo:__ <https://youtu.be/QUkrMO7xYyk>
* __`autonameow` version `v0.4.0`:__ ([`v0.4.0.tar.gz`](https://github.com/jonasjberg/autonameow/archive/v0.4.0.tar.gz), [`v0.4.0.zip`](https://github.com/jonasjberg/autonameow/archive/v0.4.0.zip))
* __Installationsguide:__ <https://github.com/jonasjberg/autonameow/blob/master/install.md>
* __Projektets Wiki-sidor:__ <https://github.com/jonasjberg/autonameow/wiki>
* __Projektets källkod:__ <https://github.com/jonasjberg/autonameow>


--------------------------------------------------------------------------------


*(__P.S.__ Gibson lever och är glad idag, 2017-06-19! __D.S.__)*


[autonameowgithub]: https://github.com/jonasjberg/autonameow
