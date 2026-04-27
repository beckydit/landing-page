<script>
    import Icon from "$lib/components/Icon.svelte";

    const {
        ref,
        title = null,
        children = null,
        leadingIcon = null,
        trailingIcon = null,
    } = $props();
</script>

<a href={ref}>
    {#if children}
        {@render children()}
    {:else}
        {#if leadingIcon}
            <Icon name={leadingIcon} />
        {/if}

        <span class="link-text">{title}</span>

        {#if trailingIcon}
            <Icon name={trailingIcon} />
        {/if}
    {/if}
</a>

<style>
    a {
        display: inline-flex;
        align-items: center;
        gap: var(--size-1);
        text-decoration: none;
        
        /* Il colore del testo rimane quello base */
        color: var(--color-ink);
        
        /* Applichiamo la transizione globale per sicurezza */
        transition: color 0.3s var(--ease-out-quart);

        /* Quando passi il mouse sul link, l'icona interna cambia colore */
        &:hover :global(i) {
            color: var(--color-link);
        }
    }

    /* Stile per l'icona (tag <i> generato da Phosphor) */
    :global(i) {
        transition: color 0.3s var(--ease-out-quart);
    }

    .link-text {
        /* Il testo non cambia colore, quindi non serve transition qui */
    }
</style>