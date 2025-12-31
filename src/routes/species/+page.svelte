<script lang="ts">
	import Footer from '$lib/Footer.svelte';
</script>

<section class="species-page">
	<div class="species-container">
		<div class="species-header">
			<a href="/" class="back-link">← Back to Home</a>
			<div class="species-emoji">🦈</div>
			<h1>ALL SHARK SPECIES</h1>
			<p class="species-subtitle">Explore the amazing diversity of sharks!</p>
		</div>
		
		<div class="species-grid">
			<div class="species-card">
				<h3>Great White Shark</h3>
				<p class="species-speed">⚡ 35 mph</p>
				<p>The ocean's most iconic predator! Can grow up to 20 feet long and live for over 70 years.</p>
			</div>
			<div class="species-card">
				<h3>Whale Shark</h3>
				<p class="species-info">Gentle giant - 40+ feet</p>
				<p>The largest fish species! Despite their size, they feed only on plankton and small fish.</p>
			</div>
			<div class="species-card">
				<h3>Hammerhead Shark</h3>
				<p class="species-info">360° vision</p>
				<p>Their hammer-shaped heads give them incredible vision and help pin prey to the ocean floor.</p>
			</div>
			<div class="species-card">
				<h3>Tiger Shark</h3>
				<p class="species-info">Garbage can of the sea</p>
				<p>Will eat almost anything! Named for dark stripes on their bodies, grow up to 16 feet long.</p>
			</div>
			<div class="species-card">
				<h3>Shortfin Mako</h3>
				<p class="species-speed">⚡ 60+ mph</p>
				<p>The fastest shark in the ocean! Built for speed with a sleek body and powerful tail.</p>
			</div>
			<div class="species-card">
				<h3>Bull Shark</h3>
				<p class="species-info">Freshwater survivor</p>
				<p>Can survive in both saltwater and freshwater. Known for their aggressive behavior.</p>
			</div>
			<div class="species-card">
				<h3>Nurse Shark</h3>
				<p class="species-info">Bottom dweller</p>
				<p>Gentle and slow-moving, they use barbels near their mouth to sense food on the ocean floor.</p>
			</div>
			<div class="species-card">
				<h3>Thresher Shark</h3>
				<p class="species-info">Whip-like tail</p>
				<p>Uses their incredibly long tail to herd and stun fish schools. Up to 20 feet of tail!</p>
			</div>
			<div class="species-card">
				<h3>Goblin Shark</h3>
				<p class="species-info">Deep sea mystery</p>
				<p>A rare deep-sea shark with a long snout and extendable jaws. Barely studied!</p>
			</div>
			<div class="species-card">
				<h3>Blue Shark</h3>
				<p class="species-info">Ocean blue beauty</p>
				<p>Named for their deep blue coloring, they're migratory sharks that travel thousands of miles.</p>
			</div>
			<div class="species-card">
				<h3>Blacktip Reef Shark</h3>
				<p class="species-info">Recognizable fins</p>
				<p>Famous for their black-tipped fins. Often seen near shallow coral reefs!</p>
			</div>
			<div class="species-card">
				<h3>Lemon Shark</h3>
				<p class="species-info">Yellow-brown</p>
				<p>Named for their pale yellow color. Super smart and curious about their surroundings.</p>
			</div>
			<div class="species-card">
				<h3>Basking Shark</h3>
				<p class="species-info">Plankton eater - 30+ feet</p>
				<p>Second largest shark! Swims with mouth wide open to filter feed on plankton.</p>
			</div>
			<div class="species-card">
				<h3>Sawfish</h3>
				<p class="species-info">Chainsaw snout</p>
				<p>More closely related to rays, but often called "shark-like." Has a serrated rostrum!</p>
			</div>
			<div class="species-card">
				<h3>Frilled Shark</h3>
				<p class="species-info">Living fossil</p>
				<p>One of the most primitive sharks, with 300+ teeth arranged in 25 rows!</p>
			</div>
			<div class="species-card">
				<h3>Lanternshark</h3>
				<p class="species-info">Tiny bioluminescent</p>
				<p>The smallest shark species at just 7 inches! Glows in the deep sea darkness.</p>
			</div>
			<div class="species-card">
				<h3>Angel Shark</h3>
				<p class="species-info">Flat body</p>
				<p>More ray-like with their flat bodies and wing-like fins. Masters of camouflage!</p>
			</div>
			<div class="species-card">
				<h3>Sevengill Shark</h3>
				<p class="species-info">Ancient design</p>
				<p>Has seven gill slits instead of five. A prehistoric-looking deep-sea dweller!</p>
			</div>
			<div class="species-card">
				<h3>Greenland Shark</h3>
				<p class="species-info">Arctic survivor</p>
				<p>Can live over 400 years! The longest-living vertebrate species on Earth.</p>
			</div>
			<div class="species-card">
				<h3>Megamouth Shark</h3>
				<p class="species-info">Rare filter feeder</p>
				<p>Extremely rare deep-sea shark with a massive mouth. Less than 300 sightings ever!</p>
			</div>
			<div class="species-card">
				<h3>Port Jackson Shark</h3>
				<p class="species-info">Horn shark</p>
				<p>Named after a bay in Australia. Has unique head ridges and can walk on the ocean floor!</p>
			</div>
			<div class="species-card">
				<h3>Cookie Cutter Shark</h3>
				<p class="species-info">Circular bite</p>
				<p>Takes round "cookie" shaped bites out of prey! Even attacks submarines and whales.</p>
			</div>
		</div>
	</div>
