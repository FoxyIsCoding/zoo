<script lang="ts">
	import './layout.css';
	import Zoo from '$lib/zoo.svelte';
	let { children } = $props();
</script>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200&icon_names=pets" />

<Zoo />

{@render children()}
