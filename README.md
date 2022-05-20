# Web Typography, 2020/2021

Wat ik heb geprobeerd:
ik heb een aantal text styles geprobeerd, maar veelal hadden een ingewikkelde html layout waarbij elke letter een eigen html tag zou worden. Ook werd er veel gebruik gemaakt van scss. Bij sommige kon ik de variabelen vervangen, maar soms werd er ook gebruik gemaakt van functies die ik niet zomaar kon vervangen. Ook waren sommige styles gewoon kapot.

bronnen:
.glitch {
  position: relative;
  color: #fff;
  font-size: 4em;
  letter-spacing: 0.5em;
  animation: glitch-skew 1s infinite linear alternate-reverse;

  &::before {
    @include glitchCopy;
    left: 2px;
    text-shadow: -2px 0 #ff00c1;
    clip: rect(44px, 450px, 56px, 0);
    animation: glitch-anim 5s infinite linear alternate-reverse;
  }

  &::after {
    @include glitchCopy;
    left: -2px;
    text-shadow: -2px 0 #ff00c1, 2px 2px #ff00c1;
    clip: rect(44px, 450px, 56px, 0);
    animation: glitch-anim2 5s infinite linear alternate-reverse;
  }
}

@keyframes glitch-anim {
  $steps: 20;
  @for $i from 0 to $steps {
    #{percentage($i*(1/$steps))} {
      clip: rect(random(100) + px, 9999px, random(100) + px, 0);
      transform: skew((random(100) / 100) + deg);
    }
  }
}

@keyframes glitch-anim2 {
  $steps: 20;
  @for $i from 0 to $steps {
    #{percentage($i*(1/$steps))} {
      clip: rect(random(100) + px, 9999px, random(100) + px, 0);
      transform: skew((random(100) / 100) + deg);
    }
  }
}

@keyframes glitch-skew {
  $steps: 10;
  @for $i from 0 to $steps {
    #{percentage($i*(1/$steps))} {
      transform: skew((random(10) - 5) + deg);
    }
  }
}


