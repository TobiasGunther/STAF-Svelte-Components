# Hvordan få STAF sitt Svelte komponentbibliotektet til å fungere

Dette repoet inneholder info rundt oppsett at et nytt Svelte prosjekt som benytter STAF sitt eksisterende Svelte komponentbibliotek.
"Out-of-the-Box" fungerer ikke biblioteket som tiltenkt, slik at noen tiltak må gjøres for å få ting til å fungere.

## Steg 1:

Sett opp ett nytt Svelte prosjekt, med TypeScript, som vist.

```
npm create vite@latest <PROJECT NAME> -- --template svelte-ts
```

![Alt text](src/assets/setup.png)

## Steg 2:

Endre Svelte versjonen til `^3.59.2` som vist under (STAF komponentene baserer seg på en eldre versjon av Svelte).

![Alt text](src/assets/changeSvelteVersion.png)

## Steg 3:

Installer STAF komponentene ved å kjøre:

```
npm install --save svelte @statsforvalteren/staf-komponentbibliotek-svelte
```

## Steg 4:

Inkluder følgende CSS-fil i root-en av prosjektet, f.eks. i `main.ts` eller `App.svelte`, for å få med styling på alle komponetene:

```
import "@statsforvalteren/staf-komponentbibliotek-svelte/src/custom.css";
```
