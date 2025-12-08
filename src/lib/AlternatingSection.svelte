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
		padding: 80px 20px;
	}

	.container {
		max-width: 1200px;
		margin: 0 auto;
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 60px;
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
		font-size: 1.3rem;
		line-height: 1.6;
		margin: 15px 0;
	}

	@media (max-width: 768px) {
		.container {
			grid-template-columns: 1fr;
			gap: 30px;
		}

		.reverse .container {
			direction: ltr;
		}

		.content-column {
			text-align: center;
		}
	}
</style>
