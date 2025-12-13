<script lang="ts">
	import { onMount, onDestroy } from 'svelte';
	import type { PageProps } from './$types.js';
	import PetStats from '$lib/pet/PetStats.svelte';
	import SharkDisplay from '$lib/pet/SharkDisplay.svelte';
	import PetControls from '$lib/pet/PetControls.svelte';
	import DeadScreen from '$lib/pet/DeadScreen.svelte';
	import defaultImg from '$lib/../assets/interactive/low quality/1.png?url';
	import sadImg from '$lib/../assets/interactive/low quality/sad.png?url';
	import eatingImg from '$lib/../assets/interactive/low quality/vege.png?url';
	import slepImg from '$lib/../assets/interactive/low quality/slep.png?url';
	import dreamImg from '$lib/../assets/interactive/low quality/dream.png?url';
	import sillyImg from '$lib/../assets/interactive/low quality/silly.png?url';
	import love1Img from '$lib/../assets/interactive/low quality/love1.png?url';
	import loveImg from '$lib/../assets/interactive/low quality/love.png?url';

	let { data }: PageProps = $props();

	const images = {
		default: defaultImg,
		sad: sadImg,
		eating: eatingImg,
		slep: slepImg,
		dream: dreamImg,
		silly: sillyImg,
		love1: love1Img,
		love: loveImg
	};

	

	const getInitialImage = () => {
		const currentHour = new Date().getHours();
		return currentHour >= 21 ? images.slep : images.default;
	};

	let health = $state(100);
	let hunger = $state(0);
	let currentImage = $state(getInitialImage());
	let showHungryBubble = $state(false);
	let isEating = $state(false);
	let isDead = $state(false);
	let isPetting = $state(false);

	const derived_hungerPercent = $derived(hunger);
	const derived_healthPercent = $derived(health);
	const derived_isHungry = $derived(hunger >= 60);

	let hungerInterval: ReturnType<typeof setInterval> | null = null;
	let eatingTimeout: ReturnType<typeof setTimeout> | null = null;
	let pettingTimeout: ReturnType<typeof setTimeout> | null = null;

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
			currentImage = hunger >= 60 ? images.sad : getInitialImage();
		}, 2500);
	};

	const petShark = () => {
		if (isPetting || isEating || isDead) return;

		isPetting = true;
		showHungryBubble = false;

		const randomValue = Math.random();
		if (randomValue < 0.5) {
			currentImage = images.dream;
		} else {
			const otherImages = [images.silly, images.love1, images.love];
			const randomImage = otherImages[Math.floor(Math.random() * otherImages.length)];
			currentImage = randomImage;
		}

		pettingTimeout = setTimeout(() => {
			isPetting = false;
			currentImage = hunger >= 60 ? images.sad : getInitialImage();
		}, 2000);
	};	
	const restartGame = () => {
		health = 100;
		hunger = 0;
		isDead = false;
		currentImage = getInitialImage();
		showHungryBubble = false;
		isEating = false;
		isPetting = false;
		startHungerTimer();
	};

	const stopTimers = () => {
		if (hungerInterval) clearInterval(hungerInterval);
		if (eatingTimeout) clearTimeout(eatingTimeout);
		if (pettingTimeout) clearTimeout(pettingTimeout);
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

	<SharkDisplay {currentImage} {showHungryBubble} {isEating} onPet={petShark} {isPetting} />

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
