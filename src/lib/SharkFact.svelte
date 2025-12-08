<script lang="ts">
	import { onMount } from 'svelte';
	
	let fact = $state('Loading shark wisdom...');
	let loading = $state(true);

	async function fetchSharkFact() {
		loading = true;
		try {
			const sillyFacts = [
				"Sharks can't stop swimming or they'll sink... kinda like me with coffee ",
				"Baby sharks are called pups. Adult sharks are called 'sir' or 'ma'am' ",
				"Sharks have been around for 400 million years and still haven't learned to use smartphones ",
				"A shark's favorite game? Swallow the leader! ",
				"Sharks lose about 30,000 teeth in their lifetime. The tooth fairy owes them BIG TIME ",
				"Some sharks glow in the dark. They're basically underwater disco balls ",
				"Hammerhead sharks can get a tan. No really, they do! ",
				"Sharks have no bones. They're 100% cartilage and 100% vibes "
			];
			
			fact = sillyFacts[Math.floor(Math.random() * sillyFacts.length)];
		} catch (error) {
			fact = "Error: Shark ate the internet connection :( ";
		}
		loading = false;
	}

	onMount(() => {
		fetchSharkFact();
	});
</script>

<div class="shark-fact">
	<div class="emoji">🦈</div>
	<p>{fact}</p>
	<button onclick={fetchSharkFact} disabled={loading}>
		{loading ? '🌊 Swimming...' : '🦈 Get Another Fact'}
	</button>
</div>

<style>
	.shark-fact {
		padding: 30px;
		background: #FFD93D;
		border-radius: 15px;
		text-align: center;
		margin: 20px;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
	}

	.emoji {
		font-size: 4em;
		margin-bottom: 15px;
	}

	p {
		font-size: 1.3em;
		color: #2d3436;
		margin: 20px 0;
		line-height: 1.6;
	}

	button {
		background: #6BCF7F;
		color: white;
		border: none;
		padding: 12px 24px;
		font-size: 1.1em;
		border-radius: 25px;
		cursor: pointer;
		transition: all 0.3s;
		font-weight: bold;
	}

	button:hover:not(:disabled) {
		background: #55B56A;
		transform: scale(1.05);
	}

	button:disabled {
		opacity: 0.6;
		cursor: not-allowed;
	}
</style>
