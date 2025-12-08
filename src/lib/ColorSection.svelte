<script lang="ts">
	interface Props {
		bg: string;
		emoji?: string;
		textColor?: string;
		children?: any;
	}
	
	let { bg, emoji, textColor = 'white', children }: Props = $props();
</script>

<section class="color-section" style="background-color: {bg}; color: {textColor};">
	{#if emoji}
		<div class="emoji">{emoji}</div>
	{/if}
	{@render children?.()}
</section>

<style>
	.color-section {
		padding: 60px 20px;
		text-align: center;
		min-height: 300px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.emoji {
		font-size: 5em;
		margin-bottom: 20px;
	}

	:global(.color-section h2) {
		font-size: 2.5em;
		margin-bottom: 20px;
	}

	:global(.color-section p) {
		font-size: 1.3em;
		max-width: 700px;
		margin: 10px auto;
	}
</style>
