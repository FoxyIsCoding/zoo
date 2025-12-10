<script lang="ts">
	type Props = {
		onRestart: () => void;
	};

	let { onRestart }: Props = $props();
</script>

<div class="dead-screen">
	<div class="dead-content">
		<div class="skull">💀</div>
		<h2>Your shark has died</h2>
		<p>You didn't feed them in time...</p>
		<button class="restart-button" onclick={onRestart}>Try Again</button>
	</div>
</div>

<style>
	.dead-screen {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		background: rgba(0, 0, 0, 0.9);
		display: flex;
		align-items: center;
		justify-content: center;
		z-index: 1000;
		animation: fadeIn 0.5s ease;
	}

	@keyframes fadeIn {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}

	.dead-content {
		text-align: center;
		color: white;
		animation: slideUp 0.6s ease;
	}

	@keyframes slideUp {
		from {
			transform: translateY(30px);
			opacity: 0;
		}
		to {
			transform: translateY(0);
			opacity: 1;
		}
	}

	.skull {
		font-size: clamp(4rem, 10vw, 6rem);
		margin-bottom: 20px;
		animation: float 3s ease-in-out infinite;
	}

	@keyframes float {
		0%,
		100% {
			transform: translateY(0);
		}
		50% {
			transform: translateY(-15px);
		}
	}

	h2 {
		font-size: clamp(1.8rem, 5vw, 2.5rem);
		font-weight: 700;
		margin: 0 0 12px 0;
		color: #ff4757;
	}

	p {
		font-size: clamp(1rem, 2.5vw, 1.2rem);
		margin: 0 0 30px 0;
		color: #cbd5e0;
	}

	.restart-button {
		background: #48bb78;
		color: white;
		border: none;
		padding: clamp(12px, 2.5vw, 16px) clamp(28px, 5vw, 40px);
		border-radius: 12px;
		font-size: clamp(0.9rem, 2vw, 1.1rem);
		font-weight: 600;
		cursor: pointer;
		transition: all 0.2s ease;
		box-shadow: 0 4px 12px rgba(72, 187, 120, 0.3);
	}

	.restart-button:hover {
		background: #38a169;
		transform: translateY(-2px);
		box-shadow: 0 6px 16px rgba(72, 187, 120, 0.4);
	}
</style>
