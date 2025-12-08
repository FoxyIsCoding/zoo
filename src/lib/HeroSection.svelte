<script lang="ts">
	interface Props {
		title: string;
		subtitle?: string;
	}
	
	let { title, subtitle }: Props = $props();
</script>

<section class="hero">
	<div class="hero-content">
		<h1>{title}</h1>
		{#if subtitle}
			<p class="subtitle">{subtitle}</p>
		{/if}
	</div>
</section>

<style>
	.hero {
		background: linear-gradient(180deg, #0E4D92 0%, #1B9AAA 100%);
		min-height: 60vh;
		display: flex;
		align-items: center;
		justify-content: center;
		text-align: center;
		padding: 60px 20px;
		color: white;
	}

	.hero-content {
		max-width: 1200px;
	}

	h1 {
		font-size: clamp(3rem, 8vw, 7rem);
		font-weight: 900;
		margin: 0;
		line-height: 1.1;
		text-transform: uppercase;
		letter-spacing: -0.02em;
	}

	.subtitle {
		font-size: clamp(1.2rem, 3vw, 2rem);
		margin-top: 20px;
		opacity: 0.95;
	}
</style>
