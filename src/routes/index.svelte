<script>
	import Danfojs from '$lib/Danfojs.svelte';
	import MainWebsite from './MainWebsite.svelte';
</script>

<Danfojs let:dfd>
	<MainWebsite {dfd} />
</Danfojs>
