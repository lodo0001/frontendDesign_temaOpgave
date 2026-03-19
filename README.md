# Kort refleksion af temaopgaven

Lavet af Emily Goldberg & Louise Do

## 1. Reflekter kort men fagligt over jeres løsning med henblik på udfordringerne og successerne ved opgaven.

Det lykkedes os at udvikle en hjemmeside, hvor de centrale benspænd blev opfyldt, men processen var mere udfordrende, end vi først havde forventet. Undervejs oplevede vi især problemer med GitHub, hvor der opstod vanskeligheder i forbindelse med at hente hinandens commits og ved egne commits. Dette skabte en del frustration og krævede ekstra tid til fejlfinding. Derudover er det noget tid siden, vi sidst har arbejdet med Astro, hvilket gjorde det sværere at genopfriske arbejdsgangen og de grundlæggende principper.

På trods af udfordringerne har vi også opnået flere faglige fremskridt. Det var første gang hvor vi reelt arbejdede med en global.css samt brugen af custom properties, og det har givet os en bedre forståelse for, hvordan man kan skabe mere konsistent og vedligeholdelig styling. Derudover var det nyt for os at skulle tage højde for brugerpræferencer, såsom reduceret bevægelse i animationer, hvilket har øget vores bevidsthed om tilgængelighed og brugeroplevelse.

De succeser, vi har haft, har blandt andet været i struktureringen af koden, hvor vi har arbejdet mere systematisk og forsøgt at opdele vores komponenter på en overskuelig måde. Samlet set har projektet givet os en bedre forståelse for både samarbejdsværktøjer og moderne frontend-udvikling, og hvis vi skulle arbejde videre med løsningen, ville vi fokusere på at styrke vores Git-workflow samt opnå en endnu mere sikker forståelse af Astro.

---

## 2. Fremhæv specifikke kodestumper, der illustrerer brugen af forskellige teknikker og principper fra undervisningen, samt hvorfor de er brugbare.

Nesting:
En af de teknikker, som vi har taget med os videre i dette projekt, er brugen af nesting. Som illustreret i eksemplet nedenfor placerer vi et img-element inde i en header, da billedet fungerer som et barn af headeren. Dette er brugbart da det bidrager til en mere struktureret opbygning af koden, hvor relaterede elementer naturligt grupperes sammen.

```astro
header{
  position: relative;

  img{
    width:100%;
    border-radius: 20px;
    display: block;
  }
}
```

Subgrid til makro-layout:
En anden teknik, vi har benyttet, er subgrid til vores layout. I global har vi body, der definerer de overordnede spor (full-bleed + content), og derefter bruger header, main, footer og section subgrid. Det er gavnligt at bruge subgrid her, da vi arbejder med makro-layouts, hvor vi har full-bleed sektioner og indhold, der skal alignes med resten af indholdet.

```astro
body {
  display: grid;
  grid-template-columns:
    [full-start] minmax(20px, 1fr)
    [content-start] min(1100px, 100%)
    [content-end] minmax(20px, 1fr)
    [full-end];
}

header,
footer,
main,
section {
  display: grid;
  grid-template-columns: subgrid;
  grid-column: full;

  > :not(&) {
    grid-column: content;
  }
}
```

---

## 3. Fremhæv steder, hvor Defensive CSS er tænkt ind.

---

## 4. Reflekter over, hvor i løsningen, der er brugt progressive enhancement og gennemgå kort, hvordan det er løst.

Et eksempel på brugen af progressive enhancement ligger i vores globale CSS, hvor vi bruger @view-transition til at tilføje en mere glidende overgang mellem vores sider. Funktionen virker kun i browsere, der understøtter det, mens navigationen i ældre browsere stadig fungerer normalt, så grundfunktionaliteten bevares. Løsningen sikrer først, at funktionaliteten virker bredt, og forbedrer derefter oplevelsen, hvor det er muligt – og det er essensen af progressive enhancement.

```astro
@view-transition {
  navigation: auto;
}
```

---

## 5. Forklar, hvordan du har organiseret din CSS; hvornår er det globalt, og hvornår er det komponent-specifikt.

Vi har organiseret vores CSS med udgangspunkt i globale styles og design tokens for at sikre et ensartet design på hele vores webløsning. De globale styles indeholder generelle regler, der gælder på tværs af alle sider, såsom grid-layout og typografi.

Design tokens har vi brugt til at definere farver og andre gennemgående værdier fra det udleverede design, så vi nemt kan genbruge dem i de forskellige komponenter. Her har vi også samlet generelle stylingregler som f.eks. gap.

Derudover har vi arbejdet med komponent-specifik CSS i vores Astro-komponenter. Her har vi stylet direkte i den enkelte komponent i <style>-sektionen for at kunne tilpasse designet præcist til det enkelte komponent, som vist i det udleveret design.

Samlet set gælder de globale styles for hele sitet, mens tokens og komponent-specifik CSS bruges mere målrettet afhængigt af komponentens behov og design.
