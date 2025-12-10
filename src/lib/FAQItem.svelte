<script lang="ts">
	interface Props {
		question: string;
		answer: string;
	}
	
	let { question, answer }: Props = $props();
	let isOpen = $state(false);
	
	function toggle() {
		isOpen = !isOpen;
	}
</script>

<div class="faq-item">
	<button class="faq-question" onclick={toggle}>
		<h3>{question}</h3>
		<span class="icon material-symbols-outlined">
			{isOpen ? '▲' : '▼'}
		</span>
	</button>
	{#if isOpen}
		<div class="faq-answer">
			<p>{answer}</p>
		</div>
	{/if}
</div>

<style>
	.faq-item {
		border-bottom: 2px solid #e0e0e0;
		margin-bottom: clamp(8px, 2vw, 10px);
	}

	.faq-question {
		width: 100%;
		padding: clamp(16px, 3vw, 25px) clamp(16px, 3vw, 20px);
		background: none;
		border: none;
		text-align: left;
		cursor: pointer;
		display: flex;
		justify-content: space-between;
		align-items: center;
		transition: background 0.2s;
	}

	.faq-question:hover {
		background: #f5f5f5;
	}

	h3 {
		font-size: clamp(1rem, 2.5vw, 1.4rem);
		font-weight: 700;
		margin: 0;
		color: #1f2d3d;
		flex: 1;
		line-height: 1.3;
	}

	.icon {
		font-size: clamp(24px, 5vw, 32px);
		color: #ec3750;
		transition: transform 0.3s;
		flex-shrink: 0;
		margin-left: clamp(8px, 2vw, 12px);
	}

	.faq-answer {
		padding: 0 clamp(16px, 3vw, 20px) clamp(20px, 4vw, 30px) clamp(16px, 3vw, 20px);
		animation: slideDown 0.3s ease-out;
	}

	.faq-answer p {
		font-size: clamp(0.95rem, 2vw, 1.1rem);
		line-height: 1.6;
		color: #555;
		margin: 0;
	}

	@keyframes slideDown {
		from {
			opacity: 0;
			transform: translateY(-10px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	@media (max-width: 640px) {
		.faq-question {
			flex-direction: column;
			align-items: flex-start;
			gap: 12px;
		}

		.icon {
			align-self: flex-end;
			margin-left: auto;
			margin-right: 0;
		}
	}
</style>
