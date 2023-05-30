<svelte:head>
	<title>Subscribe to our newsletter!</title>
	<meta
		name="description"
		content="Join 60,000 product managers receiving monthly updates on product discovery, measuring success, and much more!"
	/>
</svelte:head>

<main>
	<img class="mobile-banner" src="/illustration-sign-up-mobile.svg" alt="" />

	<div class="content">
		<div class="desktop-left">
			<h1>Stay updated!</h1>

			<p>Join 60,000 product managers receiving monthly updates on:</p>

			<ul>
				<li>Product discovery and building what matters</li>

				<li>Measuring to ensure updates are a success</li>

				<li>And much more!</li>
			</ul>

			<form action="">
				<label for="email">Email address</label>
				<input type="email" name="email" id="email" placeholder="email@company.com" />

				<button type="submit">Subscribe to monthly newsletter</button>
			</form>
		</div>

		<div class="desktop-right">
			<img class="desktop-banner" src="/illustration-sign-up-desktop.svg" alt="" />
		</div>
	</div>
</main>

<style>
	img.mobile-banner {
		width: 100%;
	}

	div.content {
		padding: 1.5rem;
	}

	h1 {
		font-size: 2.5rem;
		font-weight: 700;
	}

	p {
		margin-top: 1.25rem;
	}

	ul {
		list-style: none;
		margin-top: 1.25rem;
	}

	li {
		position: relative;
		padding-left: 2rem;
	}

	li + li {
		margin-top: 0.75rem;
	}

	li::before {
		content: url('/icon-list.svg');
		position: absolute;
		left: 0;
	}

	form {
		margin-top: 2rem;
	}

	label {
		font-size: 0.75rem;
		font-weight: 700;
	}

	input {
		border: 1px solid var(--grey);
		border-radius: 0.5rem;
		color: var(--charcoal);
		font-size: 1rem;
		margin-top: 0.5rem;
		outline: none;
		padding: 1rem 1.25rem;
		width: 100%;
	}

	button {
		background-color: var(--dark-slate);
		border: 1px solid var(--dark-slate);
		border-radius: 0.5rem;
		color: var(--white);
		font-size: 1rem;
		font-weight: bold;
		margin-top: 1.5rem;
		padding: 1rem 1.25rem;
		width: 100%;
	}

	img.desktop-banner {
		display: none;
	}

	/* Desktop styles. */
	@media (min-width: 48em) {
		:global(html) {
			height: 100%;
		}

		:global(body) {
			background-color: var(--dark-slate);
			height: 100%;
		}

		:global(main) {
			display: grid;
			height: 100%;
			padding: 1rem;
			place-content: center;
		}

		img.mobile-banner {
			display: none;
		}

		div.content {
			border-radius: 2rem;
			display: flex;
			background-color: var(--white);
		}

		div.desktop-left,
		div.desktop-right {
			flex: 1 1 100%;
		}

		div.desktop-left {
			max-width: 450px;
			padding: 2rem;
		}

		div.desktop-right {
			align-self: center;
			max-width: 400px;
		}

		h1 {
			font-size: 3rem;
		}

		img.desktop-banner {
			display: block;
			width: 100%;
		}
	}
</style>
