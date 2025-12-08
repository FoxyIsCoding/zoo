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
		margin-bottom: 10px;
	}

	.faq-question {
		width: 100%;
		padding: 25px 20px;
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
		font-size: 1.4rem;
		font-weight: 700;
		margin: 0;
		color: #1f2d3d;
		flex: 1;
	}

	.icon {
		font-size: 32px;
		color: #ec3750;
		transition: transform 0.3s;
	}

	.faq-answer {
		padding: 0 20px 30px 20px;
		animation: slideDown 0.3s ease-out;
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

	p {
		font-size: 1.2rem;
		line-height: 1.7;
		color: #555;
		margin: 0;
	}
</style>
