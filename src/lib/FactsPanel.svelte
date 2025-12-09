<script lang="ts">
	import { onMount, onDestroy } from 'svelte';

	type Fact = { title: string; text: string };

	const defaultFacts: Fact[] = [
		{
			title: 'Ancient Survivors',
			text: 'Sharks have existed for over 400 million years more than trees and dinosaurs :3'
		},
		{
			title: 'Tooth Factory',
			text: 'A shark can grow and shed tens of thousands of teeth in its lifetime :p'
		},
		{
			title: 'Super Sensors',
			text: 'Did ya know that "Ampullae of Lorenzini" let sharks detect tiny electric signals from other animals.'
		},
		{
			title: 'Speed Demons',
			text: 'The shortfin mako can burst to roughly 60 mph, making it the fastest shark. :3'
		},
		{
			title: 'Ocean Navigators',
			text: 'Some sharks migrate thousands of miles each year, guided by Earth’s magnetic field.'
		}
	];

	const { facts: incomingFacts = defaultFacts, intervalMs = 4200 } = $props<{
		facts?: Fact[];
		intervalMs?: number;
	}>();

	const facts = $derived(incomingFacts);
	let active = $state(0);
	let progress = $state(0);
	let isVisible = $state(true);
	let visited = $state<boolean[]>([]);

	const resetVisited = () => {
		visited = facts.map((_: Fact, i: number) => i === 0);
	};

	const visitedCount = $derived(visited.filter(Boolean).length);
	const completed = $derived(visitedCount >= facts.length);
	const currentFact = $derived(facts[active]);

	let raf: number | null = null;
	let startAt = 0;
	let sectionEl: HTMLElement | null = null;

	const markVisited = (index: number) => {
		if (!visited[index]) {
			visited[index] = true;
			visited = [...visited];
		}
	};

	const setActive = (index: number) => {
		active = (index + facts.length) % facts.length;
		markVisited(active);
	};

	const goTo = (index: number) => {
		setActive(index);
		startCycle();
	};

	const step = (now: number) => {
		if (completed || !isVisible) {
			progress = completed ? 1 : progress;
			stopCycle();
			return;
		}
		const elapsed = now - startAt;
		progress = Math.min(elapsed / intervalMs, 1);
		if (progress >= 1) {
			setActive(active + 1);
			startAt = now;
			progress = 0;
		}
		raf = requestAnimationFrame(step);
	};

	const startCycle = () => {
		stopCycle();
		if (completed || !isVisible) {
			return;
		}
		progress = 0;
		startAt = performance.now();
		raf = requestAnimationFrame(step);
	};

	const stopCycle = () => {
		if (raf !== null) cancelAnimationFrame(raf);
		raf = null;
	};

	const pauseCycle = () => {
		stopCycle();
	};

	const resumeCycle = () => {
		if (!completed && isVisible) {
			startAt = performance.now() - progress * intervalMs;
			raf = requestAnimationFrame(step);
		}
	};

	const replay = () => {
		resetVisited();
		active = 0;
		progress = 0;
		markVisited(0);
		startCycle();
	};

	resetVisited();

	onMount(() => {
		const observer = new IntersectionObserver(
			([entry]) => {
				isVisible = entry.isIntersecting;
				if (isVisible) {
					resumeCycle();
				} else {
					pauseCycle();
				}
			},
			{ threshold: 0.1 }
		);

		if (sectionEl) observer.observe(sectionEl);

		startCycle();

		return () => {
			observer.disconnect();
		};
	});

	onDestroy(() => {
		stopCycle();
	});
</script>

<section class="facts">
	<div class="panel">
		<p class="eyebrow">Shark Facts</p>
		<h2 class="headline">{facts[active].title}</h2>
		<p class="body">{facts[active].text}</p>
		{#if completed}
			<div class="cta-row">
				<a class="btn" href="/pet">pet shorks :3</a>
				<button class="btn ghost" type="button" onclick={replay}>replay facts</button>
			</div>
		{:else}
			<div class="indicators" aria-label="Shark facts selector">
				{#each facts as _, i}
					<button
						type="button"
						class={`dot ${i === active ? 'active' : ''}`}
						style={`--p:${i === active ? progress : 0};`}
						onclick={() => goTo(i)}
						aria-pressed={i === active}
						aria-label={`Show fact ${i + 1}`}
					></button>
				{/each}
			</div>
		{/if}
	</div>
</section>

<style>
	.facts {
		background: #e7f2ff;
		color: #0d1b2a;
		padding: clamp(50px, 8vw, 100px) 20px;
		display: flex;
		justify-content: center;
	}

	.panel {
		max-width: 720px;
		width: 100%;
		text-align: center;
	}

	.eyebrow {
		text-transform: uppercase;
		letter-spacing: 0.08em;
		font-size: 0.9rem;
		margin: 0 0 8px 0;
		color: #415a77;
	}

	.headline {
		margin: 0 0 14px 0;
		font-size: clamp(2rem, 4vw, 2.6rem);
		font-weight: 800;
	}

	.body {
		margin: 0 auto 24px auto;
		max-width: 640px;
		font-size: 1.05rem;
		line-height: 1.6;
		color: #1b263b;
	}

	.indicators {
		display: flex;
		gap: 12px;
		justify-content: center;
		align-items: center;
	}

	.cta-row {
		display: flex;
		gap: 14px;
		justify-content: center;
		flex-wrap: wrap;
		margin-top: 12px;
	}

	.btn {
		padding: 12px 20px;
		border-radius: 24px;
		border: 1px solid #1b263b;
		background: #1b263b;
		color: #e7f2ff;
		font-weight: 700;
		cursor: pointer;
		text-decoration: none;
		transition: transform 150ms ease, opacity 150ms ease;
	}

	.btn:hover {
		transform: translateY(-1px);
		opacity: 0.95;
	}

	.btn.ghost {
		background: transparent;
		color: #1b263b;
	}

	.dot {
		width: 14px;
		height: 14px;
		border-radius: 50%;
		border: 1px solid #1b263b;
		background: conic-gradient(#1b263b calc(var(--p, 0) * 360deg), #e7f2ff 0);
		cursor: pointer;
		transition: transform 150ms ease, border-color 150ms ease;
	}

	.dot.active {
		transform: scale(1.15);
		border-color: #0d1b2a;
	}

	.dot:hover {
		transform: scale(1.12);
	}

	@media (max-width: 640px) {
		.body {
			font-size: 1rem;
		}
	}
</style>