@mixin glitchCopy {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

bron: https://codepen.io/melzshawn1998/pen/xxdwORB

body {
  color: #ccc;
  background: #111;
  font-family: sans-serif;
}

section {
  padding: 20px;
}

.hero-glitch-layers span {
  animation: paths 5s step-end infinite;
}

.hero-glitch-layers::before {
  animation: paths 5s step-end infinite, opacity 5s step-end infinite,
    font 8s step-end infinite, movement 10s step-end infinite;
    content: attr(data-text);
  position: absolute;
  width: 110%;
  z-index: -1;
    top: 10px;
  left: 15px;
  color: #e0287d;
}

.hero-glitch-layers::after {
  animation: paths 5s step-end infinite, opacity 5s step-end infinite,
    font 7s step-end infinite, movement 8s step-end infinite;
    content: attr(data-text);
  position: absolute;
  width: 110%;
  z-index: -1;
    top: 5px;
  left: -10px;
  color: #1bc7fb;
}

.hero-glitch-layers {
  position: relative;
  font-size: clamp(40px, 10vw, 100px);
  line-height: 1;
  display: inline-block;
  color: #fff;
  z-index: 2;
  letter-spacing: 10px;

  /* Bright things in dark environments usually cast that light, giving off a glow */
  filter: drop-shadow(0 1px 3px);
}

 .single-path {
  clip-path: polygon(
    0% 12%,
    53% 12%,
    53% 26%,
    25% 26%,
    25% 86%,
    31% 86%,
    31% 0%,
    53% 0%,
    53% 84%,
    92% 84%,
    92% 82%,
    70% 82%,
    70% 29%,
    78% 29%,
    78% 65%,
    69% 65%,
    69% 66%,
    77% 66%,
    77% 45%,
    85% 45%,
    85% 26%,
    97% 26%,
    97% 28%,
    84% 28%,
    84% 34%,
    54% 34%,
    54% 89%,
    30% 89%,
    30% 58%,
    83% 58%,
    83% 5%,
    68% 5%,
    68% 36%,
    62% 36%,
    62% 1%,
    12% 1%,
    12% 34%,
    60% 34%,
    60% 57%,
    98% 57%,
    98% 83%,
    1% 83%,
    1% 53%,
    91% 53%,
    91% 84%,
    8% 84%,
    8% 83%,
    4% 83%
  );
}

.paths {
  animation: paths 5s step-end infinite;
}

@keyframes paths {
  0% {
    clip-path: polygon(
      0% 43%,
      83% 43%,
      83% 22%,
      23% 22%,
      23% 24%,
      91% 24%,
      91% 26%,
      18% 26%,
      18% 83%,
      29% 83%,
      29% 17%,
      41% 17%,
      41% 39%,
      18% 39%,
      18% 82%,
      54% 82%,
      54% 88%,
      19% 88%,
      19% 4%,
      39% 4%,
      39% 14%,
      76% 14%,
      76% 52%,
      23% 52%,
      23% 35%,
      19% 35%,
      19% 8%,
      36% 8%,
      36% 31%,
      73% 31%,
      73% 16%,
      1% 16%,
      1% 56%,
      50% 56%,
      50% 8%
    );
  }

  5% {
    clip-path: polygon(
      0% 29%,
      44% 29%,
      44% 83%,
      94% 83%,
      94% 56%,
      11% 56%,
      11% 64%,
      94% 64%,
      94% 70%,
      88% 70%,
      88% 32%,
      18% 32%,
      18% 96%,
      10% 96%,
      10% 62%,
      9% 62%,
      9% 84%,
      68% 84%,
      68% 50%,
      52% 50%,
      52% 55%,
      35% 55%,
      35% 87%,
      25% 87%,
      25% 39%,
      15% 39%,
      15% 88%,
      52% 88%
    );
  }

  30% {
    clip-path: polygon(
      0% 53%,
      93% 53%,
      93% 62%,
      68% 62%,
      68% 37%,
      97% 37%,
      97% 89%,
      13% 89%,
      13% 45%,
      51% 45%,
      51% 88%,
      17% 88%,
      17% 54%,
      81% 54%,
      81% 75%,
      79% 75%,
      79% 76%,
      38% 76%,
      38% 28%,
      61% 28%,
      61% 12%,
      55% 12%,
      55% 62%,
      68% 62%,
      68% 51%,
      0% 51%,
      0% 92%,
      63% 92%,
      63% 4%,
      65% 4%
    );
  }

  45% {
    clip-path: polygon(
      0% 33%,
      2% 33%,
      2% 69%,
      58% 69%,
      58% 94%,
      55% 94%,
      55% 25%,
      33% 25%,
      33% 85%,
      16% 85%,
      16% 19%,
      5% 19%,
      5% 20%,
      79% 20%,
      79% 96%,
      93% 96%,
      93% 50%,
      5% 50%,
      5% 74%,
      55% 74%,
      55% 57%,
      96% 57%,
      96% 59%,
      87% 59%,
      87% 65%,
      82% 65%,
      82% 39%,
      63% 39%,
      63% 92%,
      4% 92%,
      4% 36%,
      24% 36%,
      24% 70%,
      1% 70%,
      1% 43%,
      15% 43%,
      15% 28%,
      23% 28%,
      23% 71%,
      90% 71%,
      90% 86%,
      97% 86%,
      97% 1%,
      60% 1%,
      60% 67%,
      71% 67%,
      71% 91%,
      17% 91%,
      17% 14%,
      39% 14%,
      39% 30%,
      58% 30%,
      58% 11%,
      52% 11%,
      52% 83%,
      68% 83%
    );
  }

  76% {
    clip-path: polygon(
      0% 26%,
      15% 26%,
      15% 73%,
      72% 73%,
      72% 70%,
      77% 70%,
      77% 75%,
      8% 75%,
      8% 42%,
      4% 42%,
      4% 61%,
      17% 61%,
      17% 12%,
      26% 12%,
      26% 63%,
      73% 63%,
      73% 43%,
      90% 43%,
      90% 67%,
      50% 67%,
      50% 41%,
      42% 41%,
      42% 46%,
      50% 46%,
      50% 84%,
      96% 84%,
      96% 78%,
      49% 78%,
      49% 25%,
      63% 25%,
      63% 14%
    );
  }

  90% {
    clip-path: polygon(
      0% 41%,
      13% 41%,
      13% 6%,
      87% 6%,
      87% 93%,
      10% 93%,
      10% 13%,
      89% 13%,
      89% 6%,
      3% 6%,
      3% 8%,
      16% 8%,
      16% 79%,
      0% 79%,
      0% 99%,
      92% 99%,
      92% 90%,
      5% 90%,
      5% 60%,
      0% 60%,
      0% 48%,
      89% 48%,
      89% 13%,
      80% 13%,
      80% 43%,
      95% 43%,
      95% 19%,
      80% 19%,
      80% 85%,
      38% 85%,
      38% 62%
    );
  }

  1%,
  7%,
  33%,
  47%,
  78%,
  93% {
    clip-path: none;
  }
}

.movement {
  /* Normally this position would be absolute & on the layers, set to relative here so we can see it on the div */
  position: relative;
  animation: movement 8s step-end infinite;
}

@keyframes movement {
  0% {
    top: 0px;
    left: -20px;
  }

  15% {
    top: 10px;
    left: 10px;
  }

  60% {
    top: 5px;
    left: -10px;
  }

  75% {
    top: -5px;
    left: 20px;
  }

  100% {
    top: 10px;
    left: 5px;
  }
}

.opacity {
  animation: opacity 5s step-end infinite;
}

@keyframes opacity {
  0% {
    opacity: 0.1;
  }

  5% {
    opacity: 0.7;
  }

  30% {
    opacity: 0.4;
  }

  45% {
    opacity: 0.6;
  }

  76% {
    opacity: 0.4;
  }

  90% {
    opacity: 0.8;
  }

  1%,
  7%,
  33%,
  47%,
  78%,
  93% {
    opacity: 0;
  }
}
}

