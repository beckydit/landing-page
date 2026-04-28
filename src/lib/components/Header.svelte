<script>
    import { onMount } from 'svelte';
    import Link from "$lib/components/Link.svelte";

    let theme = $state('dark');

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
    <Link title=".indd" ref="/" leadingIcon="star" trailingIcon="star" />

    <nav>
        <label class="switch" aria-label="Cambia tema">
            <input 
                type="checkbox" 
                checked={theme === 'light'} 
                onchange={toggleTheme} 
            />
            <span class="slider"></span>
        </label>

        <Link title="@kyouuuka" ref="https://www.instagram.com/kyouuuka" />
    </nav>
</header>

<style>
    header {
        padding-block: var(--size-6);
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    nav {
        display: flex;
        /* Aumentato il gap per staccare il toggle dal link instagram */
        gap: var(--size-10); 
        align-items: center;
    }

    /* Struttura del Toggle */
    .switch {
        position: relative;
        display: inline-block;
        width: 38px;
        height: 20px;
        /* Un piccolo margine extra a destra per sicurezza */
        margin-right: var(--size-2); 
    }

    .switch input {
        opacity: 0;
        width: 0;
        height: 0;
    }

    .slider {
        position: absolute;
        cursor: pointer;
        top: 0; left: 0; right: 0; bottom: 0;
        background-color: transparent;
        border: 1px solid var(--color-ink-secondary);
        transition: 0.4s var(--ease-out-quart);
        border-radius: 20px;
    }

    .slider:before {
        position: absolute;
        content: "";
        height: 12px;
        width: 12px;
        left: 3px;
        bottom: 3px;
        background-color: var(--color-ink-secondary);
        transition: 0.4s var(--ease-out-quart);
        border-radius: 50%;
    }

    /* Quando il tema è Light */
    input:checked + .slider {
        background-color: var(--color-link);
        border-color: var(--color-link);
    }

    input:checked + .slider:before {
        transform: translateX(18px);
        background-color: white;
    }

    /* Hover effetto */
    .switch:hover .slider {
        border-color: var(--color-ink);
    }
</style>