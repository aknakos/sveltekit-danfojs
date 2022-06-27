<script lang="ts">
	import { browser } from '$app/env';
	import { dfd } from './store.js';
	import { onMount } from 'svelte';

	onMount(async () => {
		if (browser && !$dfd) $dfd = window.dfd;
	});

	async function loaded() {
		if (!$dfd) $dfd = window.dfd;
	}
</script>

<svelte:head>
	<script
		src="https://cdn.jsdelivr.net/npm/danfojs@1.1.0/lib/bundle.min.js"
		on:load={loaded}></script>
</svelte:head>

{#if $dfd}
	<slot dfd={$dfd} />
{/if}