</section>

<Footer />

<style>
	:global(html) {
		scroll-behavior: smooth;
	}

	:global(body) {
		margin: 0;
		font-family: 'Phantom Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
	}

	.species-page {
		min-height: 100vh;
		background: linear-gradient(135deg, #e3f2fd 0%, #f3e5f5 100%);
		padding: clamp(50px, 8vw, 80px) clamp(16px, 4vw, 20px);
	}

	.species-container {
		max-width: 1400px;
		margin: 0 auto;
	}

	.species-header {
		text-align: center;
		margin-bottom: clamp(40px, 8vw, 60px);
		position: relative;
	}

	.back-link {
		position: absolute;
		left: 0;
		top: 0;
		color: #1f2d3d;
		text-decoration: none;
		font-weight: 600;
		font-size: 1.1rem;
		transition: transform 0.2s;
	}

	.back-link:hover {
		transform: translateX(-5px);
	}

	.species-emoji {
		font-size: clamp(4rem, 12vw, 8rem);
		margin-bottom: clamp(15px, 3vw, 20px);
	}

	.species-header h1 {
		font-size: clamp(2.5rem, 6vw, 5rem);
		font-weight: 900;
		margin: 0 0 15px 0;
		color: #1f2d3d;
	}

	.species-subtitle {
		font-size: clamp(1rem, 2.5vw, 1.5rem);
		color: #555;
		margin: 0;
	}

	.species-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
		gap: clamp(20px, 3vw, 30px);
	}

	.species-card {
		background: white;
		border-radius: 15px;
		padding: clamp(24px, 4vw, 30px);
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
		transition: transform 0.3s ease, box-shadow 0.3s ease;
	}

	.species-card:hover {
		transform: translateY(-8px);
		box-shadow: 0 12px 30px rgba(0, 0, 0, 0.2);
	}

	.species-card h3 {
		margin: 0 0 12px 0;
		color: #1f2d3d;
		font-size: clamp(1.2rem, 2.2vw, 1.6rem);
		font-weight: 800;
	}

	.species-card p {
		margin: 8px 0;
		line-height: 1.7;
		color: #333;
		font-size: clamp(0.95rem, 1.8vw, 1.1rem);
	}

	.species-speed {
		font-weight: 700;
		color: #ec3750;
		font-size: 1.1rem;
	}

	.species-info {
		font-weight: 600;
		color: #5bc0de;
		font-size: 1rem;
	}

	@media (max-width: 768px) {
		.species-grid {
			grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
			gap: clamp(15px, 2vw, 20px);
		}

		.back-link {
			position: static;
			display: block;
			margin-bottom: 20px;
		}
	}

	@media (max-width: 640px) {
		.species-grid {
			grid-template-columns: 1fr;
		}
	}
</style>
