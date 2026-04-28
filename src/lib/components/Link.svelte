<script>
    import Icon from "$lib/components/Icon.svelte";

    const {
        ref,
        title = null,
        children = null,
        leadingIcon = null,
        trailingIcon = null,
    } = $props();

    const hasIcons = $derived(leadingIcon || trailingIcon);
</script>

<a href={ref} class:has-icons={hasIcons}>
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
        gap: var(--size-2);
        text-decoration: none;
        color: var(--color-ink);
        position: relative;
        padding-bottom: 4px;
        
        /* Usiamo la tua transizione della card per il colore */
        transition: color 0.75s var(--ease-out-quart);

        &::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 2px;
            background-color: var(--color-link);
            
            /* Animazione della linea con la tua libreria */
            transform: scaleX(0);
            transform-origin: right;
            transition: transform 0.75s var(--ease-out-quart);
        }

        &:hover {
            &::after {
                transform: scaleX(1);
                transform-origin: left;
            }

            /* Caso senza icone */
            &:not(.has-icons) {
                color: var(--color-link);
            }

            /* Caso con icone: le stelle diventano rosa */
            &.has-icons :global(i) {
                color: var(--color-link);
            }
        }
    }

    /* Coerenza totale: anche le icone usano la tua curva quart */
    :global(i) {
        transition: color 0.75s var(--ease-out-quart);
    }
</style>