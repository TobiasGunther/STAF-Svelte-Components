<script lang="ts">
	import { Test } from '$lib';
	let test: string = 'value';
	let tags: string = '<h1>test</h1>';

	const props = {
		count: 69,
		value: 'nice'
	};
</script>

<h1>Welcome to SvelteKit</h1>
<p>{test}</p>
<p>{@html tags}</p>

<Test {...props} />
