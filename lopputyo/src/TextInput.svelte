<script>
    export let value;
    export let id;
    export let label = '';
    export let type = 'text';
    export let rows = 5;
    export let cols = 40;
    export let error = '';
    export let valid;
    let visited = false;
</script>

{#if type === 'textarea'}
  <textarea bind:value {rows} {cols} on:blur={() => (visited = true)} />
  {#if !valid && error && visited}
    <p class="error">{error}</p>
  {/if}
{:else}
  <label for={id}>{label}</label>
  <input {type} {value} {id} on:input on:blur={() => (visited = true)} />
  {#if !valid && error && visited}
    <p class="error">{error}</p>
  {/if}
{/if}

<style>
  input,
  textarea {
    width: 100%;
  }

  .error {
    margin-top: 0;
    font-size: 0.75em;
    color: red;
  }
</style>