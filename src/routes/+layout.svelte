<script lang="ts">
	import './layout.css';
	import Zoo from '$lib/zoo.svelte';

	let { children } = $props();
</script>

<Zoo />

{@render children()}
