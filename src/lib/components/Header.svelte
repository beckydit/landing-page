<script>
	import Link from "$lib/components/Link.svelte";
</script>

<header class="safe-area">
	<Link title=".indd" ref="/" />

	<nav>
		<Link
			title="@kyouuuka"
			ref="https://www.instagram.com/kyouuuka"
		/>
	</nav>
</header>

<style>
	header {
		padding-block: var(--size-6);

		display: flex;
		gap: var(--size-8);
		justify-content: space-between;
		align-items: center;
	}

	nav {
		display: flex;
		gap: var(--size-6);
		align-items: center;
	}
</style>
