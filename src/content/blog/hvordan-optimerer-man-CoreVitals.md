---
title: Hvordan optimerer man et websites Core Vitals og Page Speed Score?
description: Hvordan optimerer man et websites Core Vitals og Page Speed Score?
author: Niels Johan Tygesen
date: 2024-04-11T11:10:00.000Z
tags:
  - post
image: /assets/images/blog/landing.jpg
imageAlt: cgbnh
---

Jeg har for nylig interesseret mig for at optimere et websteds sidehastighedsscore, efter at Google annoncerede deres nye Core Vitals-metrics, og hvordan det vil være den førende rangeringsfaktor fremover. Det er grundlæggende at favorisere hjemmesider, der har den hurtigste og bedste mobiloplevelse. Og det er det, jeg vil vise dig, hvordan du gør lige nu.


## Asset Optimering
Generelt handler meget af det om aktivoptimering som at have billeder i samme størrelse, som de bliver vist ved. Som ikke at have et 1000px bredt billede ændret i css til at være 300px bredt på skærmen. Det er spild af plads. Også tabsfri komprimering af alle dine aktiver kan spare op til 80 % af filstørrelsen. Jeg bruger Compressor.io til at komprimere alle mine billeder. Jeg betaler for pro-abonnementet, så jeg kan uploade 100 billeder til komprimering ad gangen. Jeg har brugt det i årevis. Jeg kan varmt anbefale dem.

Også baggrundsbilleder. Hvorfor indlæse et 2300px bredt lagerfoto på en 400px bred telefonskærm? Tilpas størrelsen på den sugekop til 500px bred, og komprimer den. Du går fra 2,3 MB til gerne 37k eller mindre. KÆMPE reduktion i størrelse og belastningstider. Så på tablet og desktop nulstiller du bare baggrundsbilledet til det større 2300px billede. Jeg så en hjemmeside fra en person, der indlæste flere 4000px brede billeder som baggrunde, og det var langsomt som helvede. Det er ikke nok at komprimere det. For selvom det komprimerer 70%, er 70% af 4MB stadig som 1,2MB, hvilket er enormt for et billede at indlæse på mobilen. Tilpas størrelsen på dine billeder og indlæs de mindre til mobil og de større til tablet og desktop, og komprimer dem.

Så er der at vælge de rigtige billeder til den rigtige skærmstørrelse, og det er, hvad attributten "srcset" gør. Du kan læse om det her fra Mozilla Developer Network. Hvad det gør, er, at du giver en liste over billeder i forskellige størrelser, der skal indlæses i de skærmstørrelser, du vil have dem til at indlæse, og bruger "src" som dit reservebillede. På denne måde, hvis du har et billede, der er 700px bredt i din html på skrivebordet, kan du indlæse en version af det, der er 350px bredt på skærme under 480px eller hvad du vil, og indlæse en mindre fil, som igen forbedrer din ladetid.

Når du har gjort alt det, skal du sørge for at tilføje de korrekte højde- og breddeattributter til dine billeder, da Google ønsker at se dem på hver enkelt af dem. Det hjælper med at allokere plads til billedet, før det indlæses, og hjælper med at reducere indholdslayoutskift.


## Lazy Loading
Så er der lazy loading indlæsning ved hjælp af loading=“lazy” attributten, der understøttes af de fleste browsere. Dette brugte browsere indbygget i lazy loading uden at du skulle lave en masse smart JavaScript. Men lad være med at indlæse billeder, der er "over skillelinjen", hvilket betyder bunden af skærmen, når hjemmesiden indlæses. Hvis billedet indlæses på landingssidesektionen og i viewporten, skal du ikke lade det indlæse. Det vil skabe indholdslayoutskift. Så uanset hvilke billeder der er på skærmen, når dit websted indlæses første gang, bør det ikke lade sig indlæse.

## Fjern jQuery, Google Fonts, og alle andre ikke essentielle CDN links
Der er tid og sted for alting, og jQuerys tid er 5 år siden, og det er på bænken. Klasseskift og alt det, der kan håndteres i javascript nu, og der er virkelig ingen grund til at bruge JQuery længere. Den er oppustet, og fjernelse af den kan gøre dit websted mere sikkert og indlæses meget hurtigere. Fjern det! Googles sidehastighedsscore vil mærke det som noget, du skal fjerne for at forbedre din score, så vi bør alle lige vænne os til at arbejde uden det, medmindre det er absolut nødvendigt.

