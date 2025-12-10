<script lang="ts">
	import { onMount, onDestroy } from 'svelte';
	import type { PageProps } from './$types.js';
	import PetStats from '$lib/pet/PetStats.svelte';
	import SharkDisplay from '$lib/pet/SharkDisplay.svelte';
	import PetControls from '$lib/pet/PetControls.svelte';
	import DeadScreen from '$lib/pet/DeadScreen.svelte';

	let { data }: PageProps = $props();

	const images = {
		default: '/src/assets/interactive/low quality/1.png',
		sad: '/src/assets/interactive/low quality/sad.png',
		eating: '/src/assets/interactive/low quality/vege.png'
	};

	let health = $state(100);
	let hunger = $state(0);
	let currentImage = $state(images.default);
	let showHungryBubble = $state(false);
	let isEating = $state(false);
	let isDead = $state(false);

	const derived_hungerPercent = $derived(hunger);
	const derived_healthPercent = $derived(health);
	const derived_isHungry = $derived(hunger >= 60);

	let hungerInterval: ReturnType<typeof setInterval> | null = null;
	let eatingTimeout: ReturnType<typeof setTimeout> | null = null;

	const startHungerTimer = () => {
		hungerInterval = setInterval(() => {
			if (isDead) return;

			if (hunger < 100) {
				hunger = Math.min(100, hunger + 5);
			}

			if (hunger >= 80 && health > 0) {
				health = Math.max(0, health - 2);
			}

			if (health <= 0) {
				isDead = true;
				stopTimers();
			}

			if (hunger >= 60) {
				showHungryBubble = true;
				currentImage = images.sad;
			}
		}, 3000);
	};


	const feedShark = () => {
		if (isEating || isDead) return;

		isEating = true;
		currentImage = images.eating;
		showHungryBubble = false;

		
		hunger = Math.max(0, hunger - 40);
		health = Math.min(100, health + 20);

		
		eatingTimeout = setTimeout(() => {
			isEating = false;
			currentImage = hunger >= 60 ? images.sad : images.default;
		}, 2500);
	};

	
	const restartGame = () => {
		health = 100;
		hunger = 0;
		isDead = false;
		currentImage = images.default;
		showHungryBubble = false;
		isEating = false;
		startHungerTimer();
	};

	const stopTimers = () => {
		if (hungerInterval) clearInterval(hungerInterval);
		if (eatingTimeout) clearTimeout(eatingTimeout);
	};

	onMount(() => {
		startHungerTimer();
	});

	onDestroy(() => {
		stopTimers();
	});
</script>

<div class="pet-container">
	<div class="pet-header">
		<h1>shork petcare :3</h1>
		<p class="subtitle">take care of your shark friend</p>
	</div>

	<PetStats health={derived_healthPercent} hunger={derived_hungerPercent} />

	<SharkDisplay {currentImage} {showHungryBubble} {isEating} />

	<PetControls onFeed={feedShark} {isEating} />

	{#if isDead}
		<DeadScreen onRestart={restartGame} />
	{/if}
</div>

<style>
	.pet-container {
		min-height: 100vh;
		background: #e7f2ff;
		padding: clamp(30px, 5vw, 60px) clamp(20px, 4vw, 40px);
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: clamp(20px, 4vw, 30px);
	}

	.pet-header {
		text-align: center;
	}

	.pet-header h1 {
		font-size: clamp(1.8rem, 4vw, 2.8rem);
		font-weight: 700;
		margin: 0 0 8px 0;
		color: #1a202c;
	}

	.subtitle {
		font-size: clamp(0.9rem, 2vw, 1.1rem);
		color: #4a5568;
		margin: 0;
	}

	@media (max-width: 640px) {
		.pet-container {
			gap: clamp(16px, 3vw, 24px);
		}
	}
</style>
