<script lang="ts">
	import '$lib/main.css';
	import successIcon from '$lib/images/icon-success.svg';
	import desktopBanner from '$lib/images/illustration-sign-up-desktop.svg';
	import mobileBanner from '$lib/images/illustration-sign-up-mobile.svg';

	let email = '';
	let showSuccessMessage = false;
	let emailIsEmpty = false;
	let emailIsInvalid = false;

	function onSubmit() {
		if (!email) {
			showSuccessMessage = false;
			emailIsEmpty = true;
			emailIsInvalid = false;
			return;
		}

		if (!email.match(/.+@.+\..+/)) {
			showSuccessMessage = false;
			emailIsEmpty = false;
			emailIsInvalid = true;
			return;
		}

		showSuccessMessage = true;
		emailIsEmpty = false;
		emailIsInvalid = false;
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
				<img src={successIcon} alt="" />

				<h1>Thanks for subscribing!</h1>

				<p>
					A confirmation email has been sent to <b>{email}</b>. Please open it and click the button
					inside to confirm your subscription.
				</p>
			</div>

			<button type="button" on:click={onDismiss}>Dismiss message</button>
		</div>
	{:else}
		<img class="mobile-banner" src={mobileBanner} alt="" />

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
					<label for="email">
						Email address

						{#if emailIsEmpty}
							<span class="error">Email required</span>
						{:else if emailIsInvalid}
							<span class="error">Valid email required</span>
						{/if}
					</label>
					<input
						type="email"
						class:error={emailIsEmpty || emailIsInvalid}
						name="email"
						id="email"
						placeholder="email@company.com"
						bind:value={email}
					/>

					<button type="submit">Subscribe to monthly newsletter</button>
				</form>
			</div>

			<div class="desktop-right">
				<img class="desktop-banner" src={desktopBanner} alt="" />
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
		display: flex;
		font-size: 0.75rem;
		font-weight: 700;
	}

	span.error {
		color: var(--tomato);
		margin-inline-start: auto;
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

	input::placeholder {
		color: var(--charcoal);
	}

	input:focus {
		border-color: var(--dark-slate);
		color: var(--dark-slate);
	}

	input.error {
		background-color: var(--tomato-light);
		border-color: var(--tomato);
		color: var(--tomato-dark);
	}

	input.error::placeholder {
		color: var(--tomato-dark);
		font-weight: 700;
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
