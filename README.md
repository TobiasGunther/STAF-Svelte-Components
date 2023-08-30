# Hvordan få STAF sitt Svelte komponentbibliotektet til å fungere

Dette repoet inneholder info rundt oppsett at et nytt Svelte prosjekt som benytter STAF sitt eksisterende Svelte komponentbibliotek.
"Out-of-the-Box" fungerer ikke biblioteket som tiltenkt, slik at noen tiltak må gjøres for å få ting til å fungere.

## Steg 1:

Sett opp ett nytt Svelte prosjekt, med TypeScript, som vist.

![Alt text](static/setup.png)

## Steg 2:

Endre Svelte versjonen til `^3.59.2` som vist under (STAF komponentene baserer seg på en eldre versjon av Svelte).

![Alt text](static/changeSvelteVersion.png)

## Steg 3:

Installer STAF komponentene ved å kjøre:

```
npm install --save svelte @statsforvalteren/staf-komponentbibliotek-svelte
```

## Steg 4:

Slik npm-pakken til STAF komponentene er satt opp per dags dato vil de ikke få med noe styling. Derfor må en ekstra bootstrap-theme også installeres.
Kjør følgende kommando:

```
npm install @netlifedesign/fmfa-bootstrap-theme
```

## _Steg 5 (optional):_

Hvis du får masse feilmeldinger i `.svelte` filer installer følgende pakke og konfigurer `svelte.config.ts` som vist.

```
npm i @sveltejs/adapter-auto
```

![Alt text](static/svelteConfig.png)

## Steg 6:

Noen av STAF komponentene bruker node_module `@popperjs/core` som sørger for trøbble for å løse problemene relatert til denne modulen endre `vite.config.ts` som vist.
Dette krever at følgende kommando kjøres først:

```
npm i @sveltejs/kit/vite
```

![Alt text](static/viteConfig.png)

## Steg 7:

Legg til en av STAF komponentene inn i prosjektet. Koden under er for en Modal.

```
<script lang="ts">
	import {
		Button,
		Modal,
		ModalBody,
		ModalFooter,
		ModalHeader
	} from '@statsforvalteren/staf-komponentbibliotek-svelte';
	let open = false;
	const toggle = () => (open = !open);
	import '@netlifedesign/fmfa-bootstrap-theme/custom.css';
</script>

<div>
	<Button color="danger" on:click={toggle}>Open Modal</Button>
	<Modal isOpen={open} {toggle}>
		<ModalHeader {toggle}>Modal title</ModalHeader>
		<ModalBody>
			Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut
			labore et dolore magna aliqua.
		</ModalBody>
		<ModalFooter>
			<Button color="primary" on:click={toggle}>Do Something</Button>
			<Button color="secondary" on:click={toggle}>Cancel</Button>
		</ModalFooter>
	</Modal>
</div>
```

**Husk å inkluder `import '@netlifedesign/fmfa-bootstrap-theme/custom.css'` for å få med styling. Denne importen kan også bare inkluderes i root komponenten hvor den deretter gjelder for alle children.**
**Husk å import STAF komponenter ved å bruke `@statsforvalteren/staf-komponentbibliotek-svelte`.**

## Steg 8:

Kjør applikasjonen ved å kjøre:

```
npm run dev
```

## _Steg 9 (optional):_

Hvis du får feilmelding/varsel i terminalen som vist på bildet under endre `tsconfig.json` som vist i det andre bilde.

![Alt text](static/tsconfigWarning.png)

![Alt text](static/tsconfig.png)
