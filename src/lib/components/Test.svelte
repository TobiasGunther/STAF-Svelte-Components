<script lang="ts">
	export let count: number = 0;
	export let value: string;
	const colors: string[] = ['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet'];
	let selected: string = colors[0];
	let name: string = 'world';
	$: doubled = count * 2;
	$: if (doubled >= 500) {
		doubled = 0;
	}

	function increment() {
		count += 1;
	}

	let numbers = [1, 2, 3, 4];

	function addNumber() {
		numbers = [...numbers, numbers.length + 1];
	}

	$: sum = numbers.reduce((total, currentNumber) => total + currentNumber, 0);

	let m = { x: 0, y: 0 };
</script>

<button on:click={increment}>
	Clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>

<p>{count} doubled is {doubled}</p>
{#if count > 10}
	<p>{count} is greater than 10.</p>
{:else}
	<p>{count} is less than or equal to 10</p>
{/if}
<p style="color: {selected}">{numbers.join(' + ')} = {sum}</p>

<button on:click={addNumber}> Add a number </button>

<button on:click|once={() => alert('clicked')}> Click me </button>

<h3>{value}</h3>

<h1 style="color: {selected}">Pick a colour</h1>

<input bind:value={name} />

<h1>Hello {name}!</h1>

<div>
	{#each colors as color, i}
		<button
			aria-current={selected === color}
			aria-label={color}
			style="background: {color}"
			on:click={() => (selected = color)}>{i + 1}</button
		>
	{/each}
</div>
<div
	on:pointermove={(e) => {
		m = { x: e.clientX, y: e.clientY };
	}}
	class="cursor"
>
	The pointer is at {m.x} x {m.y}
</div>

<style>
	h1 {
		transition: color 0.2s;
	}

	div {
		display: grid;
		grid-template-columns: repeat(7, 1fr);
		grid-gap: 5px;
		max-width: 400px;
	}

	button {
		aspect-ratio: 1;
		border-radius: 50%;
		background: var(--color, #fff);
		transform: translate(-2px, -2px);
		filter: drop-shadow(2px 2px 3px rgba(0, 0, 0, 0.2));
		transition: all 0.1s;
	}

	button[aria-current='true'] {
		transform: none;
		filter: none;
		box-shadow: inset 3px 3px 4px rgba(0, 0, 0, 0.2);
	}
	.cursor {
		position: fixed;
		right: 0;
		top: 0;
		width: 500px;
		height: 500px;
		padding: 1rem;
	}
</style>
