<script>
    import button from './button.svelte';
</script>

<div class="backdrop" on:click />

<div class="modal">
    <header>
        <slot name="header" />
    </header>
    <slot />
    <footer>
        <slot name="footer">
            <Button on:click>Sulje</Button>
        </slot>
    </footer>
</div>