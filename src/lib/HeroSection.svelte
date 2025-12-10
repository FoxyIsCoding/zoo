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
		padding: clamp(40px, 8vw, 60px) clamp(16px, 4vw, 20px);
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

	@media (max-width: 640px) {
		.hero {
			min-height: 50vh;
			padding: clamp(30px, 6vw, 50px) clamp(12px, 3vw, 20px);
		}

		h1 {
			font-size: clamp(2rem, 7vw, 4rem);
		}

		.subtitle {
			font-size: clamp(0.9rem, 2.5vw, 1.3rem);
		}
	}
</style>
