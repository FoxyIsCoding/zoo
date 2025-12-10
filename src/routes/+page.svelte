<script lang="ts">
	import HeroSection from '$lib/HeroSection.svelte';
	import AlternatingSection from '$lib/AlternatingSection.svelte';
	import MyntsSection from '$lib/SpeedSection.svelte';
	import FAQItem from '$lib/FAQItem.svelte';
	import Footer from '$lib/Footer.svelte';
	import FactsPanel from '$lib/FactsPanel.svelte';	
</script>

<HeroSection title="shorks :3" subtitle="that silly cute things that swin in oceans" />

<AlternatingSection 
	title="GREAT WHITE SHARKS" 
	imageSrc="https://www.australiangeographic.com.au/wp-content/uploads/2022/07/shutterstock_383911432-scaled.jpg?w=400"
	imageAlt="Great White Shark"
	bg="#f8f9fa"
>
	<p>The ocean's most iconic predator! Great whites can grow up to 20 feet long and swim at speeds of 35 mph.</p>
	<p>They live on avarage for over 70 years :o</p>
	<p>These sharks can alsoo swim in the insane deep of up to 4,000 feet! </p>
	<a href="#facts" class="cta-button">Learn More</a>
</AlternatingSection>

<MyntsSection />

<AlternatingSection
	title="WHALE SHARKS" 
	imageSrc="https://www.joali.com/media/qvmcod4g/joali-being-whalesharks-of-the-maldives.png?format=webp&v=1715862213?w=400"
	imageAlt="Whale Shark"
	reverse={true}
	bg="#ffffff"
>
	<p>The gentle giants of the ocean! Whale sharks are the largest fish species, growing up to 40 feet long.</p>
	<p>Despite their massive size, they feed only on plankton and small fish. Each whale shark has a unique spot pattern - like a fingerprint!</p>
	<p style="font-style: italic; opacity: 0.8;">They can live over 100 years!</p>
	<a href="https://saveourseas.com/" class="cta-button secondary">Save shorks :3</a>
</AlternatingSection>

<AlternatingSection 
	title="HAMMERHEAD SHARKS" 
	imageSrc="https://images.unsplash.com/photo-1559827260-dc66d52bef19?w=400"
	imageAlt="Hammerhead Shark"
	bg="#f0f7ff" 
>
	<p><strong>360-degree vision with their hammer-shaped heads!</strong></p>
	<p>These unique sharks use their wide heads to pin stingrays to the ocean floor. They're one of the few shark species that swim in schools :3</p>
	<a href="#learn" class="cta-button">Discover More</a>
</AlternatingSection>
<FactsPanel />
<AlternatingSection 
	title="TIGER SHARKS" 
	imageSrc="https://upload.wikimedia.org/wikipedia/commons/3/39/Tiger_shark.jpg"
	imageAlt="Tiger Shark"
	reverse={true}
	bg="#fff5f5"
>
	<p>The "garbage cans of the sea"!</p>
	<p>Tiger sharks will eat almost anything - they've been found with license plates and tires in their stomachs! Named for the dark stripes on their bodies, they can grow up to 16 feet long.</p>
	<a href="#species" class="cta-button secondary">More Species</a>
</AlternatingSection>

