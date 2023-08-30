<script lang="ts">
	import { Button } from '@statsforvalteren/staf-komponentbibliotek-svelte';
	const colors: any = [
		'primary',
		'secondary',
		'success',
		'danger',
		'warning',
		'info',
		'light',
		'dark'
	];
</script>

{#each colors as color}
	<div>
		<Button {color}>{color}</Button>
	</div>
{/each}
