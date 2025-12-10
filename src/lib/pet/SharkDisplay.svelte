<script lang="ts">
	type Props = {
		currentImage: string;
		showHungryBubble: boolean;
		isEating: boolean;
	};

	let { currentImage, showHungryBubble, isEating }: Props = $props();
</script>

<div class="shark-room">
	<div class="shark-display">
		{#if showHungryBubble && !isEating}
			<div class="speech-bubble">I'm hungry &gt;:3</div>
		{/if}

		<img src={currentImage} alt="Shark pet" class="shark-image" class:eating={isEating} />
	</div>
</div>

<style>
	.shark-room {
		width: 100%;
		max-width: 450px;
		background: linear-gradient(180deg, #2c386769 0%, #033a5755 100%);
		border-radius: 16px;
		padding: clamp(30px, 5vw, 50px) clamp(20px, 4vw, 30px);
		box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
		position: relative;
	}

	.shark-room::before {
		content: '';
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		height: 40%;
		background: linear-gradient(180deg, transparent 0%, rgba(0, 123, 255, 0.1) 100%);
		border-radius: 0 0 16px 16px;
		pointer-events: none;
	}

	.shark-display {
		position: relative;
		width: 100%;
		max-width: 120px;
		margin: 0 auto;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.shark-image {
		width: 100%;
		height: auto;
		transition: transform 0.2s ease;
		position: relative;
		z-index: 1;
	}

	.shark-image.eating {
		animation: bounce 0.5s ease infinite;
	}

	@keyframes bounce {
		0%,
		100% {
			transform: translateY(0);
		}
		50% {
			transform: translateY(-8px);
		}
	}

	.speech-bubble {
		position: absolute;
		top: -50px;
		left: 50%;
		transform: translateX(-50%);
		background: white;
		color: #2d3748;
		padding: 10px 16px;
		border-radius: 12px;
		font-weight: 600;
		font-size: clamp(0.85rem, 1.8vw, 0.95rem);
		animation: float 2s ease-in-out infinite;
		white-space: nowrap;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.12);
		z-index: 2;
	}

	.speech-bubble::after {
		content: '';
		position: absolute;
		bottom: -8px;
		left: 50%;
		transform: translateX(-50%);
		width: 0;
		height: 0;
		border-left: 8px solid transparent;
		border-right: 8px solid transparent;
		border-top: 8px solid white;
	}

	@keyframes float {
		0%,
		100% {
			transform: translateX(-50%) translateY(0);
		}
		50% {
			transform: translateX(-50%) translateY(-6px);
		}
	}

	@media (max-width: 640px) {
		.shark-room {
			padding: clamp(20px, 4vw, 40px) clamp(16px, 3vw, 24px);
		}
	}
</style>
