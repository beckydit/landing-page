<script>
    import Icon from "./Icon.svelte";
    const { data: project } = $props();
</script>

<article>
    <div class="thumbnail">
    <div class="veil">
        <span class="hover-text">
            {project.description || "Vedi Progetto"}
        </span>
    </div>
    <img src={project.thumbnail} alt={project.title} />
</div>

    <header>
        <hgroup>
            <h3>{project.title}</h3>
            <span>/ {project.year}</span>
        </hgroup>

        <div class="arrow">
            <Icon name="arrow-up-right" />
        </div>
    </header>
</article>

<style>
    article {
        display: flex;
        flex-direction: column;
        gap: var(--size-2);
        cursor: default;

        &:hover {
            .veil {
                opacity: 1;
            }
            .arrow {
                transform: translateY(0);
            }
        }
    }

    .thumbnail {
        position: relative;
        aspect-ratio: 16/10;
        overflow: hidden;

    .veil {
        position: absolute;
        inset: 0;
        
        /* Qui riportiamo il colore brand originale */
        /* Puoi usare --hex-brand-500 per il rosa classico */
        /* O --color-link se vuoi che segua il tema */
        background-color: var(--hex-brand-600); 
        
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 1;
        
        /* Manteniamo la transizione rapida che abbiamo deciso */
        transition: opacity 0.2s ease-in-out; 
        opacity: 0;
    }

        .hover-text {
        color: var(--hex-neutral-50);
        font-size: var(--size-4); /* Puoi provare size-3 se le descrizioni sono lunghe */
        font-weight: 500;
        text-transform: none; /* Forse meglio evitare il tutto maiuscolo per le descrizioni lunghe */
        padding-inline: var(--size-4); /* Evita che il testo tocchi i bordi della card */
        line-height: 1.4;
        max-width: 20ch; /* Limita la larghezza per una lettura migliore */
        }

        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    }

    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: var(--size-4);
        overflow: clip;
    }

    hgroup {
        display: flex;
        align-items: center;
        gap: var(--size-2);
        span {
            color: var(--color-ink-secondary);
        }
    }

    .arrow {
        /* La freccia mantiene il suo movimento fluido caratteristico */
        transition: transform 0.6s var(--ease-out-quart);
        transform: translateY(100%);
    }
</style>