<section class="faq-section">
	<div class="faq-container">
		<div class="faq-header">
			<div class="faq-emoji">🦈</div>
			<h2>SHARK FACTS</h2>
			<p class="faq-subtitle">Everything you wanted to know about sharks!</p>
		</div>
		
		<div class="faq-list">
			<FAQItem 
				question="How long have sharks been around?"
				answer="Sharks have existed for over 400 million years - that's before trees, before dinosaurs! They're older than Saturn's rings and have survived five mass extinction events."
			/>
			<FAQItem 
				question="Are sharks really dangerous to humans?"
				answer="Not really! You're more likely to be struck by lightning than attacked by a shark. Most shark species are completely harmless to humans, and attacks are extremely rare."
			/>
			<FAQItem 
				question="How many species of sharks are there?"
				answer="There are over 500 species of sharks! They range from the tiny dwarf lanternshark (7 inches) to the massive whale shark (40+ feet)."
			/>
			<FAQItem 
				question="Do sharks have bones?"
				answer="Nope! Sharks are made entirely of cartilage - the same flexible material that makes up your nose and ears. This makes them lighter and more flexible in the water."
			/>
			<FAQItem 
				question="How do sharks sleep?"
				answer="Some sharks must keep swimming to breathe, so they sleep while moving! Others can rest on the ocean floor and pump water over their gills."
			/>
			<FAQItem 
				question="What do sharks eat?"
				answer="It depends on the species! Some eat plankton, others prefer fish, squid, seals, or even other sharks. Each species has its own diet preference."
			/>
			<FAQItem 
				question="Can sharks smell blood from miles away?"
				answer="Yes! Sharks have an incredible sense of smell and can detect a single drop of blood in an Olympic-sized swimming pool. Some species can smell prey from several miles away."
			/>
			<FAQItem 
				question="Are sharks endangered?"
				answer="Unfortunately, many shark species are threatened or endangered due to overfishing, finning, and habitat loss. Over 100 million sharks are killed each year, and we need to protect them!"
			/>
		</div>
	</div>
</section>

<Footer />

<style>
	:global(body) {
		margin: 0;
		font-family: 'Phantom Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
	}

	.cta-button {
		display: inline-block;
		background: #ec3750;
		color: white;
		padding: clamp(12px, 2vw, 15px) clamp(24px, 5vw, 35px);
		border-radius: 50px;
		text-decoration: none;
		font-weight: 700;
		font-size: clamp(0.95rem, 2vw, 1.2rem);
		margin-top: clamp(15px, 3vw, 20px);
		transition: transform 0.2s, box-shadow 0.2s;
		box-shadow: 0 4px 12px rgba(236, 55, 80, 0.3);
	}

	.cta-button:hover {
		transform: translateY(-2px);
		box-shadow: 0 6px 20px rgba(236, 55, 80, 0.4);
	}

	.cta-button.secondary {
		background: #5bc0de;
		box-shadow: 0 4px 12px rgba(91, 192, 222, 0.3);
	}

	.cta-button.secondary:hover {
		box-shadow: 0 6px 20px rgba(91, 192, 222, 0.4);
	}

	.faq-section {
		background: #f8f9fa;
		padding: clamp(50px, 8vw, 80px) clamp(16px, 4vw, 20px);
	}

	.faq-container {
		max-width: 900px;
		margin: 0 auto;
	}

	.faq-header {
		text-align: center;
		margin-bottom: clamp(30px, 6vw, 50px);
	}

	.faq-emoji {
		font-size: clamp(4rem, 12vw, 8rem);
		margin-bottom: clamp(15px, 3vw, 20px);
	}

	.faq-header h2 {
		font-size: clamp(2.5rem, 5vw, 4rem);
		font-weight: 900;
		margin: 0 0 15px 0;
		color: #1f2d3d;
	}

	.faq-subtitle {
		font-size: clamp(1rem, 2.5vw, 1.3rem);
		color: #555;
		margin: 0;
	}

	.faq-list {
		background: white;
		border-radius: 15px;
		padding: clamp(16px, 4vw, 20px);
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
	}

	@media (max-width: 768px) {
		.faq-section {
			padding: clamp(40px, 6vw, 60px) clamp(12px, 3vw, 20px);
		}

		.faq-list {
			padding: clamp(14px, 3vw, 18px);
		}
	}

	@media (max-width: 640px) {
		.cta-button {
			display: block;
			width: 100%;
			max-width: 250px;
			margin: clamp(12px, 3vw, 15px) auto;
			text-align: center;
			padding: clamp(10px, 2vw, 12px) clamp(20px, 4vw, 24px);
		}
	}
</style>