Så er der dine Google Fonts CDN-links. I stedet for at linke til dem i dit hoved, skal du downloade dine skrifttyper fra dem, hvis det ikke er en standardskrifttype på browsere. Jeg bruger @font-face til at indlæse mine skrifttyper lokalt. Jeg gemmer alle de downloadede filer i en skrifttypemappe og indlæser dem derefter på mit core-styles.css ark, der deles på alle sider på webstedet. På denne måde kan jeg eliminere at bruge google fonts cdn, som eliminerer det som en gengivelsesblokerende ressource.

Bare kopier og indsæt denne kode i dit CSS-ark, der er delt på ALLE dine sider. Erstatter filstien med filstien til din skrifttype, som du downloadede. Skrifttypefamilieejendommen her er, hvad DU kalder den. Så det behøver ikke at være "Hummer" som i eksempelkoden. Det kan hedde, hvad jeg vil have det til, og det er det, jeg sagsøger, når jeg erklærer det i CSS et sted.

SKAL VÆRE BILLEDE --
@font-face {
    font-family:'Lobster';
    src: url('/fonts/Lobster-Regular.ttf') format('woff2');
    font-weight: normal;
    font-style: normal;
}
--


Ved at downloade og indlæse dine skrifttyper lokalt kan du eliminere behovet for at bruge Google CDN og indlæse dine skrifttyper endnu hurtigere, mens du også fjerner en gengivelsesblokerende ressource. Jeg anbefaler stærkt at gøre dette for alle dine websteder.

## Defer din ikke essentiel Javascript
På alle dine script-tags skal du tilføje defer-attributten til det åbne script-tag, og dette vil "udskyde" indlæsningen, indtil EFTER webstedet er indlæst. På denne måde afbryder Javascript ikke hjemmesiden i at indlæse dets HTML og CSS først og male siden. Den venter tålmodigt på sin tur, indtil alle andre er færdige.

## Brug SVG over PNG hvis muligt
Brug så mange svgs som du kan over pngs. Svgs er meget mindre og indlæses meget hurtigere. Jeg bruger Flaticon til at få al min svg-grafik og ikoner, og jeg kan tilpasse deres farver og downloade svg. Elsker det. Dette erstatter også Fontawesome, da det er et andet cdn-link, du ikke behøver at indlæse. I stedet for at bruge Fontawesome, skal du bare indlæse de ikoner, du har brug for, som svgs. Det er meget mere let end at bruge Fontawesome.

Hvis du kan, så hyr en person fra Fiverr, som er en SVG grafisk illustrator til at konvertere dine kunders logoer til svgs og indlæse dem på webstedet i stedet. Meget mere optimeret og skalerbar. Du kan erstatte en 36k png eller mere med en 2k svg. Det er hver en øre værd. Du kan finde nogle overkommelige muligheder for under $30 pr. grafik. En fantastisk investering.

Det er altid en god idé at konvertere dine kunders logoer til svg-format og derefter give dem det til brug for mærkater, visitkort og t-shirts. De vil elske dig for det.

## Google Lighthouse
Når alt er sagt og gjort, tjek dine Google Lighthouse-resultater i din inspektør fra dev tools. Normalt skal du bare markere nogle tilgængelighedsting som at tilføje aria-label-attributter til links uden tekst eller alt-tags på billeder eller kontrastproblemer. Når du først har en hastighedsscore på 96+ sider og næsten 100 over hele linjen på Lighthouse, er din hjemmeside nu korrekt optimeret og klædt på til at imponere.

Dette er de optimeringstrin, jeg tager, hver gang jeg afslutter en hjemmeside. Jeg ønskede at uddybe dette for alle, der leder efter en detaljeret "fremgangsmåde" om, hvad man skal gøre, og hvordan man gør det uden al jargon og over komplicerede lange beskrivelser. Jeg håber det hjælper!


