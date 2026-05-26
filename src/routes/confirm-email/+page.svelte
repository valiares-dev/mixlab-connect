<script>
	import { onMount } from 'svelte';

	let appSchemeLink = 'mixlab-alt-app://login';

	onMount(() => {
		// Grab any hash or search fragments that Supabase might append
		const hash = window.location.hash || '';
		const search = window.location.search || '';

		// Construct the deep link to the mobile app's login page
		appSchemeLink = 'mixlab-alt-app://login' + search + hash;

		// Automatically attempt to redirect without waiting for click
		setTimeout(() => {
			window.location.href = appSchemeLink;
		}, 500);
	});
</script>

<svelte:head>
	<title>MixLab | Email Confirmed</title>
</svelte:head>

<div class="container-wrapper">
	<div class="container">
		<div class="logo">✅</div>
		<h1>Email Confirmed!</h1>
		<p>
			Your email has been successfully verified. Tap the button below to return to the MixLab app and log in.
		</p>

		<a href={appSchemeLink} class="btn">Open MixLab App</a>

		<p class="help-text">If nothing happens, ensure the MixLab app is installed on your device.</p>
	</div>
</div>

<style>
	:global(body) {
		font-family:
			-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
		margin: 0;
		background-color: #f5f5f5;
	}

	.container-wrapper {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100vh;
		width: 100vw;
	}

	.container {
		text-align: center;
		background: white;
		padding: 40px;
		border-radius: 12px;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
		max-width: 90%;
		width: 400px;
	}

	h1 {
		color: #333;
		margin-bottom: 10px;
		font-size: 24px;
	}

	p {
		color: #666;
		margin-bottom: 30px;
		line-height: 1.5;
	}

	.btn {
		display: inline-block;
		background: linear-gradient(90deg, #dedaa0 0%, #b4a063 100%);
		color: white;
		text-decoration: none;
		padding: 14px 28px;
		border-radius: 999px;
		font-weight: bold;
		font-size: 16px;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
		transition: opacity 0.2s;
		cursor: pointer;
		border: none;
	}

	.btn:hover {
		opacity: 0.9;
	}

	.btn:active {
		transform: translateY(1px);
	}

	.logo {
		width: 80px;
		height: 80px;
		background-color: #f0f0f0;
		border-radius: 50%;
		margin: 0 auto 20px auto;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 32px;
		color: #b4a063;
	}

	.help-text {
		margin-top: 20px;
		font-size: 12px;
		color: #999;
		margin-bottom: 0;
	}
</style>
