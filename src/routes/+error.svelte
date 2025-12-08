<script lang="ts">
	import { page } from '$app/state';

	const errorMessages = [
		"Oopsie woopsie! The shorks ate this page!",
		"This page swam away... just like a silly shork!",
		"404 - Page not found (probably hiding from a shark)",
		"Uh oh! You've entered the deep end... too deep!",
		"This page got eaten by a hungry shark. RIP.",
		"ERROR: Too much cuteness, page exploded!",
		"Whoopsie! The shorks are on break right now"
	];

	const randomMessage = errorMessages[Math.floor(Math.random() * errorMessages.length)];
</script>

<div class="error-container">
	<h1 class="error-code">{page.status || 404}</h1>
	<h2 class="error-title">{randomMessage}</h2>
	<p class="error-description">
		{#if page.status === 404}
			The page you're looking for doesn't exist. Maybe a shark took it?
		{:else if page.status === 500}
			Something went terribly wrong on our end. The sharks are investigating!
		{:else}
			{page.error?.message || "Something went wrong!"}
		{/if}
	</p>

	<a href="/" class="home-button">Back</a>
</div>

<style>
	.error-container {
		min-height: 100vh;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		background: #3b82f6;
		padding: 2rem;
		text-align: center;
		color: white;
	}

	.error-code {
		font-size: 12rem;
		font-weight: bold;
		margin: 0;
	}

	.error-title {
		font-size: 3rem;
		margin: 1rem 0;
		font-weight: 600;
	}

	.error-description {
		font-size: 1.5rem;
		margin: 1.5rem 0;
	}

	.home-button {
		display: inline-block;
        border-radius: 25px;
		padding: 1rem 2.5rem;
		background: white;
		color: #3b82f6;
		text-decoration: none;
		font-weight: bold;
		font-size: 1.2rem;
		margin-top: 2rem;
	}

	.home-button:hover {
		opacity: 0.9;
	}

	@media (max-width: 768px) {
		.error-code {
			font-size: 6rem;
		}

		.error-title {
			font-size: 2rem;
		}

		.error-description {
			font-size: 1.2rem;
		}
	}
</style>
