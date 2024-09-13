---
title: Hvordan bygger man et responsivt website fra bunden?
description: Hvordan bygger man et responsivt website fra bunden?
author: Niels Johan Tygesen
date: 2024-04-11T11:10:00.000Z
tags:
  - post
image: /assets/images/blog/landing.jpg
imageAlt: cgbnh
---
## Til udviklere

Hvis du skal bygge en hjemmeside nu om dage, bør dit primære fokus være at sikre, at den er responsiv og kan tilpasses alle skærmstørrelser. Det skyldes, at Google har meddelt, at alle hjemmesider, der er responsive, vil rangere bedre på grund af bedre indlæsningstider, bedre brugervenlighed og vil blive foretrukket i mobile søgninger. Så en hjemmeside, der indlæses hurtigt og ser godt ud på alle mobilskærme, vil have en fordel i forhold til en hjemmeside, der ikke er bygget responsivt. Og hvis vi skal tale om mobil responsivitet, er vi også nødt til at tale om mobile first programming, hvor du bygger din html og css med mobilskærme i tankerne først. Responsivt design og mobile first-programmering går hånd i hånd, så for at få mest muligt ud af din hjemmeside, skal den laves mobile first og være fuldstændig responsiv.

Denne artikel er til udviklere, der ønsker at forstå, hvordan pokker man laver responsive hjemmesider i første omgang, og den har alle de svar, jeg ville ønske, jeg vidste, da jeg startede. Så lad os komme i gang!

## Start mobile first

Før du overhovedet tænker på at lave en responsiv hjemmeside, er du nødt til at forstå, hvordan man laver en mobile first-hjemmeside. Det er en nøglefærdighed i nutidens webudviklingsverden og efter min mening den bedste måde at lave en hjemmeside på, og det gør det faktisk lettere.

Hele ideen er at strukturere din html og css med mobiltelefonen i tankerne først. Når du er færdig med din html, åbner du den i browseren og inspicerer elementet, og vælger iPhone 5SE-skærmindstillingen. Det er den mindste mobilskærmstørrelse, du vil støde på med en bredde på 320 px. Dette vil være dit lærred i stedet for den helt åbne desktop-visning. Det bliver det sidste! Vi starter med mobilen her, og det er her, det begynder. Jeg kan godt lide at zoome 75% ind, så det ikke er så småt. Det er den skærmstørrelse, du skal skrive din css til at passe til. Der kræves ingen media queries. Bare skriv den kode, der får alt til at passe i denne skærmstørrelse. Det er begyndelsen på mobile first-programmering!

## Strukturering af css med henblik på mobile first

I mobile first starter vi toppen af din css-fil med mobilkoden og tilføjer derefter media queries til større skærmstørrelser, efterhånden som vi kommer ned på siden. De mest almindelige breakpoints at bruge er:

400px - store telefoner
568px - Liggende mobil
768px - Tablet
1024px - Lille desktop (bærbare computere)
1300px - Normal desktop
Og ethvert andet breakpoint, du måtte have brug for, så det passer til resten af dit design.
Det er de standarder, jeg arbejder med, og nogle gange tilføjer man media queries imellem for at sikre, at nogle særlige elementer passer ind. Jeg kan godt lide at begynde at skrive css, så det passer til 320 px-skærme, og derefter tilføje en media query til en min. bredde på 400 px og foretage størrelsesjusteringer til de større telefoner, hvor det er nødvendigt, f.eks. øge skriftstørrelser, ikonstørrelser osv. Jeg starter ved 320px, fordi det er den mindste skærm, du vil støde på, så hvis du vil være fuldt responsiv, er vi nødt til at tage dem i betragtning og derefter tilføje en ny medieforespørgsel til de større telefoner og skræddersy siden til dem også for at få den bedste brugeroplevelse og det bedste design.

For virkelig at være 100% responsive skal du indstille din inspector til "responsive", starte på 320px og trække i kanten af vinduet og få det til at vokse. Uanset hvor noget i designet går i stykker eller ser dårligt ud, skal du indstille en medieforespørgsel til den specifikke skærmstørrelse og rette det. Gør dette hele vejen op forbi desktop-bredder. Ved at gøre det på denne måde vil din hjemmeside passe til alle mulige skærmstørrelser, og du kan sige, at den er 100% responsiv.

Dette er din nye arbejdsskærm. Begyndelsen af dit css-ark starter med koden til at få dit indhold til at passe inden for disse grænser. Det er derfor, det kaldes "mobile first". Desktop-first ville betyde, at vi kodede med en bredde på 1500px og så klemte ned. Det er den gamle måde at gøre tingene på, og det bør du undgå, hvor du kan.

