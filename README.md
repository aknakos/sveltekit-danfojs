# Simple danfojs wrapper for svelte

Simple implementation of a wrapper for danfo.js which works with sveltekit.
Normally, I'd prefer to build it within sveltekit, but as of now I was unable to do so. This library uses danfojs' CDN, which means all code which requires it will be CSR (and not SSR).
I made this to easily reuse the logic, but feel free to copy the code in the .svelte file to customize however you want and/or if you don't want to install a dependency only for this.

You can use this library in a couple of ways.
Usage 1:

```javascript
//index.svelte
<script>
	import Danfojs from '@aknakos/sveltekit-danfojs/Danfojs.svelte';
	import Inner from './Inner.svelte';
</script>

<Danfojs let:dfd>
	<Inner {dfd} />
</Danfojs>

//Inner.svelte
<script>
	export let dfd;

	let s = new dfd.Series([1, 2, 3, 4, 5]);
	s.print();
</script>
```

Usage 2:

```javascript
//index.svelte
<script>
	import Danfojs from '@aknakos/sveltekit-danfojs/Danfojs.svelte';
	import Inner from './Inner.svelte';
</script>

<Danfojs>
	<Inner />
</Danfojs>

//Inner.svelte
<script>
	import { dfd } from '@aknakos/sveltekit-danfojs/store.js';

	let s = new $dfd.Series([1, 2, 3, 4, 5]); // Note this is in a store format now
	s.print();
</script>
```
