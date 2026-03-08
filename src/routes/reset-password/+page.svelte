<script>
	import { onMount } from 'svelte';

	let appSchemeLink = '#';

	onMount(() => {
		// Grab the hash fragments that Supabase appended to this URL
		// It looks like #access_token=...&refresh_token=...&type=recovery
		const hash = window.location.hash;

		// Construct the deep link to the mobile app
		appSchemeLink = 'mixlab-alt-app://reset-password' + hash;

		// Automatically attempt to redirect without waiting for click
		// (Some browsers allow this if they haven't blocked auto-redirects)
		setTimeout(() => {
			window.location.href = appSchemeLink;
		}, 500);
	});
</script>

<svelte:head>
	<title>MixLab Reset Password</title>
</svelte:head>

<div class="container-wrapper">
	<div class="container">
		<div class="logo">🎵</div>
		<h1>Reset Your Password</h1>
		<p>
			Authentication complete. Tap the button below to return to MixLab and set your new password.
		</p>

		<a href={appSchemeLink} class="btn">Open MixLab App</a>

		<p class="help-text">If nothing happens, ensure the MixLab app is installed.</p>
	</div>
</div>

<style>
	/* Styling scoped to this Svelte component */
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
