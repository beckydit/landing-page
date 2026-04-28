<script>
    import { onMount } from 'svelte';
    import Link from "$lib/components/Link.svelte";

    let theme = $state('dark');

    // Funzione per applicare il tema in modo sicuro
    const applyTheme = (newTheme) => {
        theme = newTheme;
        if (typeof document !== 'undefined') {
            document.documentElement.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', newTheme);
        }
    };

    onMount(() => {
        const savedTheme = localStorage.getItem('theme') || 'dark';
        applyTheme(savedTheme);
    });

    function toggleTheme() {
        const nextTheme = theme === 'dark' ? 'light' : 'dark';
        applyTheme(nextTheme);
    }
</script>

<header class="safe-area">
    <Link 
        title=".indd" 
        ref="/" 
        leadingIcon="star" 
        trailingIcon="star" 
    />

    <nav>
        <button type="button" onclick={toggleTheme} class="theme-toggle">
            {theme === 'dark' ? 'LIGHT' : 'DARK'}
        </button>

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

    .theme-toggle {
        /* Reset stili bottone */
        background: transparent;
        border: none;
        padding: 0;
        cursor: pointer;
        
        /* Typography */
        font-family: var(--font-primary);
        font-size: var(--size-3);
        font-weight: 500;
        text-transform: uppercase;
        
        /* Colore dinamico che usa i tuoi token */
        color: var(--color-ink-secondary);
        transition: color 0.3s var(--ease-out-quart);
    }

    .theme-toggle:hover {
        color: var(--color-ink);
    }
</style>