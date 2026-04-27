<script>
    let { group = $bindable(), value } = $props();
</script>

<label>
    <input type="radio" {value} bind:group />
    <span class="year-text">{value}</span>
</label>

<style>
    label {
        padding-block: var(--size-2);
        padding-inline: var(--size-4);
        border-radius: 999px;
        cursor: pointer;
        transition: 
            background-color 0.25s var(--ease-out-quart),
            color 0.25s var(--ease-out-quart);
        
        /* Colore di base per gli anni non selezionati */
        color: var(--color-ink-secondary);

        &:hover {
            background-color: var(--color-filter--hover);
            color: var(--color-ink); /* Leggermente più chiaro all'hover */
        }

        /* Quando l'input radio è selezionato */
        &:has(input:checked) {
            background-color: var(--color-filter--selected);
            color: var(--hex-neutral-50); /* L'anno diventa bianco */
        }
    }

    .year-text {
        font-weight: 600;
        font-size: var(--size-4);
    }

    input {
        display: none; /* Nascondiamo il pallino del radio button */
    }
</style>