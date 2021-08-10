<script>
    export let type = 'button';
    export let disabled = false;
    export let id;
</script>

<button {type} {id} on:click>
    <slot />
</button>