## Opsætning af media queries

Når jeg skriver dine media queries, bruger jeg altid min-width. Jeg laver ikke et interval eller en max-bredde. Det skyldes, at når du bruger min-widths, gælder al styling fra de tidligere media queries stadig for det næste trin op, og kun den nye css for den skærmstørrelse bliver indlæst oven på det, der kom før den. Det forhindrer, at du skal gentage kode eller lave sektioner om igen og igen. De bliver bare overført til den næste skærmstørrelse, hvor de bliver redigeret. Hvert trin op bør bringe dig tættere og tættere på desktopversionen af webstedet. Du laver ikke bare desktop-designet fra bunden, du bygger op til det, så når du når til det punkt, er alle de tunge løft allerede indlæst fra mobilen, alt, hvad der er tilbage, er lidt ekstra resizing eller tweaking for at toppe det af og lave din desktop nav og det endelige footer-design.


Det er det smukke ved mobile first. I stedet for at starte med desktopstørrelsen og klemme alt ned eller omskrive nogle dele, når du bliver mindre, starter du småt og tilføjer til det trin for trin og bygger på den kode, du skrev tidligere, i stedet for at rive den ned. Det passer perfekt sammen med responsivt design, fordi det er nemmere at få tingene til at vokse ind i deres beholdere end at proppe dem ind og presse dem sammen. Så vi bør kunne opnå 100 % responsive designs med mindre arbejde, færre fejl og mindre hovedpine. Det er derfor, jeg er begyndt at tale om mobile first "først". Det gør responsivt design så meget lettere at udføre, når det gøres på denne måde. Så lad os se, HVORDAN vi kan gøre dem responsive uden meget arbejde eller 50 media queries.

## Hvordan laver man responsive websites

Når man forsøger at lave responsive hjemmesider, er det vigtigt først at få styr på html-strukturen og bruge semantisk html. Jeg bruger den samme struktur til alle mine sider, nemlig at dele designet op i sektioner, som hver især har deres eget section-tag, og indeni det har de deres egen .container div, og indeni den har de indholdet. Sådan her:

BILLEDE!

Sektionstagget hjælper med at fortælle Google og skærmlæsere, at denne sektion er forskellig fra de andre omkring den. De er selvstændige, og al information inde i dem er relevant og relateret til sektionens formål. Det er bedre på denne måde, for hvis vi laver dem alle som divs, kan det få tingene til at se lidt rodede ud og gøre det svært for Googles webcrawlere at gruppere information sammen og ikke bare forstå, hvad indholdet er, men også hvad det BETYDER i sammenhæng med tingene omkring det.

Jeg kan godt lide at sætte individuelle containere ind i hver sektion, fordi ikke alle sektioner har den samme bredde. Jeg har set mange hjemmesider med en containerklasse, der omslutter hele hjemmesiden, og alt forbliver bare inden for den bredde. Det er kedeligt. Og det begrænser, hvad du kan skabe. Ved at have individuelle containere har du mere kontrol over, hvad der kan gøres i disse sektioner, og du er ikke begrænset til den samme bredde som resten af siden.

## Opsætning af containers

Jeg kan godt lide at have et globalt css-ark, der bruges på alle sider, så disse stilarter kan ændres én gang, og de ændres på alle sider, som f.eks. header- og footer-kode, kernesidestilarter som skrifttyper og farver og knapper, og hvordan alle containere opfører sig.

Selvom vi har individuelle containere i hver sektion, vil vi stadig gerne have nogle stilarter, som de alle har til fælles, så de opfører sig på samme måde. Her er, hvad jeg bruger på dem alle til at starte på 320px:

BILLEDE!

HVORFOR: Jeg indstiller beholderen til bredden 100%, så den vokser med skærmstørrelsen. Det er 100 % bredden af skærmstørrelsen. Det er sådan, du får dem til at vokse - ved at bruge procenter som bredder. Indstil derefter margen til "auto". Når du indstiller den til auto, beregner den "automatisk" venstre og højre margen for at gøre beholderen centreret vandret på skærmen. Ethvert element med visning indstillet til blok og margen indstillet til auto vil altid være centreret vandret i sin beholder eller browservinduet. Så når beholderen holder op med at vokse med den maksimale pixel, du indstiller den til, forbliver den centreret på skærmen. Indstil derefter padding til padding: 0 10px for at tilføje padding til venstre og højre. padding tilføjer plads INDE i et element, mens margin tilføjer plads omkring det. Ved at tilføje padding til venstre og højre for dine containere giver det den 10px buffer mellem indholdet inde i den og kanten af skærmen. Selvom du ønsker, at din beholder skal være 100 % af bredden af skærmen kant til kant, vil du ikke have, at dit indhold rører 100 % kant til kant. Det ser ikke godt ud. Så ved at tilføje den plads INDE i beholderen for at "pude" venstre og højre side skaber du en lille bumper, som dit indhold kan sidde imod i stedet for skærmen.

