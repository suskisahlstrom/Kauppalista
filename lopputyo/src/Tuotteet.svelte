<script>
    import Tiedot from './Tiedot.svelte';
    export let elaimet;
    export let elain;
  </script>
  
  {#each elaimet as elukka}
    <Tiedot {...elukka} {...elain} on:poista />
  {/each}
  