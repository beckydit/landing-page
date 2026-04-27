<script>
    import Link from "$lib/components/Link.svelte";
    import Icon from "$lib/components/Icon.svelte";
</script>

<header class="safe-area">
    <Link title=".indd" ref="/" />

    <nav>
        <Link
            title="my empty ig"
            ref="https://www.instagram.com/kyouuuka"
			leadingIcon="star"
            trailingIcon="star"
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