På dette billede, når vi svæver over en container i inspektøren, ser vi de grønne bjælker til højre og venstre. Det er din padding.

BILLEDE!! 

Når man kredser tilbage, fortæller max-bredden den, ved hvilken pixelbredde den skal stoppe med at vokse. Den bedste "hurtige" måde at opretholde ensartet design på alle de mærkelige skærmstørrelser mellem mobil og tablet er at indstille dine containere til at have en maks. bredde på 450 px, hvilket bare er lidt større end den største telefonskærm. På den måde mellem 450px og 568px (landskabstilstand på telefoner) forbliver containerne 450px, og designet "vokser" ikke længere end det. Elementerne inde i disse beholdere bliver, hvor de er. Den eneste ulempe er, at indholdet vil have en masse plads til venstre og højre og måske ikke ser bedst ud. Men dette er den hurtige og beskidte måde at få den til at reagere fuldt ud. Det, jeg faktisk råder dig til at gøre, er at tilføje ekstra medieforespørgsler og ændre designet og størrelsen af dine elementer inde i beholderne for at fylde skærmen op i alle mulige størrelser - hvis du har tid til at gøre en indsats. Det kan være lidt tidskrævende at gøre det den lange vej, men den overordnede kvalitet af produktets udseende vil være så meget bedre. Bare gør det, jeg nævnte tidligere, og øg størrelsen af browservinduet, og hvor designet går i stykker hvor som helst på siden, indstil en medieforespørgsel for den størrelse og ret den, og så videre.

Så hvis du vil være virkelig lydhør, skal du indstille en max-bredde på din container til 1000px, hvilket vil være den perfekte størrelse, når du kommer til 1024px-størrelsesdelen af din css. Når du så kommer højere, kan du ændre max-bredden til hvad den skal være for de forskellige sektioner. Der er ingen "én bredde til at styre dem alle", det er helt afhængigt af dit design og kan være forskelligt for flere sektioner og medieforespørgselsstørrelser. Det er ok!

Overordnet set er dette den grundlæggende skabelon, du skal vænne dig til at gøre for at begynde at bruge mobilt første responsive design på dine hjemmesider. Du har din sektion med en containerklasse inde i den, og sektionsindholdet inde i den container. Beholderen er indstillet til 100 % bredde og en maksimal bredde, som du ønsker, at den skal stoppe med at vokse til, og margin auto vil holde den centreret, mens polstringen til venstre og højre forhindrer, at indholdet rører kanterne af skærmen. Det er den grundlæggende byggesten i responsivt design og vil være en metode, hvor du vil bruge MEGET, så det er vigtigt virkelig at forpligte dette mønster til muskelhukommelsen. Du kan også indstille dit indhold til bredde: 100 %, så det kan vokse med størrelsen på sin beholder. Bare sørg for at tjekke sidedesignet, når du øger bredden af skærmen og se, hvilket sektionsskift eller se ud, og indstille en specifik medieforespørgsel til at målrette den.

## Hvordan du skal strukturere din html 

Nu til den sjove del! Når du får et desktopdesign, hvordan strukturerer du så din html for den bedste overgang fra mobil til desktop? Den første ting du skal gøre er at analysere hver SECTION individuelt og bryde designet ned i dets beholdere og stykkerne inde i dem. Her er et eksempel på design fra min hjemmeside:

## Stacking order i html

Når du skriver din html, skal du huske på, hvordan elementerne stables baseret på den oder, hvori de optræder i koden. Hvis du har tre elementer, i rækkefølge fra top til bund, vil det øverste element naturligvis være først i mobilen, og på desktop, hvis de skal stables vandret, så vil det være i venstre side, det midterste element vil være i midten og den sidste vises til højre.

BILLEDE !!! 


Det er et simpelt koncept, og det kender mange sikkert allerede, men jeg ville gerne smide dette ind for dem, der måske har misset denne del eller havde brug for at vide det. Når du skriver din html og strukturerer dine elementer, skal du huske på, at at gå fra top til bund i html til sidst vil stable venstre mod højre, når der er plads nok.

