<script lang="ts">
	import { onMount } from 'svelte';
	
	let joke = $state('Loading a fin-tastic joke...');
	let loading = $state(true);

	async function fetchJoke() {
		loading = true;
		try {
			const response = await fetch('https://v2.jokeapi.dev/joke/Any?contains=shark&safe-mode');
			const data = await response.json();
			
			if (data.error) {
				throw new Error('No shark jokes found');
			}
			
			if (data.type === 'single') {
				joke = data.joke;
			} else {
				joke = `${data.setup}\n\n${data.delivery}`;
			}
		} catch (error) {
			const sharkJokes = [
				"What do you call a shark that works at a restaurant? A WAITER SHARK! Get it? 😂",
				"Why don't sharks like fast food? Because they can't catch it! 🍔💨",
				"What's a shark's favorite sci-fi show? Shark Trek! 🖖",
				"How do sharks greet each other? 'Pleased to eat you!' 🤝",
				"What do you get from a bad-tempered shark? As far away as possible! 🏃‍♂️",
				"Why did the shark cross the reef? To get to the other tide! 🌊",
				"What's a shark's favorite sandwich? Peanut butter and jellyfish! 🥜",
				"What do sharks order at McDonald's? A quarter-flounder with cheese! 🍔"
			];
			joke = sharkJokes[Math.floor(Math.random() * sharkJokes.length)];
		}
		loading = false;
	}

	onMount(() => {
		fetchJoke();
	});
</script>

<div class="shark-joke">
	<div class="emoji">😂</div>
	<h3>Shark Joke Time!</h3>
	<p>{joke}</p>
	<button onclick={fetchJoke} disabled={loading}>
		{loading ? '🌀 Searching...' : '🎭 Another Joke!'}
	</button>
</div>

<style>
	.shark-joke {
		padding: 30px;
		background: #FF6B9D;
		border-radius: 15px;
		text-align: center;
		margin: 20px;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
		color: white;
	}

	.emoji {
		font-size: 4em;
		margin-bottom: 10px;
	}

	h3 {
		font-size: 2em;
		margin-bottom: 15px;
	}

	p {
		font-size: 1.2em;
		margin: 20px 0;
		line-height: 1.8;
		white-space: pre-line;
	}

	button {
		background: white;
		color: #FF6B9D;
		border: none;
		padding: 12px 24px;
		font-size: 1.1em;
		border-radius: 25px;
		cursor: pointer;
		transition: all 0.3s;
		font-weight: bold;
	}

	button:hover:not(:disabled) {
		transform: scale(1.05);
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
	}

	button:disabled {
		opacity: 0.6;
		cursor: not-allowed;
	}
</style>
