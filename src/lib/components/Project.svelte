<script>
    import Icon from "./Icon.svelte";

    const { data: project } = $props();
</script>

<article>
    <div class="thumbnail">
        <div class="veil"></div>
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
        cursor: default; /* Cambiato da pointer a default poiché non è cliccabile */

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
            width: 100%;
            height: 100%;
            background-color: var(--color-link);
            mix-blend-mode: soft-light;

            transition: opacity 0.75s var(--ease-out-quart);
            opacity: 0;
            z-index: 1;
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
        transition: transform 0.75s var(--ease-out-quart);
        transform: translateY(100%);
    }
</style>