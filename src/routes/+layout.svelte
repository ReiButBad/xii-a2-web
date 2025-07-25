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

<style>
	:global(body) { 
        background-image: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.8)), url("/bg.webp");
        background-repeat: no-repeat;
        background-attachment: fixed;
        background-position: center;
        background-size: cover;
	}
</style>