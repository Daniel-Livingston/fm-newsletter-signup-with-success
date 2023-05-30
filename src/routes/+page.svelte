<script lang="ts">
	let email = '';
	let showSuccessMessage = false;

	function onSubmit() {
		if (!email || !email.match(/.+@.+\..+/)) {
			showSuccessMessage = false;
			return;
		}

		showSuccessMessage = true;
	}

	function onDismiss() {
		showSuccessMessage = false;
	}
</script>

<svelte:head>
	<title>Subscribe to our newsletter!</title>
	<meta
		name="description"
		content="Join 60,000 product managers receiving monthly updates on product discovery, measuring success, and much more!"
	/>
</svelte:head>

<main>
	{#if showSuccessMessage}
		<div class="success-content">
			<div class="center-vertical">
				<img src="/icon-success.svg" alt="" />

				<h1>Thanks for subscribing!</h1>

				<p>
					A confirmation email has been sent to <b>{email}</b>. Please open it and click the button
					inside to confirm your subscription.
				</p>
			</div>

			<button type="button" on:click={onDismiss}>Dismiss message</button>
		</div>
	{:else}
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

				<form action="" on:submit={onSubmit} novalidate>
					<label for="email">Email address</label>
					<input
						type="email"
						name="email"
						id="email"
						placeholder="email@company.com"
						bind:value={email}
					/>

					<button type="submit">Subscribe to monthly newsletter</button>
				</form>
			</div>

			<div class="desktop-right">
				<img class="desktop-banner" src="/illustration-sign-up-desktop.svg" alt="" />
			</div>
		</div>
	{/if}
</main>

<style>
	:global(html, body, main) {
		height: 100%;
	}

	div.success-content {
		display: flex;
		flex-direction: column;
		height: 100%;
		justify-content: center;
		padding: 2.5rem 1.5rem;
	}

	div.center-vertical {
		margin: auto 0;
		padding-bottom: 3rem;
	}

	div.success-content h1 {
		margin-top: 2.25rem;
	}

	div.success-content button {
		margin-top: auto;
	}

	b {
		color: var(--dark-slate);
	}

	img.mobile-banner {
		width: 100%;
	}

	div.content {
		padding: 1.5rem;
	}

	h1 {
		color: var(--dark-slate);
		font-size: 2.5rem;
		font-weight: 700;
		line-height: 1;
		margin-top: 1rem;
	}

	p {
		color: var(--charcoal);
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
		color: var(--dark-slate);
		font-size: 0.75rem;
		font-weight: 700;
	}

	input {
		border: 1px solid #c3c3c3;
		border-radius: 0.5rem;
		color: var(--charcoal);
		font-size: 1rem;
		margin-top: 0.5rem;
		outline: none;
		padding: 1rem 1.25rem;
		width: 100%;
	}

	input:focus {
		border-color: var(--dark-slate);
		color: var(--dark-slate);
	}

	button {
		background: var(--dark-slate);
		border: 1px solid var(--dark-slate);
		border-radius: 0.5rem;
		color: var(--white);
		cursor: pointer;
		font-size: 1rem;
		font-weight: bold;
		margin-top: 1.5rem;
		padding: 1.125rem 1.25rem;
		width: 100%;
	}

	button:hover,
	button:focus {
		background: linear-gradient(135deg, var(--pink) 0%, var(--tomato) 50%);
		border-color: transparent;
		outline: none;
	}

	img.desktop-banner {
		display: none;
	}

	/* Desktop styles. */
	@media (min-width: 48em) {
		:global(body) {
			background-color: var(--dark-slate);
		}

		:global(main) {
			display: grid;
			padding: 1rem;
			place-content: center;
		}

		div.success-content {
			background-color: var(--white);
			border-radius: 2rem;
			max-width: 31.5rem;
			padding: 4rem;
		}

		div.center-vertical {
			padding: 0;
		}

		div.success-content button {
			margin-top: 2.5rem;
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
			font-size: 3.4rem;
			margin-top: 3rem;
		}

		p {
			margin-top: 1.5rem;
		}

		ul {
			margin-top: 1.5rem;
		}

		img.desktop-banner {
			display: block;
			width: 100%;
		}
	}
</style>