<h2 class="hero-glitch-layers" data-text="近設計"><span>近設計</span></h2>

.voice1 {
  font-size: 5rem;
  font-weight: bold;
  text-transform: uppercase;
  position: relative;
  text-shadow: 0.05em 0 0 #00fffc, -0.03em -0.04em 0 #fc00ff,
    0.025em 0.04em 0 #fffc00;
  animation: glitch 725ms infinite;
}

.voice1 span {
  position: absolute;
  top: 0;
  left: 0;
}

.voice1 span:first-child {
  animation: glitch 500ms infinite;
  clip-path: polygon(0 0, 100% 0, 100% 35%, 0 35%);
  transform: translate(-0.04em, -0.03em);
  opacity: 0.75;
}

.voice1 span:last-child {
  animation: glitch 375ms infinite;
  clip-path: polygon(0 65%, 100% 65%, 100% 100%, 0 100%);
  transform: translate(0.04em, 0.03em);
  opacity: 0.75;
}

@keyframes glitch {
  0% {
    text-shadow: 0.05em 0 0 #00fffc, -0.03em -0.04em 0 #fc00ff,
      0.025em 0.04em 0 #fffc00;
  }
  15% {
    text-shadow: 0.05em 0 0 #00fffc, -0.03em -0.04em 0 #fc00ff,
      0.025em 0.04em 0 #fffc00;
  }
  16% {
    text-shadow: -0.05em -0.025em 0 #00fffc, 0.025em 0.035em 0 #fc00ff,
      -0.05em -0.05em 0 #fffc00;
  }
  49% {
    text-shadow: -0.05em -0.025em 0 #00fffc, 0.025em 0.035em 0 #fc00ff,
      -0.05em -0.05em 0 #fffc00;
  }
  50% {
    text-shadow: 0.05em 0.035em 0 #00fffc, 0.03em 0 0 #fc00ff,
      0 -0.04em 0 #fffc00;
  }
  99% {
    text-shadow: 0.05em 0.035em 0 #00fffc, 0.03em 0 0 #fc00ff,
      0 -0.04em 0 #fffc00;
  }
  100% {
    text-shadow: -0.05em 0 0 #00fffc, -0.025em -0.04em 0 #fc00ff,
      -0.04em -0.025em 0 #fffc00;
  }
}


