<script lang="ts">
	interface Props {
		title: string;
		description?: string;
		imageSrc?: string;
		imageAlt?: string;
		reverse?: boolean;
		bg?: string;
		children?: any;
	}
	
	let { title, description, imageSrc, imageAlt = '', reverse = false, bg = '#ffffff', children }: Props = $props();
</script>

<section class="alternating" class:reverse style="background-color: {bg};">
	<div class="container">
		{#if imageSrc}
			<div class="image-column">
				<img src={imageSrc} alt={imageAlt} />
			</div>
		{/if}
		<div class="content-column">
			<h2>{title}</h2>
			{#if description}
				<p>{description}</p>
			{/if}
			{@render children?.()}
		</div>
	</div>
</section>

<style>
	.alternating {
		padding: clamp(40px, 6vw, 80px) clamp(16px, 4vw, 20px);
	}

	.container {
		max-width: 1200px;
		margin: 0 auto;
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: clamp(30px, 6vw, 60px);
		align-items: center;
	}

	.reverse .container {
		direction: rtl;
	}

	.reverse .content-column {
		direction: ltr;
	}

	.image-column img {
		width: 100%;
		max-width: 400px;
		height: auto;
		margin: 0 auto;
		display: block;
		border-radius: clamp(14px, 2vw, 20px);
	}

	.content-column {
		text-align: left;
	}

	h2 {
		font-size: clamp(2rem, 4vw, 3.5rem);
		font-weight: 800;
		margin: 0 0 20px 0;
		line-height: 1.2;
	}

	p {
		font-size: clamp(1rem, 2vw, 1.3rem);
		line-height: 1.6;
		margin: 15px 0;
	}

	@media (max-width: 768px) {
		.alternating {
			padding: clamp(32px, 4vw, 60px) clamp(12px, 3vw, 20px);
		}

		.container {
			grid-template-columns: 1fr;
			gap: clamp(20px, 5vw, 40px);
		}

		h2 {
			font-size: clamp(1.5rem, 5vw, 2.5rem);
		}

		p {
			font-size: clamp(0.95rem, 2.5vw, 1.1rem);
		}

		.reverse .container {
			direction: ltr;
		}

		.content-column {
			text-align: center;
		}
	}

	@media (max-width: 640px) {
		.image-column img {
			max-width: 100%;
			border-radius: clamp(22px, 6vw, 32px);
		}
	}
</style>
