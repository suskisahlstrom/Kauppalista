<script>
    export let type = 'button';
    export let id;
    export let disabled = false;
</script>

<button {type} {id} on:click>
    <slot />
</button>

