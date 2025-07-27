<script lang="ts">
	import '../app.css';
	import "overlayscrollbars/overlayscrollbars.css"
	import { OverlayScrollbars } from 'overlayscrollbars';
	import { onMount } from 'svelte';
	let { children } = $props();

	onMount(() => {
		const osInstance = OverlayScrollbars(document.querySelector('body') as HTMLBodyElement, {
			overflow: {
				y: "visible-hidden"
			}
		});
	})
</script>

{@render children()}