<script lang="ts">
	type Props = {
		onFeed: () => void;
		isEating: boolean;
	};

	let { onFeed, isEating }: Props = $props();
</script>

<div class="controls">
	<button class="feed-button" onclick={onFeed} disabled={isEating}>
		{isEating ? 'Eating...' : 'Feed Shark'}
	</button>
</div>

<style>
	.controls { 
		display: flex;
		justify-content: center;
	}   

	.feed-button {
		background: #3182ce;
		color: white;
		border: none;
		padding: clamp(12px, 2.5vw, 16px) clamp(28px, 5vw, 40px);
		border-radius: 12px;
		font-size: clamp(0.9rem, 2vw, 1.1rem);
		font-weight: 600;
		cursor: pointer;
		transition: all 0.2s ease;
		box-shadow: 0 4px 12px rgba(49, 130, 206, 0.3);
	}

	.feed-button:hover:not(:disabled) {
		background: #2c5aa0;
		transform: translateY(-2px);
		box-shadow: 0 6px 16px rgba(49, 130, 206, 0.4);
	}

	.feed-button:disabled {
		opacity: 0.6;
		cursor: not-allowed;
	}
</style>
  



