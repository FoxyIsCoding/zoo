<script lang="ts">
	import { onMount } from 'svelte';

	interface Props {
		speed?: number;
	}
	
	let { speed = 35 }: Props = $props();
	let useKmh = $state(false);

	const mphToKmh = (mph: number) => Math.round(mph * 1.60934);

	const toggleUnit = () => {
		useKmh = !useKmh;
		document.cookie = `speedUnit=${useKmh ? 'kmh' : 'mph'}; path=/; max-age=31536000`;
	};

	const convertSpeed = (mph: number) => (useKmh ? mphToKmh(mph) : mph);
	const unit = $derived(useKmh ? 'KMH' : 'MPH');

	onMount(() => {
		const cookies = document.cookie.split(';').reduce((acc, cookie) => {
			const [key, value] = cookie.trim().split('=');
			acc[key] = value;
			return acc;
		}, {} as Record<string, string>);

		if (cookies.speedUnit === 'kmh') {
			useKmh = true;
		}
	});
</script>

<section class="mynts-section">
	<div class="container">
		<div class="mynts-icon">🏊</div>
		<h2>Shark Speed :o</h2>
		<p class="description">Sharks are some of the fastest swimmers in the ocean!</p>
		<button class="conversion" onclick={toggleUnit}>
			<span class="rate">Great White: {convertSpeed(speed)} {unit}</span>
		</button>
		<h3>How fast can sharks swim?</h3>
		<p>🦈 Shortfin Mako: {convertSpeed(60)} {unit.toLowerCase()} (fastest!) | 🦈 Great White: {convertSpeed(35)} {unit.toLowerCase()} | 🦈 Tiger Shark: {convertSpeed(20)} {unit.toLowerCase()}</p>
	</div>
</section>

<style>
	.mynts-section {
		background: linear-gradient(135deg, #ffd93d 0%, #ffb800 100%);
		padding: clamp(48px, 8vw, 80px) clamp(16px, 6vw, 28px);
		text-align: center;
		color: #1f2d3d;
	}

	.container {
		max-width: 800px;
		margin: 0 auto;
	}

	.mynts-icon {
		font-size: clamp(3rem, 12vw, 5rem);
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
		font-size: clamp(1rem, 3vw, 1.3rem);
		line-height: 1.6;
		margin: 20px 0;
	}

	.conversion {
		background: rgba(255, 255, 255, 0.5);
		padding: clamp(14px, 4vw, 20px) clamp(24px, 6vw, 40px);
		border-radius: 999px;
		display: inline-block;
		margin: 30px 0;
		border: 2px solid transparent;
		width: min(420px, 100%);
		cursor: pointer;
		transition: all 0.2s ease;
	}

	.conversion:hover {
		background: rgba(255, 255, 255, 0.7);
		border-color: #1f2d3d;
		transform: scale(1.05);
	}

	.rate {
		font-size: clamp(1.2rem, 4vw, 1.8rem);
		font-weight: 800;
		color: #1f2d3d;
	}

	p {
		font-size: clamp(1rem, 3.2vw, 1.2rem);
		line-height: 1.7;
	}

	@media (max-width: 640px) {
		h3 {
			margin: 28px 0 16px 0;
		}

		.conversion {
			margin: 22px auto;
		}

		p {
			line-height: 1.6;
		}
	}
</style>
