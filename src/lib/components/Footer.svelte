<script>
    import poliminero from "$lib/assets/poliminero.png";
    import polimibianco from "$lib/assets/polimibianco.png";
</script>

<footer class="safe-area">
    <img src={polimibianco} alt="Logo" class="logo-on-dark" />
    <img src={poliminero} alt="Logo" class="logo-on-light" />
</footer>

<style>
    footer {
        padding-block: var(--size-10);
        display: flex;
        justify-content: center;
        align-items: center;
    }

    img {
        height: var(--size-9);
        display: block;
        transition: opacity 0.5s var(--ease-out-quart);
    }

    /* --- LOGICA DI VISUALIZZAZIONE --- */

    /* DEFAULT (DARK MODE) */
    .logo-on-light {
        display: none !important;
    }
    .logo-on-dark {
        display: block !important;
    }

    /* LIGHT MODE */
    :global(html[data-theme="light"]) .logo-on-dark {
        display: none !important;
    }
    :global(html[data-theme="light"]) .logo-on-light {
        display: block !important;
    }
</style>