Blokniveauelementer (display:blok) vises på deres egne linjer. Så startende øverst, med "Hvad vi gør", grafik og afsnit, hvad er den enkleste måde at kode det ved at bruge så få div'er (hvis nogen) som muligt? Skal du pakke disse elementer ind i én beholder og arbejde med dem inde i den?

Når jeg ser dette, ser jeg først blokniveauelementerne, der kan være på deres egen linje uden nogen ved siden af dem, såsom overskriften og afsnittet. Jeg kan indstille dem til display:block og text-align:center. Dette vil centrere dem med eller uden en beholder omkring dem, fantastisk! Men gruppen af grafik ser ud til, at den SKAL være i en separat beholder, så vi kan bruge Flexbox til at arbejde specifikt på dem og centrere dem. Så for den sektion ser det ud til, at vi bare har brug for den ene container div til at gruppere grafikken sammen, så de kan arrangeres, de to andre kan bare være blokniveauelementer og vil skaleres fint ved at gå fra mobil til desktop, fordi de i det væsentlige vil være i de samme nøjagtige pletter opfører sig på nøjagtig samme måde.

Nu til gruppen af tre mini "kort", der er centreret vandret. Fordi de er ved siden af hinanden, kan vi ikke slippe afsted med at gøre dem alle på blokniveau, da de skal være i en linje sammen (display:inline-blok), og ikke af sig selv. Så vi kan tilføje en div omkring dem med en klasse af "wrapper", så vi kan arrangere dem i den container uden at påvirke resten af sektionen over den. Og inden i den container ser det ud til, at hvert "kort" også skal have en container omkring sig, lad os kalde det "item", og hvert element inde i det kan være blokniveauelementer, da de alle er på deres egen linje af sig selv. Så det ser ud til, at det er her, vi kan stoppe med at tilføje containere.

Jeg ved, at det er meget at tage med i teksten, så her er en grafik, der viser, hvordan vi grupperede alt visuelt for at planlægge deres css-placering og arrangement:

BILLEDE!

Det kan være lille at se, om du er på mobil, men det røde felt er dine sektionstags, og indeni det er din container (grøn boks), og de blå felter er de ekstra indholdscontainere, vi skal bruge for at arrangere disse elementer uden at ødelægge de andre elementer. Vi "indeholder" dem, så de kan manipuleres separat fra resten af afsnittet. De orange felter på venstre og højre side af din beholder er din margin: autocentrerer beholderen inde i sektionsmærkerne. De sorte bokse er de "vare"-beholdere, vi bruger til at pakke hver enkelt gruppe ind, så de indeholder indholdet. Elementerne inde i dem kan alle indstilles til display:block, text-align:center, margin:auto for at centrere dem lodret og vandret i .item-beholderen.

Sådan skal mobilversionen se ud med den givne html-struktur og naturlige stabling af html-elementerne:

Billede!!!

Du kan begynde at "SE" hvordan mobil kan startes ved at se på strukturen af skrivebordsdesignet, opdele det i dets blokniveauelementer og dets containere. Dette er teknisk set den bedste måde at strukturere html'en for dette design ved at bruge den mindst mulige mængde divs. Jeg siger teknisk, fordi vi endda kunne slette den vigtigste .container div omkring alt, da det ser ud til, at det ikke er nødvendigt for at fungere som en barriere for elementer at rykke op imod. Jeg efterlod det på skrivebordsbilledet for at vise, hvordan det ser ud. Hvis vi fjernede .container-klassen, hvordan tror du så indholdet kan forblive centreret? Divs er blokniveauelementer som standard, så din .wrapper-klasse omkring de tre .items behøver bare margin:auto for at centrere sig selv vandret inden for sektionstags. Sådan skal html'en se ud:

BILLEDE!!

Kopier denne html og se om du selv kan genskabe layoutet i din egen kodeeditor. Jeg fjernede .containeren fra dette design, fordi det ikke er nødvendigt, og vores mål, når vi skriver html, er at bruge så få div'er som muligt. Dette vil få os til at skrive renere, bedre ydende og lettere at forstå kode.

Det er sådan, du skal se på designs for korrekt at planlægge, hvordan de vil se ud og opføre sig fra mobil til desktop, og det er den første ting, du skal gøre, før du skriver nogen kode. Du skal analysere de individuelle sektioner og planlægge din html-struktur baseret på, hvad der kan være blokniveauelementer, og hvad der har brug for containere. At finde ud af, HVORDAN du vil gruppere elementerne, vil hjælpe dig med at se, hvordan puslespilsbrikkerne kan arrangere sig selv fra mobil til desktop.

