<script lang="ts">
	interface Props {
		speed?: number;
	}
	
	let { speed = 35 }: Props = $props();
</script>

<section class="mynts-section">
	<div class="container">
		<div class="mynts-icon">🏊</div>
		<h2>Shark Speed</h2>
		<p class="description">Sharks are some of the fastest swimmers in the ocean! Different species have different top speeds.</p>
		<div class="conversion">
			<span class="rate">Great White: {speed} MPH</span>
		</div>
		<h3>How fast can sharks swim?</h3>
		<p>🦈 Shortfin Mako: 60 mph (fastest!) | 🦈 Great White: 35 mph | 🦈 Tiger Shark: 20 mph</p>
	</div>
</section>

<style>
	.mynts-section {
		background: linear-gradient(135deg, #ffd93d 0%, #ffb800 100%);
		padding: 80px 20px;
		text-align: center;
		color: #1f2d3d;
	}

	.container {
		max-width: 800px;
		margin: 0 auto;
	}

	.mynts-icon {
		font-size: 5rem;
		margin-bottom: 20px;
	}

	h2 {
		font-size: clamp(2.5rem, 5vw, 4rem);
		font-weight: 900;
		margin: 0 0 20px 0;
	}

	h3 {
		font-size: clamp(1.5rem, 3vw, 2.5rem);
		font-weight: 800;
		margin: 40px 0 20px 0;
	}

	.description {
		font-size: 1.3rem;
		line-height: 1.6;
		margin: 20px 0;
	}

	.conversion {
		background: rgba(255, 255, 255, 0.5);
		padding: 20px 40px;
		border-radius: 50px;
		display: inline-block;
		margin: 30px 0;
	}

	.rate {
		font-size: 1.8rem;
		font-weight: 800;
		color: #1f2d3d;
	}

	p {
		font-size: 1.2rem;
		line-height: 1.7;
	}
</style>
