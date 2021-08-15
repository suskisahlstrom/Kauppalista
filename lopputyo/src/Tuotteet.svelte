<script>
    import Tiedot from './Tiedot.svelte'; //Koodin pätkä otettu lemmikkiprojektista, en muista tarkkaa toimintaa mutta sivusto ei toimi ilman tätä.
    export let lisatytTuotteet;
    export let tuotte;
  </script>
  
  {#each lisatytTuotteet as tuot}
    <Tiedot {...tuot} {...tuotte} on:poista /> 
  {/each}
  