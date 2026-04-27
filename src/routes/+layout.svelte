<script>
	import favicon from "$lib/assets/favicon.svg";

	import "$lib/styles/reset.css";
	import "$lib/styles/tokens.css";
	import "$lib/styles/base.css";
	import "$lib/styles/utilities.css";

	import Header from "$lib/components/Header.svelte";
	import Footer from "$lib/components/Footer.svelte";

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />

	<!-- Rowan Font -->
	<link rel="preconnect" href="https://api.fontshare.com/" />
	<link href="https://api.fontshare.com/v2/css?f[]=rowan@400&display=swap" rel="stylesheet"/>
</svelte:head>

<Header />

{@render children()}

<Footer />