Du vil også bemærke brugen af aria-hidden="true", dette er en Aria-attribut, der fortæller skærmlæsere at ignorere dette element, da det ikke er vigtigt. Vi bruger dette til alt, der udelukkende bruges til design og har ingen betydning for at forstå indholdet på siden. Så dybest set ville alle ikoner have denne egenskab på sig, da de kun er til at se og tilføjer intet til læsernes forståelse af, hvad de læser. For at lære mere om webtilgængelighed og brug af de rigtige Aria-attributter, besøg www.w3.org for at lære om dem, og hvornår du skal bruge dem. Dette er noget, du skal bruge meget, når du skriver din html. Hav dem altid i tankerne!

Så hvis vi først skulle kode denne mobil, ville vi starte øverst. Jeg vil bruge en gammeldags måde at centrere indhold uden Flexbox på denne for at vise en anden måde at gøre tingene på. Når du har inline-blok-elementer inde i en container, hvis du tilføjer text-align:center på containeren, vil alle inline-blokkene nu blive centreret inde i containeren. vertikal-align: midt centrerer inline-blokelementer lodret inde i deres beholdere. Det er en fin lille ejendom, jeg brugte en gang imellem.

BILLEDE!!

Vi kan så skabe plads mellem billederne ved at tilføje margen til venstre og højre for hvert billede med margin:0 10px. Dette tilføjer 0 margen top og bund og 10px margen til venstre og højre. Dette er en meget hurtig og nem måde at centrere og placere elementer inde i en container ved hjælp af inline-blok-egenskaben. Du kan også bruge tekstjustering: venstre eller højre, og det vil skubbe alle elementer til venstre eller højre for beholderen. Sådan skal det se ud:

Billede!

Jeg tilføjede width:100% og max-width:600px til p-tagget, fordi jeg vil have det til at vokse bredere med skærmen og stoppe ved 600px, hvilket er hvor bredt det i sidste ende bliver på skrivebordet. Så når vi kommer til tablet, vil den allerede være på skrivebordsstørrelsen og behøver ikke røre ved den, når vi kommer til skrivebordet. Mindre arbejde! Den har også en polstring til venstre og højre på 10px, da vi ikke bruger beholderen længere. Den skal bruge noget for at forhindre den i at røre kanterne på skærmen, så når vi har elementer uden en hovedbeholder at skubbe op imod, kan vi bare tilføje polstringen til venstre og højre, som ville have været der med beholderen.

Med hensyn til css'en om, hvordan du vil arrangere og centrere de 3 kort, anbefaler jeg stærkt at lære at bruge flexbox fra Flexbox Froggy og øve dig i at bruge det. Jeg vil ikke gå ind i flexbox her, fordi denne artikel allerede er lang nok... Men for at gøre det uden Flexbox, brug den samme inline-blok teknik, som jeg brugte på billederne. Det vil gøre det samme arbejde.

Men! Jeg vil ikke lade dig hænge på, hvilken kode du skal bruge, så for .wrapper-beholderen er her koden, du ville skrive på skrivebordet:

BILLEDE!

Dette vil centrere emnerne og stable dem lodret, og tillade dem at vokse med skærmstørrelsen, der kun stopper ved 350px bred, mens de stadig er centreret.

Disse elementer forbliver på denne måde hele vejen gennem tabletten. Så når du kommer til den skærmstørrelse, skal du ikke gøre noget!

Billede!

Billede2!

Når du kommer til skrivebordet, er ovenstående kode, hvad du skal bruge. Flexbox og CSS Grid er de grundlæggende værktøjer til at skabe responsive hjemmesider. Jeg bruger Flexbox overalt på min side. Med blot et par linjer kode kan du fuldstændig omarrangere stablingen og placeringen af elementerne inde i flexbeholderne. Efter at have læst denne artikel, foreslår jeg stærkt at du lærer og øver dig med Flexbox og Grid.

## Opsummering

Det er alt det grundlæggende i mobil første responsive programmering og hvordan man konfigurerer det. Forhåbentlig hjælper dette dig med at forstå, hvordan du konfigurerer din css for at begynde mobilt første responsive design. Det kræver øvelse og lidt tilvænning, men når først du har formlen nede, og du bliver rigtig god til at nedbryde hver sektions design i deres mest basale og minimale strukturer, vil det hele komme i anden natur for dig, og til sidst vil du være i stand til bare at se på et skrivebordsdesign og "vide" præcis, hvordan du vil bygge det. Dette vil gøre dig meget mere effektiv i din tid, og din kode vil blive skrevet mere rent og med mere formål, hvilket vil minimere mængden af fejl og hovedpine, du kan løbe ind i under processen.
