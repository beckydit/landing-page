<script>
    import Icon from "./Icon.svelte";
    const { data: project } = $props();
</script>

<article>
    <div class="thumbnail">
        <div class="veil">
            <span class="hover-text">Vedi Progetto</span>
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
            background-color: var(--hex-brand-800);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1;
            
            /* Transizione rapida e secca */
            transition: opacity 0.2s ease-in-out; 
            opacity: 0;
        }

        .hover-text {
            color: var(--hex-neutral-50);
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            /* Nessun movimento, appare e basta insieme al velo */
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