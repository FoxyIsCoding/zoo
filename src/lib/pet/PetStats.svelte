<script lang="ts">
	type Props = {
		health: number;
		hunger: number;
	};

	let { health, hunger }: Props = $props();
</script>

<div class="stats-container">
	<div class="stat-bar">
		<div class="stat-label">
			<span>Health</span>
			<span class="stat-value">{Math.round(health)}%</span>
		</div>
		<div class="bar">
			<div class="bar-fill health" style="width: {health}%"></div>
		</div>
	</div>

	<div class="stat-bar">
		<div class="stat-label">
			<span>Hunger</span>
			<span class="stat-value">{Math.round(hunger)}%</span>
		</div>
		<div class="bar">
			<div class="bar-fill hunger" style="width: {hunger}%"></div>
		</div>
	</div>
</div>

<style>
	.stats-container {
		width: 100%;
		max-width: 400px;
		display: flex;
		flex-direction: column;
		gap: 14px;
	}

	.stat-bar {
		background: white;
		padding: 14px 16px;
		border-radius: 12px;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
	}

	.stat-label {
		display: flex;
		justify-content: space-between;
		margin-bottom: 8px;
		font-weight: 600;
		font-size: clamp(0.85rem, 1.8vw, 0.95rem);
		color: #2d3748;
	} 

	.stat-value {
		color: #718096;
	}

	.bar {
		height: 18px;
		background: #e2e8f0;
		border-radius: 9px;
		overflow: hidden;
	}

	.bar-fill {
		height: 100%;
		transition: width 0.5s ease;
		border-radius: 9px;
	}

	.bar-fill.health {
		background: #48bb78;
	}

	.bar-fill.hunger {
		background: #f6ad55;
	}
</style>
