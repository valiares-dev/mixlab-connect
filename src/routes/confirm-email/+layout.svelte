<script lang="ts">
	import '../layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import { injectAnalytics } from '@vercel/analytics/sveltekit';

	injectAnalytics();

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>MixLab | Confirm Email</title>
	<meta
		name="description"
		content="Verify your email address to get started with MixLab Connect and MixLab Mobile App."
	/>
</svelte:head>
{@render children()}
