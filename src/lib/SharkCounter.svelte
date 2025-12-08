<script lang="ts">
	let sharkCount = $state(0);
	let sharkEmojis = $state('');

	function addShark() {
		sharkCount++;
		sharkEmojis += '🦈';
	}

	function resetSharks() {
		sharkCount = 0;
		sharkEmojis = '';
	}
</script>

<div class="shark-counter">
	<h3>How Many Sharks?</h3>
	<div class="count">
		<span class="number">{sharkCount}</span>
		<span class="label">Sharks!</span>
	</div>
	<div class="sharks-display">{sharkEmojis || '🌊'}</div>
	<div class="buttons">
		<button onclick={addShark}>🦈 Add a Shark!</button>
		<button onclick={resetSharks} class="reset">🔄 Reset Ocean</button>
	</div>
</div>

<style>
	.shark-counter {
		padding: 40px;
		background: #4ECDC4;
		border-radius: 15px;
		text-align: center;
		margin: 20px;
		color: white;
	}

	h3 {
		font-size: 2em;
		margin-bottom: 20px;
	}

	.count {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin: 20px 0;
	}

	.number {
		font-size: 4em;
		font-weight: bold;
	}

	.label {
		font-size: 1.5em;
	}

	.sharks-display {
		font-size: 2em;
		min-height: 80px;
		margin: 20px 0;
		overflow-wrap: break-word;
		word-break: break-all;
	}

	.buttons {
		display: flex;
		gap: 15px;
		justify-content: center;
		flex-wrap: wrap;
	}

	button {
		background: white;
		color: #4ECDC4;
		border: none;
		padding: 12px 24px;
		font-size: 1.1em;
		border-radius: 25px;
		cursor: pointer;
		transition: all 0.3s;
		font-weight: bold;
	}

	button:hover {
		transform: scale(1.05);
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
	}

	.reset {
		background: #FF6B9D;
		color: white;
	}
</style>
