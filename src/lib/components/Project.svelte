<script>
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
        }
    }

    .thumbnail {
        position: relative;
        aspect-ratio: 16/10;
        overflow: hidden;

    .veil {
        position: absolute;
        inset: 0;
        background-color: var(--hex-brand-600); 
        
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 1;
        
        transition: opacity 0.2s ease-in-out; 
        opacity: 0;
    }

        .hover-text {
        color: var(--hex-neutral-50);
        font-size: var(--size-4);
        font-weight: 500;
        text-transform: none;
        padding-inline: var(--size-4);
        line-height: 1.4;
        max-width: 20ch;
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
</style>