<footer class="zoo-footer">
	<div class="footer-content">
		<div class="footer-brand">
			<p class="footer-text">shorks :3</p>
		</div>
		<div class="footer-links">
			<a href="https://saveourseas.com" target="_blank" rel="noopener noreferrer">save poor sharks :c</a>
			<a href="#facts">some facts</a>
			<a href="#species">species guide</a>
		</div>
	</div>
</footer>

<style>
	.zoo-footer {
		background: #1f2d3d;
		color: white;
		padding: clamp(30px, 6vw, 40px) clamp(16px, 4vw, 20px);
		text-align: center;
	}

	.footer-content {
		max-width: 1200px;
		margin: 0 auto;
	}

	.footer-brand {
		margin-bottom: clamp(15px, 4vw, 25px);
	}

	.footer-text {
		font-size: 1.1rem;
		margin: 10px 0;
		opacity: 0.9;
	}

	.footer-links {
		display: flex;
		gap: clamp(15px, 4vw, 30px);
		justify-content: center;
		flex-wrap: wrap;
		margin-top: clamp(15px, 3vw, 20px);
	}

	.footer-links a {
		color: white;
		text-decoration: none;
		font-size: 1rem;
		opacity: 0.8;
		transition: opacity 0.2s;
	}

	.footer-links a:hover {
		opacity: 1;
		text-decoration: underline;
	}

	@media (max-width: 640px) {
		.footer-links {
			gap: clamp(12px, 3vw, 20px);
		}

		.footer-links a {
			font-size: clamp(0.85rem, 2vw, 1rem);
		}

		.footer-icon {
			font-size: clamp(36px, 8vw, 48px);
		}

		.footer-text {
			font-size: clamp(0.9rem, 2.5vw, 1.1rem);
		}
	}
</style>