bron: https://codepen.io/cbanlawi/pen/xxRBeMY



<p class="voice1">
    <span aria-hidden="true">codepen</span>
    codepen
    <span aria-hidden="true">codepen</span>
  </p>
  
  .voice1 {
  position: relative;
	&::after {
    content: "|";
    position: absolute;
    right: 0;
    width: 100%;
    color: $caret-color;
    background: $bg;
    animation: typing $animation-time steps($text-length) forwards,
      caret 1s infinite;
  }
}
// Animation
@keyframes typing {
	to { width: 0 }
}
@keyframes caret {
	50% { color: transparent }
}

.voice1 {
  width: 22ch;
  animation: typing 2s steps(22), blink .5s step-end infinite alternate;
  white-space: nowrap;
  overflow: hidden;
  border-right: 3px solid;
  font-family: monospace;
  font-size: 2em;
}

@keyframes typing {
  from {
    width: 0
  }
}
    
@keyframes blink {
  50% {
    border-color: transparent
  }
}


{
    font-size: 2em;
    animation: interlinked .5s infinite linear;
}

@keyframes interlinked {
    0% {
        text-shadow: 5px 0px #FF0000;
    }
    25% {
        text-shadow: 0px 7px #257ca3;
    }
    60% {
        text-shadow: 5px 0px #FF0000;
    }
    100% {
        text-shadow: -5px 0px #257ca3
    }
}






Als je doof bent, of als je om een andere reden geen geluid kunt horen, dan mis je veel informatie als je een film kijkt. Knisperende voetstappen, langzaam aanzwellende muziek, nerveus getik op een deur, je hoort het natuurlijk allemaal niet. Nu bestaat er zoiets als *closed caption*, wat een type ondertiteling is waarbij ook dingen als omgevingsgeluiden en de muziek beschreven worden. Hierdoor krijgt een kijker die informatie wel binnen.

Alleen wordt die auditieve informatie nogal neutraal beschreven. Het geluid van huilend persoon zou bijvoorbeeld beschreven kunnen worden als *snikgeluid op de achtergrond*. En iemand die lacht zou geschreven kunnen worden als *iemand lacht.* Heel neutraal, bijna zakelijk, en bovendien allebei in precies hetzelfde neutrale lettertype. Terwijl het toch echt over twee heel verschillende emoties gaat. 

Dat kan visueel sterker. 

En dat gaan jullie doen.

## Leerdoelen

- Je kan de kennis over vormgeving die je hebt opgedaan tijdens de minor technisch toepassen met behulp van CSS
- Je kan verborgen nuance uit een audiotrack overtuigend vertalen naar visuele (typografische) beelden
- Je kan je typografische keuzes onderbouwen.
- Je hebt de exclusive design principles gebruikt.

## Oplevering

Je levert een werkende versie op, gemaakt met HTML, CSS en JavaScript. Deze staat op Github. In een duidelijke readme documenteer en onderbouw je je ontwerpkeuzes. Je developmentgeschiedenis is terug te vinden op GitHub.

Je levert ook een *screen recording* met audio op van je fragment. Dit is een video van de definitieve versie, gemaakt van jouw browserscherm.

De beoordeling is mondeling en volgt [de rubric uit het beoordelingsformulier](web-typografie-beoordeling.pdf).

## Typografische restricties

Je *moet* een van deze twee opties kiezen, en je keuze moet je onderbouwen. In je readme staat een uitleg over je overwegingen om de ene of de andere restrictie te kiezen.

### Optie 1: Systeemfont

De eerste optie is dat je gebruik maakt van het zogenaamde *systeemfont* van degene die naar jouw werk kijkt. Dit font verschilt per operating system, en het verschilt soms zelfs per versie van het operating system. Het is ook aan te passen door de gebruiker zelf. 

Je hebt dus geen controle over welk lettertype er precies gebruikt wordt. Het levert dus een onzeker, en beperkt typografisch palet op. Je hebt geen *light* versies, of *extrabold*. En ook geen serif en sans-serif versie van dezelfde familie. In dit geval heb je alleen de beschikking over normal, **bold** en _italic_. Dit heeft natuurlijk ook zijn voordelen!

### Optie 2: Brenner

Je kan er ook voor kiezen om gebruik te maken van de complete Brenner familie. Dit is een zeer uitgebreid en uiterst flexibel font. [Hier kan je je verdiepen in dit font](https://www.typotheque.com/blog/brenner_an_unusual_typeface_family_with_distinct_voices). Als je kiest voor dit font dan heb je de beschikking over een *sans serif*, een *condensed*, een *serif*, een *monotype*, een *slab*, een *display* en een *script* versie. En veel van deze versies hebben varianten van *light* tot *bold*, en allemaal zowel *bold* als *italic*.

Met Brenner zijn er natuurlijk veel en veel meer mogelijkheden dan met systeemfonts. Dat kan zowel een voordeel als een nadeel zijn. 

Voor een overzicht, zie [de brenner.pdf](brenner.pdf).

## Het fragment

Ik heb een fragment voorbereid. Het gaat om twee scenes uit *Blade Runner 2049*. De captions staan in de HTML, en ze verschijnen in sync met de video. [Kijk maar](closed-captions/index.html).

### De captions

De captions staan in de html, in het bestand index.html. Je kan aan elke paragraaf eventueel een of meer classes toevoegen. Bijvoorbeeld `voice1` of `voice2 soft`. Classes voeg je handmatig toe in de html.

Met JavaScript worden er een paar dingen extra gedaan: 

- er wordt aan elke paragraaf een unieke class toegevoegd (`p0`, `p1`, etc)
- Elk woord wordt in een aparte `span` gezet. Hierdoor kan je elk woord apart stylen, en eventueel ook [na elkaar laten verschijnen](https://github.com/cmda-minor-vid/web-typography-18-19/blob/master/closed-captions/css.css#L41).

### Tijdens het afspelen

Tijdens het afspeelen wordt er een class `on` op de caption gezet als hij moet verschijnen, en een class `off` als hij klaar is. *Zowel class `on` als class `off` blijft op de caption staan!*

De timimg van de captions kan je aanpassen in [closed-captions/captions.js](closed-captions/captions.js).

Er verschijnen ook classes op de body op momenten dat er geluiden worden afgespeeld, zoals `sound1` en `sound2`. Je kan geluiden toevoegen in [closed-captions/sounds.js](closed-captions/sounds.js).

*let op,* de geluiden zijn niet compleet, dit zal je zelf moeten aanvullen.

## Een eigen fragment (afgeraden, uitgebreide onderbouwing is nodig)

Je kan er ook voor kiezen om een eigen, *beter* fragment te gebruiken. Dit wordt afgeraden. De tijd die je besteedt aan het zoeken naar dat fragment kan je beter besteden aan het werken aan de opdracht. Bovendien blijkt dat er vaak fragmenten worden gekozen die niet goed voldoen aan de opdracht. Als je een ander fragment kiest dan *moet* je dit goed onderbouwd voorleggen aan je docent. De deadline hiervoor is vrijdagochtend in de eerste week.

### Waar moet je op letten bij het kiezen van een eigen fragment.
Lees de opdracht nog eens goed door. Waar gaat het ook al weer precies om? 

Voor een goede onderbouwing van je keuze voor een ander fragment moet je deze vragen in elk geval beantwoorden:

- Welke informatie zit er in de audio die echt niet zichtbaar is?
- Welke rol speelt de audio in het fragment?
- Werkt de scene nog zonder geluid?
- Waarom is dit fragment beter dan het aangeboden fragment?

Je kan dan de nodige HTML en JavaScript genereren door gebruik te maken van [caption generator](https://cmda-minor-vid.github.io/web-typography-18-19/generator/) (in Google Chrome). 

Als je de closed captions wil bewerken dan kan je een tool zoals [Amber Script](https://www.amberscript.com/en) gebruiken. Daar kan je exporteren als `.srt`, en die kan je weer door de generator halen.